---
title: PowerShell 시작
description: 신규 사용자에게 PowerShell을 찾고 실행하는 방법을 알려줍니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8b9fee222347970df4e35f9ba0841232952a292d
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99599326"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="07240-103">1장 - PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="07240-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="07240-104">필자는 회의와 사용자 그룹 모임에서 발표자가 초보자용 프레젠테이션을 시작할 때 PowerShell을 실행하는 모습을 자주 목격합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="07240-105">이 책은 PowerShell을 사용해 본 적 없는 참석자들이 세션에서 한 질문에 대답하는 것으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="07240-106">특히 이 장에서는 PowerShell을 찾아 실행하고, PowerShell을 처음 사용하는 사용자가 초반에 겪는 문제를 해결하는 방법을 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="07240-107">Windows 10 랩 환경 컴퓨터에서 이 장에 나오는 예제를 따라 하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="07240-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="07240-108">PowerShell을 시작하려면 무엇이 필요하나요?</span><span class="sxs-lookup"><span data-stu-id="07240-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="07240-109">모든 Windows 운영 체제 최신 버전에는 PowerShell이 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="07240-110">5\.1 미만 버전을 실행한다면 최신 버전을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="07240-111">PowerShell 5.1로 업그레이드하는 방법은 [기존 Windows PowerShell 업그레이드][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="07240-112">PowerShell 최신 버전을 설치하는 자세한 방법은 [PowerShell 설치][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="07240-113">PowerShell은 어디서 찾을 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="07240-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="07240-114">Windows 10에서 PowerShell을 찾는 가장 쉬운 방법은 그림 1-1처럼 검색 창에 **PowerShell** 를 입력하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="07240-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![그림 1-1 - 시작 메뉴에서 PowerShell 검색](media/figure1-1.png)

<span data-ttu-id="07240-116">그림 1-1에는 PowerShell을 여는 네 가지 바로 가기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="07240-117">이 책에서 시연 목적으로 사용하는 컴퓨터는 Windows 10 64비트 버전을 실행하고 있습니다. 따라서 64비트 버전의 PowerShell 콘솔과 PowerShell ISE(통합 스크립팅 환경)가 있으며, 각 항목의 32비트 버전은 바로 가기에 (x86) 접미사가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="07240-118">Windows 10 32비트 버전을 실행해야 한다면 두 가지 바로 가기만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="07240-119">두 바로 가기는 (x86) 접미사가 없지만 32비트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="07240-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="07240-120">64비트 운영 체제를 이용한다면, 32비트 버전을 실행해야 하는 특별한 이유가 없는 한 PowerShell 64비트 버전을 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="07240-121">다른 Windows 버전에서 PowerShell을 시작하는 자세한 방법은 [Windows PowerShell 시작][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="07240-122">PowerShell을 실행하려면 어떻게 할까요?</span><span class="sxs-lookup"><span data-stu-id="07240-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="07240-123">필자가 지원하는 프로덕션 엔터프라이즈 환경에서 필자는 세 가지 Active Directory 사용자 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="07240-124">이 책에서 사용하는 랩 환경에는 이 계정 미러링되었습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="07240-125">필자는 Windows 10 컴퓨터에 도메인 또는 로컬 관리자가 아닌 도메인 사용자로 로그인했습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="07240-126">그리고 그림 1-1처럼 "Windows PowerShell" 바로 가기를 클릭하여 PowerShell 콘솔을 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![그림 1-4 - PowerShell 창의 제목 표시줄](media/figure1-4.png)

<span data-ttu-id="07240-128">그림 1-4처럼 PowerShell 콘솔의 제목 표시줄에 "Windows PowerShell"이 표시된다는 점에 주목하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="07240-129">일부 명령은 정상적으로 실행되지만 PowerShell은 UAC(사용자 계정 컨트롤)에는 참여할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="07240-130">관리자의 승인이 필요한 작업에 대해 권한 승격을 요청할 수 없다는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="07240-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="07240-131">다음 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-131">The following error message is generated:</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

<span data-ttu-id="07240-132">이 문제를 해결 방법은 PowerShell을 로컬 관리자인 도메인 사용자로 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="07240-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="07240-133">필자는 두 번째 도메인 사용자 계정을 이 방법으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="07240-134">최소 권한 원칙에 따라 이 계정은 도메인 관리자가 아니거나 도메인에서 승격된 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="07240-135">PowerShell을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-135">Close PowerShell.</span></span> <span data-ttu-id="07240-136">PowerShell 콘솔을 다시 실행합니다. 이번에는 **Windows PowerShell** 바로 가기를 마우스 오른쪽 단추로 클릭하고 그림 1-5처럼 **관리자 권한으로 실행** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![그림 1-5 - 상황에 맞는 메뉴 - 관리자 권한으로 실행](media/figure1-5.png)

<span data-ttu-id="07240-138">일반 사용자로 Windows에 로그인했다면 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="07240-139">그림 1-6처럼 도메인 사용자이자 로컬 관리자인 필자 사용자 계정의 자격 증명을 입력하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![그림 1-6](media/figure1-6.png)

<span data-ttu-id="07240-141">PowerShell을 관리자 권한으로 다시 실행하면 그림 1-7처럼 제목 표시줄에 "Administrator: Windows PowerShell"이라고 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![그림 1-7](media/figure1-7.png)

<span data-ttu-id="07240-143">이제 PowerShell이 로컬 관리자 권한으로 승격되어 실행되며, 일반적으로 승격 메시지를 표시하는 로컬 컴퓨터에서 명령을 실행할 때는 UAC가 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="07240-144">하지만 이 승격된 PowerShell 콘솔에서 실행하는 모든 명령이 승격된 상태로 실행된다는 점을 명심하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="07240-145">관리자 권한으로 PowerShell을 쉽게 찾고 실행할 수 있도록, 작업 표시줄에 고정하고 실행될 때마다 관리자 권한으로 자동으로 시작되도록 설정하는 방법을 추천합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="07240-146">PowerShell을 다시 검색하되, 이번에는 마우스 오른쪽 단추로 클릭한 다음 그림 1-8처럼 "작업 표시줄에 고정"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![그림 1-8](media/figure1-8.png)

<span data-ttu-id="07240-148">작업 표시줄에 고정된 PowerShell 바로 가기를 마우스 오른쪽 단추로 클릭하고 그림 1-9처럼 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![그림 1-9 - 사용자 계정 컨트롤 - 자격 증명 입력](media/figure1-9.png)

<span data-ttu-id="07240-150">그림 1-10에 #1로 표시된 “고급”을 클릭하고 그림 1-10에 #2로 표시된 “관리자 권한으로 실행” 확인란을 선택한 다음, 확인을 두 번 클릭하여 변경사항을 수락하고 대화 상자 2개를 모두 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![그림 1-10 - “관리자”를 표시하는 제목 표시줄](media/figure1-10.png)

<span data-ttu-id="07240-152">PowerShell을 찾거나 관리자 권한으로 다시 실행하는 일은 걱정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="07240-153">관리자 권한으로 PowerShell을 실행하여 UAC 관련 문제를 방지하는 작업은 로컬 컴퓨터를 대상으로 실행하는 명령에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07240-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="07240-154">원격 컴퓨터를 대상으로 하는 명령에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="07240-155">제가 실행하는 PowerShell 버전은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="07240-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="07240-156">PowerShell에는 상태 정보를 저장하는 여러 자동 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="07240-157">이러한 변수 중 하나인 `$PSVersionTable`에는 관련 PowerShell 버전 정보를 표시하는 해시 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="07240-158">최신 버전의 Windows PowerShell은 WMF(Windows Management Framework)의 구성요소로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="07240-159">WMF 버전에 따라 특정 버전의 .NET Framework가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="07240-160">PowerShell 5.1로 업그레이드하는 방법은 [기존 Windows PowerShell 업그레이드][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="07240-161">실행 정책</span><span class="sxs-lookup"><span data-stu-id="07240-161">Execution Policy</span></span>

<span data-ttu-id="07240-162">통념과는 달리 PowerShell의 실행 정책은 보안 경계가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="07240-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="07240-163">사용자가 자신도 모르게 스크립트를 실행하는 일이 없도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="07240-164">사용자는 마음만 먹으면 PowerShell에서 실행 정책을 쉽게 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="07240-165">표 1-2는 현재 Windows 운영 체제에 대한 기본 실행 정책을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="07240-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="07240-166">서버 운영 체제 버전</span><span class="sxs-lookup"><span data-stu-id="07240-166">Windows Operating System Version</span></span> | <span data-ttu-id="07240-167">기본 실행 정책</span><span class="sxs-lookup"><span data-stu-id="07240-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="07240-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="07240-168">Server 2019</span></span>                      | <span data-ttu-id="07240-169">원격 서명됨</span><span class="sxs-lookup"><span data-stu-id="07240-169">Remote Signed</span></span>            |
| <span data-ttu-id="07240-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="07240-170">Server 2016</span></span>                      | <span data-ttu-id="07240-171">원격 서명됨</span><span class="sxs-lookup"><span data-stu-id="07240-171">Remote Signed</span></span>            |
| <span data-ttu-id="07240-172">윈도우 10</span><span class="sxs-lookup"><span data-stu-id="07240-172">Windows 10</span></span>                       | <span data-ttu-id="07240-173">제한</span><span class="sxs-lookup"><span data-stu-id="07240-173">Restricted</span></span>               |

<span data-ttu-id="07240-174">실행 정책 설정에 관계없이 모든 PowerShell 명령은 대화형으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="07240-175">실행 정책은 스크립트에서 실행하는 명령에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07240-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="07240-176">`Get-ExecutionPolicy` cmdlet은 현재 실행 정책 설정을 확인하는 데 사용하고 `Set-ExecutionPolicy` cmdlet은 실행 정책을 변경하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="07240-177">**RemoteSigned** 정책 사용을 추천합니다. 이 정책을 실행하려면 다운로드한 스크립트에 신뢰할 수 있는 게시자가 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="07240-178">현재 실행 정책을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="07240-179">실행 정책을 **제한됨** 으로 설정하면 PowerShell 스크립트를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="07240-180">이것은 모든 Windows 클라이언트 운영 체제의 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="07240-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="07240-181">문제를 확인하고 싶다면 다음 코드를 `Stop-TimeService.ps1`이라는 `.ps1` 파일로 저장하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="07240-182">이 명령은 PowerShell을 관리자 권한으로 실행하는 한 오류 없이 대화형으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="07240-183">하지만 스크립트 파일로 저장한 후 스크립트를 실행하면 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="07240-184">이전 결과 모음에 표시된 오류를 확인하면 정확한 문제를 파악할 수 있습니다(이 시스템에서 스크립트 실행이 비활성화됨).</span><span class="sxs-lookup"><span data-stu-id="07240-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="07240-185">PowerShell에서 오류 메시지를 생성하는 명령을 실행할 때는 명령을 다시 실행하고 성공하길 바라는 대신 오류 메시지를 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="07240-186">PowerShell 실행 정책을 원격 서명으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="07240-186">Change the PowerShell execution policy to remote signed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

<span data-ttu-id="07240-187">실행 정책을 변경할 때 표시되는 경고를 반드시 읽어 보세요.</span><span class="sxs-lookup"><span data-stu-id="07240-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="07240-188">[about_Execution_Policies][] 도움말 항목을 확인해 정책 보안 변경이 보안에 미치는 영향을 알아보는 것도 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="07240-189">이제 실행 정책이 **RemoteSigned** 로 설정되었으므로 `Stop-TimeService.ps1` 스크립트가 오류 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="07240-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="07240-190">계속하기 전에 Windows 시간 서비스를 시작해야 합니다. 그렇지 않으면 예기치 않은 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="07240-191">요약</span><span class="sxs-lookup"><span data-stu-id="07240-191">Summary</span></span>

<span data-ttu-id="07240-192">이 장에서는 PowerShell을 찾고 시작하는 방법과 관리자 권한으로 PowerShell을 시작하는 바로 가기를 만드는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="07240-193">기본 실행 정책과 이를 변경하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="07240-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="07240-194">검토</span><span class="sxs-lookup"><span data-stu-id="07240-194">Review</span></span>

1. <span data-ttu-id="07240-195">컴퓨터에서 실행 중인 PowerShell 버전을 확인하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="07240-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="07240-196">관리자 권한으로 PowerShell을 실행해야 하는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="07240-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="07240-197">현재 PowerShell 실행 정책을 확인하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="07240-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="07240-198">기본 PowerShell 실행 정책이 Windows 클라이언트 컴퓨터에서 방지하는 일은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="07240-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="07240-199">PowerShell 실행 정책을 변경하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="07240-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="07240-200">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="07240-200">Recommended Reading</span></span>

<span data-ttu-id="07240-201">이 장에서 다루는 항목에 대한 자세한 정보를 확인하려면 다음 PowerShell 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07240-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="07240-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="07240-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="07240-203">[about_Hash_Tables][]</span><span class="sxs-lookup"><span data-stu-id="07240-203">[about_Hash_Tables][]</span></span>
- <span data-ttu-id="07240-204">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="07240-204">[about_Execution_Policies][]</span></span>

<span data-ttu-id="07240-205">다음 장에서는 PowerShell 명령의 검색 기능을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="07240-205">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="07240-206">대표적인 주제는 PowerShell을 업데이트하여 이러한 도움말 항목을 인터넷이 아닌 PowerShell에서 바로 확인하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="07240-206">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[기존 Windows PowerShell 업그레이드]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[PowerShell 설치]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[Windows PowerShell 시작]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
