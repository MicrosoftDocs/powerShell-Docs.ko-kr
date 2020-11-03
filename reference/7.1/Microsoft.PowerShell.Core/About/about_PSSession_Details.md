---
description: PowerShell 세션과 원격 명령에서 수행 하는 역할에 대 한 자세한 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 3d6ac25d7f8cac3d0b38cf921382e9a7aaeaf3d6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93224002"
---
# <a name="about-pssession-details"></a><span data-ttu-id="15f3f-104">PSSession 정보 정보</span><span class="sxs-lookup"><span data-stu-id="15f3f-104">About PSSession Details</span></span>

## <a name="short-description"></a><span data-ttu-id="15f3f-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="15f3f-105">Short Description</span></span>
<span data-ttu-id="15f3f-106">PowerShell 세션과 원격 명령에서 수행 하는 역할에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-106">Provides detailed information about PowerShell sessions and the role they play in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="15f3f-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="15f3f-107">Long Description</span></span>

<span data-ttu-id="15f3f-108">세션은 PowerShell을 실행 하는 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-108">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="15f3f-109">PowerShell을 시작할 때마다 세션이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-109">A session is created for you whenever you start PowerShell.</span></span> <span data-ttu-id="15f3f-110">컴퓨터 또는 다른 컴퓨터에서 "PowerShell 세션" 또는 "PSSessions" 라는 추가 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-110">You can create additional sessions, called "PowerShell sessions" or "PSSessions" on your computer or another computer.</span></span>

<span data-ttu-id="15f3f-111">PowerShell에서 만드는 세션과 달리 사용자가 만든 pssession을 제어 하 고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-111">Unlike the sessions that PowerShell creates for you, you control and manage the PSSessions that you create.</span></span>

<span data-ttu-id="15f3f-112">PSSessions는 원격 컴퓨팅에서 중요 한 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-112">PSSessions play an important role in remote computing.</span></span> <span data-ttu-id="15f3f-113">원격 컴퓨터에 연결 된 PSSession을 만들 때 PowerShell은 PSSession을 지원 하기 위해 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-113">When you create a PSSession that is connected to a remote computer, PowerShell establishes a persistent connection to the remote computer to support the PSSession.</span></span> <span data-ttu-id="15f3f-114">PSSession을 사용 하 여 데이터를 공유 하는 일련의 명령, 함수 및 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-114">You can use the PSSession to run a series of commands, functions, and scripts that share data.</span></span>

<span data-ttu-id="15f3f-115">이 항목에서는 PowerShell의 세션 및 pssession에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-115">This topic provides detailed information about sessions and PSSessions in PowerShell.</span></span> <span data-ttu-id="15f3f-116">세션에서 수행할 수 있는 작업에 대 한 기본 정보는 [about_PSSessions](about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-116">For basic information about the tasks that you can perform with sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="about-sessions"></a><span data-ttu-id="15f3f-117">세션 정보</span><span class="sxs-lookup"><span data-stu-id="15f3f-117">About Sessions</span></span>

<span data-ttu-id="15f3f-118">기술적으로 세션은 PowerShell을 실행 하는 실행 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-118">Technically, a session is an execution environment in which PowerShell runs.</span></span> <span data-ttu-id="15f3f-119">각 세션에는 PowerShell을 실행 하는 호스트 프로그램 및 System.object의 인스턴스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-119">Each session includes an instance of the System.Management.Automation engine and a host program in which PowerShell runs.</span></span> <span data-ttu-id="15f3f-120">호스트는 Windows PowerShell ISE (통합 스크립팅 환경)와 같이 PowerShell을 호스트 하도록 빌드된 프로그램 또는 Cmd.exe 같은 명령을 실행 하는 친숙 한 PowerShell 콘솔 또는 다른 프로그램 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-120">The host can be the familiar PowerShell console or another program that runs commands, such as Cmd.exe, or a program built to host PowerShell, such as Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="15f3f-121">Windows 관점에서 세션은 대상 컴퓨터의 Windows 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-121">From a Windows perspective, a session is a Windows process on the target computer.</span></span>

<span data-ttu-id="15f3f-122">각 세션은 독립적으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-122">Each session is configured independently.</span></span> <span data-ttu-id="15f3f-123">자체 속성, 자체 실행 정책 및 자체 프로필을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-123">It includes its own properties, its own execution policy, and its own profiles.</span></span> <span data-ttu-id="15f3f-124">세션을 만들 때 존재 하는 환경은 컴퓨터에서 환경을 변경 하는 경우에도 수명 동안 지속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-124">The environment that exists when the session is created persists for its lifetime even if you change the environment on the computer.</span></span> <span data-ttu-id="15f3f-125">모든 세션은 스크립트에서 만든 세션을 비롯 하 여 전역 범위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-125">All sessions are created in a global scope, even sessions that you create in a script.</span></span>

<span data-ttu-id="15f3f-126">한 번에 하나의 명령 (또는 명령 파이프라인)만 세션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-126">You can run only one command (or command pipeline) in a session at one time.</span></span> <span data-ttu-id="15f3f-127">두 번째 명령은 동기적으로 (한 번에 하나씩) 실행 되며, 첫 번째 명령이 완료 될 때까지 최대 4 분이 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-127">A second command run synchronously (one at a time) waits up to four minutes for the first command to be completed.</span></span> <span data-ttu-id="15f3f-128">두 번째 명령은 비동기적으로 (동시에) 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-128">A second command run asynchronously (concurrently) fails.</span></span>

## <a name="about-pssessions"></a><span data-ttu-id="15f3f-129">PSSessions 정보</span><span class="sxs-lookup"><span data-stu-id="15f3f-129">About PSSessions</span></span>

<span data-ttu-id="15f3f-130">PowerShell을 시작할 때마다 세션이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-130">A session is created each time that you start PowerShell.</span></span> <span data-ttu-id="15f3f-131">PowerShell은 개별 명령을 실행할 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-131">And, PowerShell creates temporary sessions to run individual commands.</span></span>
<span data-ttu-id="15f3f-132">그러나 사용자가 제어 하 고 관리 하는 세션 ("PowerShell 세션" 또는 "PSSessions")을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-132">However, you can also create sessions (called "PowerShell sessions" or "PSSessions") that you control and manage.</span></span>

<span data-ttu-id="15f3f-133">PSSessions는 원격 명령에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-133">PSSessions are critical to remote commands.</span></span> <span data-ttu-id="15f3f-134">또는 cmdlet의 **ComputerName** 매개 변수를 사용 하는 경우 `Invoke-Command` `Enter-PSSession` PowerShell에서 명령을 실행 하는 임시 세션을 설정 하 고 명령이 나 대화형 세션이 완료 되는 즉시 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-134">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlets, PowerShell establishes a temporary session to run the command and then closes the session as soon as the command or the interactive session is complete.</span></span>

<span data-ttu-id="15f3f-135">그러나 cmdlet을 사용 하 여 `New-PSSession` PSSession을 만드는 경우 PowerShell은 여러 명령 또는 대화형 세션을 실행할 수 있는 원격 컴퓨터에 영구 세션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-135">However, if you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent session on the remote computer in which you can run multiple commands or interactive sessions.</span></span> <span data-ttu-id="15f3f-136">사용자가 만든 pssession은 열어 둔 후 삭제할 때까지 또는 해당 세션이 만들어진 세션을 닫을 때까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-136">The PSSessions that you create remain open and available for use until you delete them or until you close the session in which they were created.</span></span>

<span data-ttu-id="15f3f-137">원격 컴퓨터에서 PSSession을 만들 때 시스템은 원격 컴퓨터에서 PowerShell 프로세스를 만들고 로컬 컴퓨터에서 원격 컴퓨터의 프로세스에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-137">When you create a PSSession on a remote computer, the system creates a PowerShell process on the remote computer and establishes a connection from the local computer to the process on the remote computer.</span></span> <span data-ttu-id="15f3f-138">로컬 컴퓨터에서 PSSession을 만들 때 새 프로세스와 연결이 모두 로컬 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-138">When you create a PSSession on the local computer, both the new process and the connections are created on the local computer.</span></span>

## <a name="when-do-i-need-a-pssession"></a><span data-ttu-id="15f3f-139">PSSession은 언제 필요 한가요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-139">When Do I Need a PSSession?</span></span>

<span data-ttu-id="15f3f-140">`Invoke-Command`및 cmdlet에는 `Enter-PSSession` **ComputerName** 및 **Session** 매개 변수가 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-140">The `Invoke-Command` and `Enter-PSSession` cmdlets have both **ComputerName** and **Session** parameters.</span></span> <span data-ttu-id="15f3f-141">둘 중 하나를 사용 하 여 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-141">You can use either to run a remote command.</span></span>

<span data-ttu-id="15f3f-142">**ComputerName** 매개 변수를 사용 하 여 하나 이상의 컴퓨터에서 단일 명령이 나 일련의 관련 되지 않은 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-142">Use the **ComputerName** parameter to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="15f3f-143">데이터를 공유 하는 명령을 실행 하려면 원격 컴퓨터에 대 한 영구 연결이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-143">To run commands that share data, you need a persistent connection to the remote computer.</span></span> <span data-ttu-id="15f3f-144">이 경우 PSSession을 만든 다음 **Session** 매개 변수를 사용 하 여 pssession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-144">In that case, create a PSSession, and then use the **Session** parameter to run commands in the PSSession.</span></span>

<span data-ttu-id="15f3f-145">,, 및와 같은 원격 컴퓨터에서 데이터를 가져오는 다른 많은 cmdlet에 `Get-Process` `Get-Service` `Get-EventLog` `Get-WmiObject` 는 **ComputerName** 매개 변수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-145">Many other cmdlets that get data from remote computers, such as `Get-Process`, `Get-Service`, `Get-EventLog`, and `Get-WmiObject` have only a **ComputerName** parameter.</span></span> <span data-ttu-id="15f3f-146">PowerShell remoting 이외의 기술을 사용 하 여 데이터를 원격으로 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-146">They use technologies other than PowerShell remoting to gather data remotely.</span></span> <span data-ttu-id="15f3f-147">이러한 cmdlet에는 **Session** 매개 변수가 없지만 cmdlet을 사용 `Invoke-Command` 하 여 PSSession에서 이러한 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-147">These cmdlets do not have a **Session** parameter, but you can use the `Invoke-Command` cmdlet to run these commands in a PSSession.</span></span>

## <a name="how-do-i-create-a-pssession"></a><span data-ttu-id="15f3f-148">PSSession을 만들려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-148">How Do I Create a PSSession?</span></span>

<span data-ttu-id="15f3f-149">PSSession을 만들려면 cmdlet을 사용 `New-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-149">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="15f3f-150">`New-PSSession`를 사용 하 여 로컬 또는 원격 컴퓨터에서 PSSession을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-150">You can use `New-PSSession` to create a PSSession on a local or remote computer.</span></span>

## <a name="can-i-create-a-pssession-on-any-computer"></a><span data-ttu-id="15f3f-151">모든 컴퓨터에서 PSSession을 만들 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-151">Can I Create a PSSession on Any Computer?</span></span>

<span data-ttu-id="15f3f-152">원격 컴퓨터에 연결 된 PSSession을 만들려면 PowerShell에서 원격 기능을 사용할 수 있도록 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-152">To create a PSSession that is connected to a remote computer, the computer must be configured for remoting in PowerShell.</span></span> <span data-ttu-id="15f3f-153">현재 사용자는 원격 컴퓨터에서 Administrators 그룹의 구성원 이거나, 현재 사용자가 Administrators 그룹의 구성원 자격 증명을 제공할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-153">The current user must be a member of the Administrators group on the remote computer, or the current user must be able to supply the credentials of a member of the Administrators group.</span></span> <span data-ttu-id="15f3f-154">자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-154">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="can-i-see-my-pssessions-in-other-sessions"></a><span data-ttu-id="15f3f-155">다른 세션에서 내 pssession을 볼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-155">Can I See My PSSessions in Other Sessions?</span></span>

<span data-ttu-id="15f3f-156">Windows PowerShell 3.0부터 cmdlet의 **ComputerName** 매개 변수는 `Get-PSSession` 지정 된 원격 컴퓨터에서 만든 pssessions를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-156">Beginning in Windows PowerShell 3.0, the **ComputerName** parameter of the `Get-PSSession` cmdlet gets PSSessions that you created on the specified remote computers.</span></span>

<span data-ttu-id="15f3f-157">활성 pssession은 원격 컴퓨터 (연결의 "서버 쪽")에서 유지 관리 되며 모든 컴퓨터의 모든 세션에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-157">Active PSSessions are maintained on the remote computer (the "server-side" of a connection) and you can get them from any session on any computer.</span></span>

<span data-ttu-id="15f3f-158">예를 들어 Server01 컴퓨터에서 Server02 컴퓨터로 PSSession을 만든 다음 Server03 컴퓨터로 전환 하는 경우 다음과 같은 명령을 사용 하 여 세션을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-158">For example, if you create a PSSession from the Server01 computer to the Server02 computer, and then switch to the Server03 computer, you can use a command like the following one to get the session.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

<span data-ttu-id="15f3f-159">세션에서 연결을 끊는 경우에도 세션은 사용자가 삭제 하거나 시간 초과 될 때까지 원격 컴퓨터에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-159">Even if you disconnect from the session, the session is maintained on the remote computer until you delete it or it times out.</span></span>

<span data-ttu-id="15f3f-160">Windows PowerShell 2.0에서는 현재 세션에서 만든 pssession만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-160">In Windows PowerShell 2.0, you can get only the PSSessions that you have created in the current session.</span></span> <span data-ttu-id="15f3f-161">다른 세션에서 만든 pssession은 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-161">You cannot get PSSessions that you created in other sessions.</span></span>

<span data-ttu-id="15f3f-162">자세한 내용은 [get-help](xref:Microsoft.PowerShell.Core.Get-PSSession)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-162">For more information, see [Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession).</span></span>

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a><span data-ttu-id="15f3f-163">다른 사용자가 내 컴퓨터에서 만든 pssession을 볼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-163">Can I See the PSSessions That Others Have Created on My Computer?</span></span>

<span data-ttu-id="15f3f-164">PSSession을 만든 사용자의 자격 증명을 제공 하거나 PSSession에서 사용 하는 세션 구성에 RunAs 자격 증명을 포함 하는 경우에만 다른 사용자가 만든 pssession을 가져오고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-164">You can get and manage only the PSSessions that others have created only if you can supply the credentials of the user who created the PSSession or the session configuration that the PSSession uses includes RunAs credentials.</span></span> <span data-ttu-id="15f3f-165">그렇지 않으면 만든 pssession만 가져오고, 연결 하 고, 사용 하 고, 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-165">Otherwise, you can get, connect to, use, and manage only the PSSessions that you created.</span></span>

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a><span data-ttu-id="15f3f-166">다른 컴퓨터에서 PSSession에 연결할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-166">Can I Connect to a PSSession From a Different Computer?</span></span>

<span data-ttu-id="15f3f-167">Windows PowerShell 3.0부터 pssession은 생성 된 세션과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-167">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they were created.</span></span> <span data-ttu-id="15f3f-168">활성 pssession은 원격 또는 "서버 쪽" 연결의 컴퓨터에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-168">Active PSSessions are maintained on the computer at the remote or "server-side" of a connection.</span></span>

<span data-ttu-id="15f3f-169">Cmdlet을 사용 `Disconnect-PSSession` 하 여 PSSession에서 연결을 끊을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-169">You can use the `Disconnect-PSSession` cmdlet to disconnect from a PSSession.</span></span> <span data-ttu-id="15f3f-170">PSSession은 로컬 세션에서 연결이 끊어져 원격 컴퓨터에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-170">The PSSession is disconnected from the local session, but is maintained on the remote computer.</span></span>
<span data-ttu-id="15f3f-171">명령은 연결 되지 않은 PSSession에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-171">Commands continue to run in the disconnected PSSession.</span></span> <span data-ttu-id="15f3f-172">PSSession을 중단 하지 않고 PowerShell을 닫고 원래 컴퓨터를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-172">You can close PowerShell and shut down the originating computer without interrupting the PSSession.</span></span>

<span data-ttu-id="15f3f-173">그런 다음 나중에 cmdlet을 사용 하 여 PSSession을 가져오고 cmdlet을 사용 하 여 `Get-PSSession` `Connect-PSSession` 다른 컴퓨터의 새 세션에서 pssession에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-173">Then, even hours later, you can use the `Get-PSSession` cmdlet to get the PSSession and the `Connect-PSSession` cmdlet to connect to the PSSession from a new session on a different computer.</span></span>

<span data-ttu-id="15f3f-174">자세한 내용은 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-174">For more information, see [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).</span></span>

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a><span data-ttu-id="15f3f-175">내 컴퓨터 중지 되 면 PSSession이 어떻게 되나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-175">What Happens to My PSSession if My Computer Stops?</span></span>

<span data-ttu-id="15f3f-176">연결 되지 않은 pssession은 자신이 만들어진 세션과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-176">Disconnected PSSessions are independent of the sessions in which they were created.</span></span> <span data-ttu-id="15f3f-177">PSSession의 연결을 끊은 다음 원래 컴퓨터를 닫으면 PSSession이 원격 컴퓨터에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-177">If you disconnect a PSSession and then close the originating computer, the PSSession is maintained on the remote computer.</span></span>

<span data-ttu-id="15f3f-178">또한 PowerShell은 컴퓨터를 다시 부팅 하는 경우와 같이 실수로 연결 되지 않은 활성 pssession을 복구 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-178">In addition, PowerShell attempts to recover active PSSessions that are disconnected unintentionally, such as by a computer reboot, a temporary power outage or network disruption.</span></span> <span data-ttu-id="15f3f-179">PowerShell은 열린 상태 (원래 세션을 계속 사용할 수 있는 경우) 또는 연결이 끊어진 상태 (없는 경우)로 PSSession을 유지 관리 또는 복구 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-179">PowerShell attempts to maintain or recover the PSSession to an Opened state, if the originating session is still available, or to a disconnected state if it is not.</span></span>

<span data-ttu-id="15f3f-180">"활성" PSSession은 명령을 실행 하는 PSSession입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-180">An "active" PSSession is one that is running commands.</span></span> <span data-ttu-id="15f3f-181">PSSession이 연결 되어 있고 (연결이 끊어져 있지 않음), 연결 된 세션이 닫힐 때 PSSession에서 명령이 실행 되는 경우 PowerShell은 원격 컴퓨터에서 PSSession을 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-181">If a PSSession is connected (not disconnected) and commands are running in the PSSession when the connected session closes, PowerShell attempts to maintain the PSSession on the remote computer.</span></span> <span data-ttu-id="15f3f-182">그러나 PSSession에서 실행 중인 명령이 없으면 PowerShell은 연결 된 세션이 닫힐 때 PSSession을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-182">However, if no commands are running in the PSSession, PowerShell closes the PSSession when the connected session closes.</span></span>

<span data-ttu-id="15f3f-183">자세한 내용은 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-183">For more information, see [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).</span></span>

## <a name="can-i-run-a-background-job-in-a-pssession"></a><span data-ttu-id="15f3f-184">PSSession에서 백그라운드 작업을 실행할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-184">Can I Run a Background Job in a PSSession?</span></span>

<span data-ttu-id="15f3f-185">예.</span><span class="sxs-lookup"><span data-stu-id="15f3f-185">Yes.</span></span> <span data-ttu-id="15f3f-186">백그라운드 작업은 현재 세션과 상호 작용 하지 않고 백그라운드에서 비동기적으로 실행 되는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-186">A background job is a command that runs asynchronously in the background without interacting with the current session.</span></span> <span data-ttu-id="15f3f-187">작업을 시작 하는 명령을 제출할 때이 명령은 작업 개체를 반환 하지만 완료 될 때까지 백그라운드에서 작업을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-187">When you submit a command to start a job, the command returns a job object, but the job continues to run in the background until it is complete.</span></span>

<span data-ttu-id="15f3f-188">로컬 컴퓨터에서 백그라운드 작업을 시작 하려면 `Start-Job` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-188">To start a background job on a local computer, use the `Start-Job` command.</span></span>
<span data-ttu-id="15f3f-189">**ComputerName** 매개 변수를 사용 하 여 임시 연결에서 또는 **세션** 매개 변수를 사용 하 여 PSSession에서 백그라운드 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-189">You can run the background job in a temporary connection (by using the **ComputerName** parameter) or in a PSSession (by using the **Session** parameter).</span></span>

<span data-ttu-id="15f3f-190">원격 컴퓨터에서 백그라운드 작업을 시작 하려면 `Invoke-Command` cmdlet을 **AsJob** 매개 변수와 함께 사용 하거나 cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-190">To start a background job on a remote computer, use the `Invoke-Command` cmdlet with its **AsJob** parameter, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="15f3f-191">**AsJob** 매개 변수를 사용 하는 경우 **ComputerName** 또는 **Session** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-191">When using the **AsJob** parameter, you can use the **ComputerName** or **Session** parameters.</span></span>

<span data-ttu-id="15f3f-192">를 사용 하 여 명령을 실행 하는 경우 `Invoke-Command` `Start-Job` PSSession에서 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-192">When using `Invoke-Command` to run a `Start-Job` command, you must run the command in a PSSession.</span></span> <span data-ttu-id="15f3f-193">**ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 작업 개체가 반환 될 때 연결을 종료 하 고 작업이 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-193">If you use the **ComputerName** parameter, PowerShell ends the connection when the job object returns, and the job is interrupted.</span></span>

<span data-ttu-id="15f3f-194">자세한 내용은 [about_Jobs](about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-194">For more information, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="can-i-run-an-interactive-session"></a><span data-ttu-id="15f3f-195">대화형 세션을 실행할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-195">Can I Run an Interactive Session?</span></span>

<span data-ttu-id="15f3f-196">예.</span><span class="sxs-lookup"><span data-stu-id="15f3f-196">Yes.</span></span> <span data-ttu-id="15f3f-197">원격 컴퓨터와의 대화형 세션을 시작 하려면 cmdlet을 사용 `Enter-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-197">To start an interactive session with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="15f3f-198">대화형 세션에서 입력 하는 명령은 원격 컴퓨터에서 직접 입력 하는 것 처럼 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-198">In an interactive session, the commands that you type run on the remote computer, just as if you typed them directly on the remote computer.</span></span>

<span data-ttu-id="15f3f-199">**ComputerName** 매개 변수를 사용 하 여 임시 세션에서 또는 **세션** 매개 변수를 사용 하 여 PSSession에서 대화형 세션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-199">You can run an interactive session in a temporary session (by using the **ComputerName** parameter) or in a PSSession (by using the **Session** parameter).</span></span>
<span data-ttu-id="15f3f-200">PSSession을 사용 하는 경우 PSSession은 이전 명령의 데이터를 유지 하 고, PSSession은 대화형 세션 중에 생성 된 모든 데이터를 이후 명령에서 사용할 수 있도록 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-200">If you use a PSSession, the PSSession retains the data from previous commands, and the PSSession retains any data generated during the interactive session for use in later commands.</span></span>

<span data-ttu-id="15f3f-201">대화형 세션을 종료 하면 PSSession이 열려 있고 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-201">When you end the interactive session, the PSSession remains open and available for use.</span></span>

<span data-ttu-id="15f3f-202">자세한 내용은 [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 및 [종료-pssession](xref:Microsoft.PowerShell.Core.Exit-PSSession)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-202">For more information, see [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) and [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession).</span></span>

## <a name="must-i-delete-the-pssessions"></a><span data-ttu-id="15f3f-203">PSSessions를 삭제 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-203">Must I Delete the PSSessions?</span></span>

<span data-ttu-id="15f3f-204">예.</span><span class="sxs-lookup"><span data-stu-id="15f3f-204">Yes.</span></span> <span data-ttu-id="15f3f-205">PSSession은 사용 하지 않는 경우에도 메모리 및 기타 리소스를 사용 하는 자체 포함 환경인 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-205">A PSSession is a process, which is a self-contained environment that uses memory and other resources even when you are not using it.</span></span> <span data-ttu-id="15f3f-206">PSSession이 완료 되 면 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-206">When you are finished with a PSSession, delete it.</span></span> <span data-ttu-id="15f3f-207">여러 pssession을 만드는 경우 사용 하지 않는 pssession을 닫고 현재 사용 중인 파일만 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-207">If you create multiple PSSessions, close the ones that you are not using, and maintain only the ones currently in use.</span></span>

<span data-ttu-id="15f3f-208">Pssession을 삭제 하려면 cmdlet을 사용 `Remove-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-208">To delete PSSessions, use the `Remove-PSSession` cmdlet.</span></span> <span data-ttu-id="15f3f-209">이 명령은 pssession을 삭제 하 고 사용 하 던 모든 리소스를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-209">It deletes the PSSessions and releases all of the resources that they were using.</span></span>

<span data-ttu-id="15f3f-210">의 **IdleTimeOut** 매개 변수를 사용 하 여 `New-PSSessionOption` 지정한 간격 후에 유휴 PSSession을 닫을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-210">You can also use the **IdleTimeOut** parameter of `New-PSSessionOption` to close an idle PSSession after an interval that you specify.</span></span> <span data-ttu-id="15f3f-211">자세한 내용은 [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-211">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="15f3f-212">PSSession 개체를 변수에 저장 하 고 PSSession을 삭제 하거나 시간 초과를 허용 하는 경우 변수에는 PSSession 개체가 계속 포함 되지만 PSSession은 활성화 되지 않으며 사용 하거나 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-212">If you save a PSSession object in a variable and then delete the PSSession or let it time out, the variable still contains the PSSession object, but the PSSession is not active and cannot be used or repaired.</span></span>

## <a name="are-all-sessions-and-pssessions-alike"></a><span data-ttu-id="15f3f-213">모든 세션과 pssession이 동일 한가요?</span><span class="sxs-lookup"><span data-stu-id="15f3f-213">Are All Sessions and PSSessions Alike?</span></span>

<span data-ttu-id="15f3f-214">아니요.</span><span class="sxs-lookup"><span data-stu-id="15f3f-214">No.</span></span> <span data-ttu-id="15f3f-215">개발자는 선택한 공급자 및 cmdlet만 포함 하는 사용자 지정 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-215">Developers can create custom sessions that include only selected providers and cmdlets.</span></span> <span data-ttu-id="15f3f-216">한 세션에서 명령이 작동 하지만 다른 세션에서는 작동 하지 않는 경우이는 세션이 제한 되기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f3f-216">If a command works in one session but not in another, it might be because the session is restricted.</span></span>

## <a name="see-also"></a><span data-ttu-id="15f3f-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15f3f-217">See Also</span></span>

[<span data-ttu-id="15f3f-218">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="15f3f-218">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="15f3f-219">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="15f3f-219">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="15f3f-220">about_Remote</span><span class="sxs-lookup"><span data-stu-id="15f3f-220">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="15f3f-221">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="15f3f-221">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="15f3f-222">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="15f3f-222">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="15f3f-223">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="15f3f-223">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="15f3f-224">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="15f3f-224">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="15f3f-225">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="15f3f-225">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="15f3f-226">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="15f3f-226">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="15f3f-227">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="15f3f-227">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="15f3f-228">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="15f3f-228">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)

