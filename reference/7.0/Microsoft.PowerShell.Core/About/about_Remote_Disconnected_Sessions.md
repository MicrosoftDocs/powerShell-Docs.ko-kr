---
description: PowerShell 세션 (PSSession)에 대 한 연결을 끊고 다시 연결 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: f4dbcd4d9255e4285687692902a41a3f3f40e093
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223801"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="f7268-104">연결 되지 않은 원격 세션 정보</span><span class="sxs-lookup"><span data-stu-id="f7268-104">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="f7268-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f7268-105">Short description</span></span>

<span data-ttu-id="f7268-106">PowerShell 세션 (PSSession)에 대 한 연결을 끊고 다시 연결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-106">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="f7268-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-107">Long description</span></span>

<span data-ttu-id="f7268-108">PowerShell 3.0부터 PSSession에서 연결을 끊고 동일한 컴퓨터 또는 다른 컴퓨터의 PSSession에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-108">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="f7268-109">세션의 연결이 끊어지면 세션 상태가 유지 되 고 PSSession의 명령이 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-109">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="f7268-110">연결이 끊어진 세션 기능은 원격 컴퓨터에서 PowerShell 3.0 이상 버전을 실행 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-110">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="f7268-111">연결 끊김 세션 기능을 사용 하면 pssession이 생성 된 세션을 닫고, PowerShell을 닫고, PSSession에서 실행 중인 명령을 방해 하지 않고 컴퓨터를 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-111">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="f7268-112">연결 되지 않은 세션은 완료 하는 데 오랜 시간이 걸리는 명령을 실행 하는 데 유용 하며 IT 전문가에 게 필요한 시간과 장치 유연성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-112">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="f7268-113">Cmdlet을 사용 하 여 시작 된 대화형 세션에서 연결을 끊을 수 없습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-113">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="f7268-114">연결 되지 않은 세션을 사용 하 여 컴퓨터 또는 네트워크 중단으로 인해 실수로 연결 해제 된 pssession을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-114">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="f7268-115">실제 사용에서 연결 끊김 기능을 사용 하면 문제 해결을 시작 하 고, 더 높은 우선 순위 문제를 확인 하 고, 다른 위치에 있는 다른 컴퓨터를 비롯 하 여 솔루션에서 작업을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-115">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="f7268-116">연결 되지 않은 세션 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f7268-116">Disconnected session cmdlets</span></span>

<span data-ttu-id="f7268-117">다음 cmdlet은 Disconnected 세션 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-117">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="f7268-118">`Connect-PSSession`: 연결 되지 않은 PSSession에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-118">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="f7268-119">`Disconnect-PSSession`: PSSession의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-119">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="f7268-120">`Get-PSSession`: 로컬 컴퓨터 또는 원격 컴퓨터에서 PSSessions를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-120">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="f7268-121">`Receive-PSSession`: 연결 되지 않은 세션에서 실행 된 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-121">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="f7268-122">`Invoke-Command`: **InDisconnectedSession** 매개 변수는 PSSession을 만들고 즉시 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-122">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="f7268-123">연결 되지 않은 세션 기능의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="f7268-123">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="f7268-124">PowerShell 3.0부터 pssession은 생성 된 세션과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-124">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="f7268-125">활성 PSSession은 PSSession을 만든 세션이 닫히고 원래 컴퓨터가 종료 되거나 네트워크에서 연결이 끊어진 경우에도 연결의 원격 컴퓨터 또는 **서버 쪽** 에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-125">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="f7268-126">PowerShell 2.0에서 PSSession은 원래 세션이 나 생성 된 세션이 종료 될 때 원격 컴퓨터에서 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-126">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="f7268-127">PSSession의 연결을 끊으면 PSSession이 활성 상태로 유지 되 고 원격 컴퓨터에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-127">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="f7268-128">세션 상태가 **실행 중** 에서 **Disconnected** 로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-128">The session state changes from **Running** to **Disconnected**.</span></span> <span data-ttu-id="f7268-129">현재 세션 또는 동일한 컴퓨터의 다른 세션이 나 다른 컴퓨터에서 연결이 끊어진 PSSession에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-129">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="f7268-130">세션을 유지 관리 하는 원격 컴퓨터가 실행 중 이어야 하 고 네트워크에 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-130">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="f7268-131">연결 끊김 PSSession의 명령은 명령이 완료 되거나 출력 버퍼가 채워질 때까지 원격 컴퓨터에서 중단 없이 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-131">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="f7268-132">전체 출력 버퍼가 명령을 일시 중단 하지 않도록 하려면, 또는 cmdlet의 **OutputBufferingMode** 매개 변수를 `Disconnect-PSSession` 사용 `New-PSSessionOption` `New-PSTransportOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-132">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="f7268-133">연결 되지 않은 세션은 원격 컴퓨터에서 연결 되지 않은 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-133">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="f7268-134">Cmdlet을 사용 `Remove-PSSession` 하거나 pssession의 유휴 시간 제한이 만료 될 때 까지는 pssession을 삭제할 때까지 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-134">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="f7268-135">, 또는 cmdlet의 **IdleTimeoutSec** 또는 **IdleTimeout** 매개 변수를 사용 하 여 PSSession의 유휴 시간 제한을 조정할 수 있습니다 `Disconnect-PSSession` `New-PSSessionOption` `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="f7268-135">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="f7268-136">다른 사용자가 만든 pssession에 연결할 수 있지만 세션을 만드는 데 사용 된 자격 증명을 제공할 수 있는 경우에만 `RunAs` 세션 구성의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-136">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="f7268-137">PSSessions를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="f7268-137">How to get PSSessions</span></span>

<span data-ttu-id="f7268-138">PowerShell 3.0부터 `Get-PSSession` cmdlet은 로컬 컴퓨터와 원격 컴퓨터에서 PSSessions를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-138">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="f7268-139">현재 세션에서 만들어진 pssession도 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-139">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="f7268-140">로컬 컴퓨터 또는 원격 컴퓨터에서 pssession을 가져오려면 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-140">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="f7268-141">매개 변수가 없으면는 `Get-PSSession` 종료 위치에 관계 없이 로컬 세션에서 만들어진 PSSession을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-141">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="f7268-142">Pssession을 가져올 때는 해당 세션이 유지 되 고 있는 컴퓨터, 즉 원격 **서버 또는 서버 쪽** 컴퓨터에서이를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-142">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="f7268-143">예를 들어 Server01 컴퓨터에 대 한 PSSession을 만드는 경우 Server01 컴퓨터에서 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-143">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="f7268-144">다른 컴퓨터에서 로컬 컴퓨터로 PSSession을 만드는 경우 로컬 컴퓨터에서 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-144">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="f7268-145">다음 명령 시퀀스는가 작동 하는 방법을 보여 줍니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-145">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="f7268-146">첫 번째 명령은 Server01 컴퓨터에 대 한 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-146">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="f7268-147">세션은 Server01 컴퓨터에 상주 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-147">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="f7268-148">세션을 가져오려면의 **ComputerName** 매개 변수를 `Get-PSSession` Server01 값과 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-148">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="f7268-149">의 **ComputerName** 매개 변수 값 `Get-PSSession` 이 localhost 인 경우는 `Get-PSSession` 에서 종료 되 고 로컬 컴퓨터에서 유지 관리 되는 pssession을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-149">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="f7268-150">로컬 컴퓨터에서 시작 된 경우에도 Server01 컴퓨터에서 pssession을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-150">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="f7268-151">현재 세션에서 만든 세션을 가져오려면 `Get-PSSession` 매개 변수 없이 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-151">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="f7268-152">이 예에서는 `Get-PSSession` 현재 세션에서 만들어진 PSSession을 가져오고 Server01 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-152">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="f7268-153">세션의 연결을 끊는 방법</span><span class="sxs-lookup"><span data-stu-id="f7268-153">How to disconnect sessions</span></span>

<span data-ttu-id="f7268-154">PSSession의 연결을 끊으려면 cmdlet을 사용 `Disconnect-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-154">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="f7268-155">PSSession을 식별 하려면 **Session** 매개 변수를 사용 하거나 또는 cmdlet에서로 pssession을 파이프라인 합니다 `New-PSSession` `Get-PSSession` `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-155">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="f7268-156">다음 명령은 PSSession을 Server01 컴퓨터와의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-156">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="f7268-157">**State** 속성의 값이 **Disconnected** 이 고 **Availability** 가 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-157">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None**.</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="f7268-158">연결 되지 않은 세션을 만들려면 cmdlet의 **InDisconnectedSession** 매개 변수를 사용 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f7268-158">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="f7268-159">명령이 출력을 반환 하기 전에 세션을 만들고, 명령을 시작 하 고, 즉시 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-159">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="f7268-160">다음 명령은 `Get-WinEvent` Server02 원격 컴퓨터의 연결 되지 않은 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-160">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="f7268-161">연결이 끊어진 세션에 연결 하는 방법</span><span class="sxs-lookup"><span data-stu-id="f7268-161">How to connect to disconnected sessions</span></span>

<span data-ttu-id="f7268-162">PSSession을 만든 세션이 나 로컬 컴퓨터 또는 다른 컴퓨터의 다른 세션에서 연결이 끊어진 모든 PSSession에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-162">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="f7268-163">PSSession을 만들고, PSSession에서 명령을 실행 하 고, PSSession에서 연결을 끊고, PowerShell을 닫고, 컴퓨터를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-163">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="f7268-164">나중에 다른 컴퓨터를 열고, PSSession을 가져오고, 연결 하 고, 연결이 끊어진 동안 PSSession에서 실행 된 명령의 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-164">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="f7268-165">그런 다음 세션에서 더 많은 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-165">Then you can run more commands in the session.</span></span>

<span data-ttu-id="f7268-166">연결이 끊어진 PSSession을 연결 하려면 cmdlet을 사용 `Connect-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-166">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="f7268-167">**ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 pssession을 식별 하거나에서로 pssession을 파이프라인 합니다 `Get-PSSession` `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-167">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="f7268-168">다음 명령은 Server02 컴퓨터의 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-168">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="f7268-169">출력에는 두 개의 연결 되지 않은 세션 (둘 다 사용 가능)이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-169">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="f7268-170">다음 명령은 Session2에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-170">The following command connects to Session2.</span></span> <span data-ttu-id="f7268-171">이제 PSSession이 열리고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-171">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="f7268-172">결과를 얻는 방법</span><span class="sxs-lookup"><span data-stu-id="f7268-172">How to get the results</span></span>

<span data-ttu-id="f7268-173">연결 되지 않은 PSSession에서 실행 된 명령의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-173">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="f7268-174">`Receive-PSSession`Cmdlet을 사용 하는 대신을 사용할 수 있습니다 `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-174">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="f7268-175">세션이 이미 다시 연결 된 경우 `Receive-PSSession` 세션의 연결이 끊어질 때 실행 된 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-175">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="f7268-176">PSSession의 연결이 끊어지면에서 연결 된 `Receive-PSSession` 후에도 연결을 끊은 후 실행 된 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-176">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="f7268-177">`Receive-PSSession` 작업 (비동기적으로) 또는 호스트 프로그램 (동기적)으로 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-177">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="f7268-178">**Outtarget** 매개 변수를 사용 하 여 **작업** 또는 **호스트** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-178">Use the **OutTarget** parameter to select **Job** or **Host**.</span></span> <span data-ttu-id="f7268-179">기본값은 **Host** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-179">The default value is **Host**.</span></span> <span data-ttu-id="f7268-180">그러나 수신 중인 명령이 현재 세션에서 **작업** 으로 시작 된 경우에는 기본적으로 **작업** 으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-180">However, if the command that's being received was started in the current session as a **Job** , it's returned as a **Job** by default.</span></span>

<span data-ttu-id="f7268-181">다음 명령은 cmdlet을 사용 하 여 `Receive-PSSession` Server02 컴퓨터의 PSSession에 연결 하 고 `Get-WinEvent` Session3 세션에서 실행 된 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-181">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="f7268-182">이 명령은 **Outtarget** 매개 변수를 사용 하 여 **작업** 의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-182">The command uses the **OutTarget** parameter to get the results in a **Job**.</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="f7268-183">작업의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="f7268-183">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a><span data-ttu-id="f7268-184">상태 및 가용성 속성</span><span class="sxs-lookup"><span data-stu-id="f7268-184">State and Availability properties</span></span>

<span data-ttu-id="f7268-185">연결이 끊어진 PSSession의 **상태** 및 **가용성** 속성은 세션을 연결할 수 있는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-185">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="f7268-186">PSSession이 현재 세션에 연결 되 면 상태가 **열리고** 해당 가용성을 **사용할 수** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-186">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available**.</span></span> <span data-ttu-id="f7268-187">PSSession에서 연결을 끊으면 PSSession 상태의 **연결이 끊어지고** 해당 가용성은 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-187">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None**.</span></span>

<span data-ttu-id="f7268-188">**State** 속성 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-188">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="f7268-189">**연결 끊김** 값은 PSSession이 현재 세션에 연결 되지 않았음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-189">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="f7268-190">그러나 모든 세션에서 PSSession의 연결이 끊어졌음을 의미 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-190">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="f7268-191">다른 세션에 연결되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-191">It might be connected to a different session.</span></span>

<span data-ttu-id="f7268-192">PSSession에 연결 하거나 다시 연결할 수 있는지 확인 하려면 **Availability** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-192">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="f7268-193">**None** 값은 세션에 연결할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-193">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="f7268-194">**사용 중** 값은 다른 세션에 연결 되어 있으므로 PSSession에 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-194">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="f7268-195">다음 예제는 동일한 컴퓨터의 두 PowerShell 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-195">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="f7268-196">PSSession로 각 세션에서 **상태** 및 **가용성** 속성의 변경 값이 연결 해제 되 고 다시 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-196">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

<span data-ttu-id="f7268-197">연결 되지 않은 세션은 cmdlet을 사용 하는 등의 방법으로 삭제 하거나 시간 초과 될 때까지 원격 컴퓨터에서 유지 관리 됩니다 `Remove-PSSession` . PSSession의 **IdleTimeout** 속성은 연결이 끊어진 세션이 삭제 되기 전에 유지 되는 기간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-197">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="f7268-198">PSSessions는 **하트 비트 스레드가** 응답을 받지 못한 경우 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-198">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="f7268-199">연결이 끊어진 세션에서 아직 실행 되 고 있는 경우에도 세션의 연결을 해제 하면 해당 세션은 유휴 상태가 되 고 **IdleTimeout** 시계가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-199">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="f7268-200">PowerShell은 연결 되지 않은 세션을 활성 상태로 유지 하지만 유휴 상태로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-200">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="f7268-201">세션을 만들고 연결을 끊을 때 PSSession의 유휴 시간 제한 시간이 사용자 요구에 대 한 세션을 유지 하는 데 충분 한 긴 하지만 원격 컴퓨터에서 불필요 한 리소스를 사용 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-201">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="f7268-202">세션 구성의 **IdleTimeoutMs** 속성은 세션 구성을 사용 하는 세션의 기본 유휴 제한 시간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-202">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="f7268-203">기본값을 재정의할 수 있지만 사용자가 사용 하는 값은 세션 구성의 **MaxIdleTimeoutMs** 속성을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-203">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="f7268-204">세션 구성의 **IdleTimeoutMs** 및 **MaxIdleTimeoutMs** 값 값을 찾으려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-204">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="f7268-205">PSSession을 만들 때 및 연결을 끊을 때 세션 구성에서 기본값을 재정의 하 고 PSSession의 유휴 시간 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-205">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="f7268-206">원격 컴퓨터에서 Administrators 그룹의 구성원 인 경우 세션 구성의 **IdleTimeoutMs** 및 **MaxIdleTimeoutMs** 속성을 만들고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-206">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="f7268-207">유휴 시간 제한 값</span><span class="sxs-lookup"><span data-stu-id="f7268-207">Idle timeout values</span></span>

<span data-ttu-id="f7268-208">세션 구성 및 세션 옵션의 유휴 시간 제한 값은 밀리초 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-208">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="f7268-209">세션의 유휴 시간 제한 값과 세션 구성 옵션은 초 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-209">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="f7268-210">PSSession ( `New-PSSession` ,)을 만들고 `Invoke-Command` 연결을 끊을 때 () pssession의 유휴 시간 제한을 설정할 수 있습니다 `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-210">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="f7268-211">그러나 PSSession ()에 연결 하거나 결과를 가져올 때는 **IdleTimeout** 값을 변경할 수 없습니다 `Connect-PSSession` ( `Receive-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="f7268-211">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="f7268-212">`Connect-PSSession`및 cmdlet에는 `Receive-PSSession` cmdlet에서 반환 된 것과 같은 **sessionoption** 개체를 사용 하는 **sessionoption** 매개 변수가 있습니다 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="f7268-212">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="f7268-213">**Sessionoption** 개체의 **idletimeout** 값과 기본 설정 변수의 **idletimeout** 값은 `$PSSessionOption` 또는 명령에서 PSSession의 **idletimeout** 값을 변경 하지 않습니다 `Connect-PSSession` `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-213">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="f7268-214">특정 유휴 시간 제한 값을 사용 하 여 PSSession을 만들려면 `$PSSessionOption` 기본 설정 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-214">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="f7268-215">**IdleTimeout** 속성의 값을 원하는 값 (밀리초)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-215">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="f7268-216">Pssession을 만들 때 변수 값이 `$PSSessionOption` 세션 구성의 값 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-216">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="f7268-217">예를 들어 다음 명령은 유휴 시간 제한을 48 시간으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-217">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="f7268-218">특정 유휴 시간 제한 값을 사용 하 여 PSSession을 만들려면 cmdlet의 **IdleTimeoutMSec** 매개 변수를 사용 합니다 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="f7268-218">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="f7268-219">그런 다음 또는 cmdlet의 **sessionoption** 매개 변수 값에서 session 옵션을 사용 합니다 `New-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f7268-219">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="f7268-220">세션을 만들 때 설정 된 값은 `$PSSessionOption` 기본 설정 변수 및 세션 구성에 설정 된 값 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-220">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="f7268-221">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-221">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="f7268-222">연결을 끊을 때 PSSession의 유휴 시간 제한을 변경 하려면 cmdlet의 **IdleTimeoutSec** 매개 변수를 사용 합니다 `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-222">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="f7268-223">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-223">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="f7268-224">특정 유휴 시간 제한 및 최대 유휴 시간 제한으로 세션 구성을 만들려면 cmdlet의 **IdleTimeoutSec** 및 **MaxIdleTimeoutSec** 매개 변수를 사용 합니다 `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="f7268-224">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="f7268-225">그런 다음 **의 매개 변수** 값에서 transport 옵션을 사용 `Register-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-225">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="f7268-226">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-226">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="f7268-227">세션 구성의 기본 유휴 시간 제한 및 최대 유휴 시간 제한을 변경 하려면 cmdlet의 **IdleTimeoutSec** 및 **MaxIdleTimeoutSec** 매개 변수를 사용 합니다 `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="f7268-227">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="f7268-228">그런 다음 **의 매개 변수** 값에서 transport 옵션을 사용 `Set-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-228">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="f7268-229">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-229">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="f7268-230">출력 버퍼링 모드</span><span class="sxs-lookup"><span data-stu-id="f7268-230">Output buffering mode</span></span>

<span data-ttu-id="f7268-231">PSSession의 출력 버퍼링 모드는 PSSession의 출력 버퍼가 가득 찬 경우 명령 출력을 관리 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-231">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="f7268-232">연결이 끊어진 세션에서 출력 버퍼링 모드는 세션의 연결이 끊어지는 동안 명령이 계속 실행 되는지 여부를 효과적으로 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-232">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="f7268-233">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-233">The valid values as follows:</span></span>

- <span data-ttu-id="f7268-234">**블록**.</span><span class="sxs-lookup"><span data-stu-id="f7268-234">**Block**.</span></span> <span data-ttu-id="f7268-235">출력 버퍼가 가득 찰 경우 버퍼를 지울 때까지 실행이 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-235">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="f7268-236">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-236">The default value.</span></span>
- <span data-ttu-id="f7268-237">**Drop**</span><span class="sxs-lookup"><span data-stu-id="f7268-237">**Drop**.</span></span> <span data-ttu-id="f7268-238">출력 버퍼가 가득 차도 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-238">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="f7268-239">새 출력이 생성 되 면 가장 오래 된 출력이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-239">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="f7268-240">**Block** 은 데이터를 유지 하지만 명령을 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-240">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="f7268-241">값이 **Drop** 이면 데이터가 손실될 수는 있지만 명령을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-241">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="f7268-242">**Drop** 값을 사용할 경우 명령 출력을 디스크의 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-242">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="f7268-243">이 값은 연결이 끊어진 세션에 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-243">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="f7268-244">세션 구성의 **OutputBufferingMode** 속성은 세션 구성을 사용 하는 세션의 기본 출력 버퍼링 모드를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-244">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="f7268-245">**OutputBufferingMode** 의 세션 구성 값을 찾기 위해 다음 명령 형식 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-245">To find a session configuration's value of the **OutputBufferingMode** , you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="f7268-246">세션 구성에서 기본값을 재정의 하 고 PSSession을 만들 때, 연결을 끊을 때 및 다시 연결할 때 PSSession의 출력 버퍼링 모드를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-246">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="f7268-247">원격 컴퓨터에서 Administrators 그룹의 구성원 인 경우 세션 구성의 출력 버퍼링 모드를 만들고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-247">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="f7268-248">출력 버퍼링 모드가 **drop** 인 PSSession을 만들려면 `$PSSessionOption` **OutputBufferingMode** 속성 값이 **drop** 인 기본 설정 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-248">To create a PSSession with an output buffering mode of **Drop** , create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop**.</span></span>

<span data-ttu-id="f7268-249">Pssession을 만들 때 변수 값이 `$PSSessionOption` 세션 구성의 값 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-249">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="f7268-250">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-250">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="f7268-251">출력 버퍼링 모드가 **drop** 인 PSSession을 만들려면 Cmdlet의 **OutputBufferingMode** 매개 변수를 사용 하 여 drop 값을 사용 하 `New-PSSessionOption` 여 세션 옵션을 만듭니다. **Drop**</span><span class="sxs-lookup"><span data-stu-id="f7268-251">To create a PSSession with an output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="f7268-252">그런 다음 또는 cmdlet의 **sessionoption** 매개 변수 값에서 session 옵션을 사용 합니다 `New-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f7268-252">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="f7268-253">세션을 만들 때 설정 된 값은 `$PSSessionOption` 기본 설정 변수 및 세션 구성에 설정 된 값 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-253">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="f7268-254">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-254">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="f7268-255">연결을 끊을 때 PSSession의 출력 버퍼링 모드를 변경 하려면 cmdlet의 **OutputBufferingMode** 매개 변수를 사용 합니다 `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-255">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="f7268-256">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-256">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="f7268-257">다시 연결할 때 PSSession의 출력 버퍼링 모드를 변경 하려면 cmdlet의 **OutputBufferingMode** 매개 변수를 사용 `New-PSSessionOption` 하 여 **Drop** 값을 사용 하 여 세션 옵션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-257">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="f7268-258">그런 다음 또는의 **sessionoption** 매개 변수 값에서 session 옵션을 사용 합니다 `Connect-PSSession` `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f7268-258">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="f7268-259">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-259">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="f7268-260">**Drop** 의 기본 출력 버퍼링 모드를 사용 하 여 세션 구성을 만들려면 Cmdlet의 **OutputBufferingMode** 매개 변수를 사용 하 여 `New-PSTransportOption` 값을 **drop** 으로 설정 하 여 전송 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-260">To create a session configuration with a default output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop**.</span></span> <span data-ttu-id="f7268-261">그런 다음 **의 매개 변수** 값에서 transport 옵션을 사용 `Register-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-261">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="f7268-262">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-262">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="f7268-263">세션 구성의 기본 출력 버퍼링 모드를 변경 하려면 cmdlet의 **OutputBufferingMode** 매개 변수를 사용 `New-PSTransportOption` 하 여 값을 **Drop** 으로 설정 하 여 전송 옵션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-263">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop**.</span></span> <span data-ttu-id="f7268-264">그런 다음의 **sessionoption** 매개 변수 값에서 Transport 옵션을 사용 합니다 `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="f7268-264">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="f7268-265">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f7268-265">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="f7268-266">루프백 세션 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="f7268-266">Disconnecting loopback sessions</span></span>

<span data-ttu-id="f7268-267">루프백 세션 또는 로컬 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 pssession입니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-267">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="f7268-268">다른 pssession과 마찬가지로 활성 루프백 세션은 연결의 원격 끝에 있는 컴퓨터 (로컬 컴퓨터)에서 유지 되므로 루프백 세션에서 연결을 끊고 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-268">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="f7268-269">기본적으로 루프백 세션은 세션에서 명령을 실행 하 여 다른 컴퓨터에 액세스할 수 없도록 하는 네트워크 보안 토큰을 사용 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-269">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="f7268-270">로컬 컴퓨터 또는 원격 컴퓨터의 모든 세션에서 네트워크 보안 토큰이 있는 루프백 세션에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-270">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="f7268-271">그러나, 또는 cmdlet의 **EnableNetworkAccess** 매개 변수를 사용 하는 경우 `New-PSSession` `Enter-PSSession` `Invoke-Command` 루프백 세션은 대화형 보안 토큰을 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-271">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="f7268-272">대화형 토큰을 사용 하면 루프백 세션에서 실행 되는 명령을 사용 하 여 다른 컴퓨터에서 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-272">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="f7268-273">대화형 토큰을 사용 하 여 루프백 세션의 연결을 끊은 다음 동일한 세션 또는 동일한 컴퓨터의 다른 세션에서 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-273">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="f7268-274">그러나 악의적인 액세스를 방지 하기 위해 자신이 만든 컴퓨터 에서만 대화형 토큰을 사용 하 여 루프백 세션에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-274">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="f7268-275">연결 되지 않은 세션에서 작업을 기다리는 중</span><span class="sxs-lookup"><span data-stu-id="f7268-275">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="f7268-276">`Wait-Job`Cmdlet은 작업이 완료 될 때까지 대기한 다음 명령 프롬프트나 다음 명령으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-276">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="f7268-277">기본적으로는 `Wait-Job` 작업이 실행 중인 세션의 연결이 끊어질 때를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-277">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="f7268-278">`Wait-Job`세션이 다시 연결 될 때까지 대기 하도록 cmdlet을 지시 하려면 **열린** 상태에서 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-278">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="f7268-279">자세한 내용은 [대기 작업](xref:Microsoft.PowerShell.Core.Wait-Job)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7268-279">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="f7268-280">강력한 세션 및 의도 하지 않은 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="f7268-280">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="f7268-281">컴퓨터 오류 또는 네트워크 중단으로 인해 PSSession의 연결을 실수로 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-281">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="f7268-282">PowerShell은 PSSession을 복구 하려고 시도 하지만 성공 여부는 문제의 심각도와 기간에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-282">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="f7268-283">실수로 연결이 끊긴 PSSession의 상태가 **끊어졌거나** **닫힐** 수 있지만 **연결이 끊어질** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-283">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed** , but it might also be **Disconnected**.</span></span> <span data-ttu-id="f7268-284">**상태** 값이 **disconnected** 인 경우 세션의 연결이 해제 되는 것 처럼 동일한 기술을 사용 하 여 PSSession을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-284">If the value of **State** is **Disconnected** , you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="f7268-285">예를 들어 cmdlet을 사용 하 여 `Connect-PSSession` 세션에 다시 연결 하 고 cmdlet을 사용 하 여 `Receive-PSSession` 세션 연결이 끊어진 동안 실행 된 명령의 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-285">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="f7268-286">명령이 PSSession에서 실행 되는 동안 PSSession이 생성 된 세션을 닫은 (종료) 하면 PowerShell에서 원격 컴퓨터의 **연결 끊김** 상태로 pssession을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-286">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="f7268-287">PSSession을 만든 세션을 닫거나 PSSession에서 실행 되는 명령이 없는 경우 PowerShell은 PSSession을 유지 관리 하려고 시도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7268-287">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7268-288">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7268-288">See also</span></span>

[<span data-ttu-id="f7268-289">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f7268-289">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="f7268-290">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f7268-290">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="f7268-291">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="f7268-291">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="f7268-292">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f7268-292">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="f7268-293">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="f7268-293">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="f7268-294">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f7268-294">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="f7268-295">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f7268-295">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="f7268-296">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f7268-296">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="f7268-297">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="f7268-297">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="f7268-298">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f7268-298">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
