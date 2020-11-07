---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: b0177a00bbbf93659775ee94f7d4898a99f570f3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345581"
---
# <span data-ttu-id="2eebd-103">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-103">Receive-PSSession</span></span>

## <span data-ttu-id="2eebd-104">개요</span><span class="sxs-lookup"><span data-stu-id="2eebd-104">SYNOPSIS</span></span>

<span data-ttu-id="2eebd-105">연결이 끊긴 세션에서 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-105">Gets results of commands in disconnected sessions</span></span>

## <span data-ttu-id="2eebd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2eebd-106">SYNTAX</span></span>

### <span data-ttu-id="2eebd-107">세션(기본값)</span><span class="sxs-lookup"><span data-stu-id="2eebd-107">Session (Default)</span></span>

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eebd-108">Id</span><span class="sxs-lookup"><span data-stu-id="2eebd-108">Id</span></span>

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="2eebd-109">ComputerSessionName 이름</span><span class="sxs-lookup"><span data-stu-id="2eebd-109">ComputerSessionName</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eebd-110">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="2eebd-110">ComputerInstanceId</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eebd-111">ConnectionUriSessionName 이름</span><span class="sxs-lookup"><span data-stu-id="2eebd-111">ConnectionUriSessionName</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eebd-112">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="2eebd-112">ConnectionUriInstanceId</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eebd-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2eebd-113">InstanceId</span></span>

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="2eebd-114">이름</span><span class="sxs-lookup"><span data-stu-id="2eebd-114">SessionName</span></span>

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2eebd-115">설명</span><span class="sxs-lookup"><span data-stu-id="2eebd-115">DESCRIPTION</span></span>

<span data-ttu-id="2eebd-116">`Receive-PSSession`Cmdlet은 분리 된 PowerShell 세션 ( **PSSession** )에서 실행 되는 명령 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-116">The `Receive-PSSession` cmdlet gets the results of commands running in PowerShell sessions ( **PSSession** ) that were disconnected.</span></span> <span data-ttu-id="2eebd-117">세션이 현재 연결 되어 있는 경우 `Receive-PSSession` 세션 연결이 끊어질 때 실행 중 이었던 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-117">If the session is currently connected, `Receive-PSSession` gets the results of commands that were running when the session was disconnected.</span></span> <span data-ttu-id="2eebd-118">세션의 연결이 끊어지면에서 세션에 `Receive-PSSession` 연결 하 여 일시 중단 된 모든 명령을 다시 시작 하 고 세션에서 실행 중인 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-118">If the session is still disconnected, `Receive-PSSession` connects to the session, resumes any commands that were suspended, and gets the results of commands running in the session.</span></span>

<span data-ttu-id="2eebd-119">이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="2eebd-120">`Receive-PSSession`명령 대신 또는를 사용할 수 있습니다 `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-120">You can use a `Receive-PSSession` in addition to or instead of a `Connect-PSSession` command.</span></span>
<span data-ttu-id="2eebd-121">`Receive-PSSession` 다른 세션이 나 다른 컴퓨터에서 시작 된 연결이 끊어졌거나 다시 연결 된 세션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-121">`Receive-PSSession` can connect to any disconnected or reconnected session that was started in other sessions or on other computers.</span></span>

<span data-ttu-id="2eebd-122">`Receive-PSSession`cmdlet 또는 InDisconnectedSession 매개 변수를 사용 하 여 의도적으로 **분리 된 pssession에서 작동** `Disconnect-PSSession` `Invoke-Command` **InDisconnectedSession** 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-122">`Receive-PSSession` works on **PSSessions** that were disconnected intentionally using the `Disconnect-PSSession` cmdlet or the `Invoke-Command` **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="2eebd-123">또는 실수로 네트워크 중단으로 인해 연결을 끊었습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-123">Or disconnected unintentionally by a network interruption.</span></span>

<span data-ttu-id="2eebd-124">`Receive-PSSession`실행 중이거나 일시 중단 된 명령이 없는 세션에 연결 하기 위해 cmdlet을 사용 하는 경우 `Receive-PSSession` 은 세션에 연결 하지만 출력 또는 오류를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-124">If you use the `Receive-PSSession` cmdlet to connect to a session in which no commands are running or suspended, `Receive-PSSession` connects to the session, but returns no output or errors.</span></span>

<span data-ttu-id="2eebd-125">연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-125">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="2eebd-126">일부 예제에서는 스 플랫를 사용 하 여 줄 길이를 줄이고 가독성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-126">Some examples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="2eebd-127">자세한 내용은 [about_Splatting](./About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-127">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="2eebd-128">예제</span><span class="sxs-lookup"><span data-stu-id="2eebd-128">EXAMPLES</span></span>

### <span data-ttu-id="2eebd-129">예제 1: PSSession에 연결</span><span class="sxs-lookup"><span data-stu-id="2eebd-129">Example 1: Connect to a PSSession</span></span>

<span data-ttu-id="2eebd-130">이 예에서는 원격 컴퓨터의 세션에 연결 하 고 세션에서 실행 중인 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-130">This example connects to a session on a remote computer and gets the results of commands that are running in a session.</span></span>

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

<span data-ttu-id="2eebd-131">는 `Receive-PSSession` **ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-131">The `Receive-PSSession` specifies the remote computer with the **ComputerName** parameter.</span></span> <span data-ttu-id="2eebd-132">**Name** 매개 변수는 Server01 컴퓨터의 ittask 세션을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-132">The **Name** parameter identifies the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="2eebd-133">이 예에서는 ITTask 세션에서 실행 중인 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-133">The example gets the results of commands that were running in the ITTask session.</span></span>

<span data-ttu-id="2eebd-134">명령이 **Outtarget** 매개 변수를 사용 하지 않으므로 결과는 명령줄에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-134">Because the command doesn't use the **OutTarget** parameter, the results appear on the command line.</span></span>

### <span data-ttu-id="2eebd-135">예 2: 연결 되지 않은 세션에서 모든 명령의 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="2eebd-135">Example 2: Get results of all commands on disconnected sessions</span></span>

<span data-ttu-id="2eebd-136">이 예제에서는 두 원격 컴퓨터의 연결 되지 않은 모든 세션에서 실행 중인 모든 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-136">This example gets the results of all commands running in all disconnected sessions on two remote computers.</span></span>

<span data-ttu-id="2eebd-137">세션의 연결이 끊어졌거나 명령이 실행 되 고 있지 않은 경우 `Receive-PSSession` 은 세션에 연결 하지 않고 출력 또는 오류를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-137">If any session wasn't disconnected or isn't running commands, `Receive-PSSession` doesn't connect to the session and doesn't return any output or errors.</span></span>

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

<span data-ttu-id="2eebd-138">`Get-PSSession`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-138">`Get-PSSession` uses the **ComputerName** parameter to specify the remote computers.</span></span> <span data-ttu-id="2eebd-139">개체는 파이프라인에서로 전송 됩니다 `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-139">The objects are sent down the pipeline to `Receive-PSSession`.</span></span>

### <span data-ttu-id="2eebd-140">예 3: 세션에서 실행 중인 스크립트의 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="2eebd-140">Example 3: Get the results of a script running in a session</span></span>

<span data-ttu-id="2eebd-141">이 예에서는 cmdlet을 사용 하 여 `Receive-PSSession` 원격 컴퓨터의 세션에서 실행 중인 스크립트의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-141">This example uses the `Receive-PSSession` cmdlet to get the results of a script that was running in a remote computer's session.</span></span>

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

<span data-ttu-id="2eebd-142">**ComputerName** 및 **Name** 매개 변수를 사용하여 연결이 끊긴 세션을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-142">The command uses the **ComputerName** and **Name** parameters to identify the disconnected session.</span></span>
<span data-ttu-id="2eebd-143">작업으로 결과를 반환 하기 위해 작업 값과 함께 **Outtarget** 매개 변수를 사용 `Receive-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-143">It uses the **OutTarget** parameter with a value of Job to direct `Receive-PSSession` to return the results as a job.</span></span> <span data-ttu-id="2eebd-144">**JobName** 매개 변수는 다시 연결 된 세션에서 작업 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-144">The **JobName** parameter specifies a name for the job in the reconnected session.</span></span>
<span data-ttu-id="2eebd-145">**Credential** 매개 변수는 `Receive-PSSession` 도메인 관리자의 사용 권한을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-145">The **Credential** parameter runs the `Receive-PSSession` command using the permissions of a domain administrator.</span></span>

<span data-ttu-id="2eebd-146">출력은 결과를 `Receive-PSSession` 현재 세션에서 작업으로 반환 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-146">The output shows that `Receive-PSSession` returned the results as a job in the current session.</span></span> <span data-ttu-id="2eebd-147">작업 결과를 가져오려면 명령을 사용 합니다. `Receive-Job`</span><span class="sxs-lookup"><span data-stu-id="2eebd-147">To get the job results, use a `Receive-Job` command</span></span>

### <span data-ttu-id="2eebd-148">예 4: 네트워크 중단 후 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="2eebd-148">Example 4: Get results after a network outage</span></span>

<span data-ttu-id="2eebd-149">이 예에서는 cmdlet을 사용 하 여 `Receive-PSSession` 네트워크 중단으로 인해 세션 연결이 중단 된 후 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-149">This example uses the `Receive-PSSession` cmdlet to get the results of a job after a network outage disrupts a session connection.</span></span> <span data-ttu-id="2eebd-150">PowerShell은 다음 4 분 동안 초당 한 번 세션을 다시 연결 하려고 시도 하 고 4 분 간격의 모든 시도가 실패 한 경우에만 활동을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-150">PowerShell automatically attempts to reconnect the session once per second for the next four minutes and abandons the effort only if all attempts in the four-minute interval fail.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

<span data-ttu-id="2eebd-151">`New-PSSession`Cmdlet은 Server01 컴퓨터에서 세션을 만들고이 세션을 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-151">The `New-PSSession` cmdlet creates a session on the Server01 computer and saves the session in the `$s` variable.</span></span> <span data-ttu-id="2eebd-152">`$s`변수가 **상태** 를 열고 **가용성** 을 사용할 수 있음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-152">The `$s` variable displays that the **State** is Opened and the **Availability** is Available.</span></span> <span data-ttu-id="2eebd-153">이러한 값은 세션에 연결 되어 세션에서 명령을 실행할 수 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-153">These values indicate that you're connected to the session and can run commands in the session.</span></span>

<span data-ttu-id="2eebd-154">`Invoke-Command`Cmdlet은 변수의 세션에서 스크립트를 실행 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-154">The `Invoke-Command` cmdlet runs a script in the session in the `$s` variable.</span></span> <span data-ttu-id="2eebd-155">스크립트 실행이 시작되고 데이터를 반환하지만 네트워크 중단이 발생하여 세션이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-155">The script begins to run and return data, but a network outage occurs that interrupts the session.</span></span> <span data-ttu-id="2eebd-156">사용자는 세션을 끝내고 로컬 컴퓨터를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-156">The user has to exit the session and restart the local computer.</span></span>

<span data-ttu-id="2eebd-157">컴퓨터가 다시 시작 되 면 사용자가 PowerShell을 시작 하 고 `Get-PSSession` 명령을 실행 하 여 Server01 컴퓨터에서 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-157">When the computer restarts, the user starts PowerShell and runs a `Get-PSSession` command to get sessions on the Server01 computer.</span></span> <span data-ttu-id="2eebd-158">출력에는 **AD** 세션이 여전히 Server01 컴퓨터에 존재 하는 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-158">The output shows that the **AD** session still exists on the Server01 computer.</span></span> <span data-ttu-id="2eebd-159">**상태** 는 **AD** 세션의 연결이 끊어졌음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-159">The **State** indicates that the **AD** session is disconnected.</span></span> <span data-ttu-id="2eebd-160">None의 **가용성** 값은 세션이 클라이언트 세션에 연결 되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-160">The **Availability** value of None, indicates that the session isn't connected to any client sessions.</span></span>

<span data-ttu-id="2eebd-161">`Receive-PSSession`Cmdlet은 **AD** 세션에 다시 연결 하 고 세션에서 실행 된 스크립트의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-161">The `Receive-PSSession` cmdlet reconnects to the **AD** session and gets the results of the script that ran in the session.</span></span> <span data-ttu-id="2eebd-162">이 명령은 **Outtarget** 매개 변수를 사용 하 여 **adjob** 이라는 작업에서 결과를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-162">The command uses the **OutTarget** parameter to request the results in a job named **ADJob**.</span></span> <span data-ttu-id="2eebd-163">이 명령은 작업 개체를 반환 하 고 출력은 스크립트가 아직 실행 되 고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-163">The command returns a job object and the output indicates that the script is still running.</span></span>

<span data-ttu-id="2eebd-164">`Get-PSSession`Cmdlet은 작업 상태를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-164">The `Get-PSSession` cmdlet is used to check the job state.</span></span> <span data-ttu-id="2eebd-165">출력은 `Receive-PSSession` cmdlet이 **AD** 세션에 다시 연결 된 것을 확인 하 여 명령에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-165">The output confirms that the `Receive-PSSession` cmdlet reconnected to the **AD** session, which is now open and available for commands.</span></span> <span data-ttu-id="2eebd-166">스크립트가 실행을 다시 시작 하 고 스크립트 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-166">And, the script resumed execution and is getting the script results.</span></span>

### <span data-ttu-id="2eebd-167">예 5: 연결이 끊어진 세션에 다시 연결</span><span class="sxs-lookup"><span data-stu-id="2eebd-167">Example 5: Reconnect to disconnected sessions</span></span>

<span data-ttu-id="2eebd-168">이 예에서는 cmdlet을 사용 하 여 `Receive-PSSession` 의도적으로 연결이 끊어진 세션에 다시 연결 하 고 세션에서 실행 중인 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-168">This example uses the `Receive-PSSession` cmdlet to reconnect to sessions that were intentionally disconnected and get the results of jobs that were running in the sessions.</span></span>

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

<span data-ttu-id="2eebd-169">이 `Invoke-Command` cmdlet은 3 개의 원격 컴퓨터에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-169">The `Invoke-Command` cmdlet runs a script on three remote computers.</span></span> <span data-ttu-id="2eebd-170">스크립트는 여러 데이터베이스의 데이터를 수집 하 고 요약 하기 때문에 스크립트를 완료 하는 데 오랜 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-170">Because the script gathers and summarizes data from multiple databases, it often takes the script an extended time to finish.</span></span> <span data-ttu-id="2eebd-171">이 명령은 스크립트를 시작 하는 **InDisconnectedSession** 매개 변수를 사용 하 여 세션의 연결을 즉시 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-171">The command uses the **InDisconnectedSession** parameter that starts the scripts and then immediately disconnects the sessions.</span></span> <span data-ttu-id="2eebd-172">**Sessionoption** 매개 변수는 연결 되지 않은 세션의 **IdleTimeout** 값을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-172">The **SessionOption** parameter extends the **IdleTimeout** value of the disconnected session.</span></span> <span data-ttu-id="2eebd-173">연결 되지 않은 세션은 연결을 끊은 순간부터 유휴 상태로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-173">Disconnected sessions are considered idle from the moment they're disconnected.</span></span> <span data-ttu-id="2eebd-174">명령이 완료 되 고 세션에 다시 연결할 수 있도록 충분 한 시간 동안 유휴 시간 제한 시간을 설정 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-174">It's important to set the idle time-out for long enough so that the commands can complete and you can reconnect to the session.</span></span> <span data-ttu-id="2eebd-175">**PSSession** 을 만든 경우에만 **IdleTimeout** 을 설정 하 고 연결을 끊을 때만이를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-175">You can set the **IdleTimeout** only when you create the **PSSession** and change it only when you disconnect from it.</span></span> <span data-ttu-id="2eebd-176">**PSSession** 에 연결 하거나 결과를 받을 때에는 **IdleTimeout** 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-176">You can't change the **IdleTimeout** value when you connect to a **PSSession** or receiving its results.</span></span> <span data-ttu-id="2eebd-177">명령을 실행 한 후 사용자가 PowerShell을 종료 하 고 컴퓨터를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-177">After running the command, the user exits PowerShell and closes the computer.</span></span>

<span data-ttu-id="2eebd-178">다음 날에는 사용자가 Windows를 다시 시작 하 고, PowerShell을 시작 하 고,를 사용 하 여 `Get-PSSession` 스크립트가 실행 되는 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-178">The next day, the user resumes Windows, starts PowerShell, and uses `Get-PSSession` to get the sessions in which the scripts were running.</span></span> <span data-ttu-id="2eebd-179">이 명령은 컴퓨터 이름, 세션 이름 및 세션 구성의 이름을 기준으로 세션을 식별 하 고이 세션을 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-179">The command identifies the sessions by the computer name, session name, and the name of the session configuration and saves the sessions in the `$s` variable.</span></span> <span data-ttu-id="2eebd-180">`$s`변수의 값이 표시 되 고 세션의 연결이 끊어져 있지만 사용 중이 아닌 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-180">The value of the `$s` variable is displayed and shows that the sessions are disconnected, but aren't busy.</span></span>

<span data-ttu-id="2eebd-181">`Receive-PSSession`Cmdlet은 변수의 세션에 연결 하 여 `$s` 해당 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-181">The `Receive-PSSession` cmdlet connects to the sessions in the `$s` variable and gets their results.</span></span>
<span data-ttu-id="2eebd-182">이 명령은 결과를 `$Results` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-182">The command saves the results in the `$Results` variable.</span></span> <span data-ttu-id="2eebd-183">`$s`변수가 표시 되 고 세션이 연결 되어 명령에 사용할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-183">The `$s` variable is displayed and shows that the sessions are connected and available for commands.</span></span>

<span data-ttu-id="2eebd-184">변수의 스크립트 결과가 `$Results` PowerShell 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-184">The script results in the `$Results` variable are displayed in the PowerShell console.</span></span> <span data-ttu-id="2eebd-185">예기치 않은 결과가 발생 하는 경우 사용자는 세션에서 명령을 실행 하 여 근본 원인을 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-185">If any of the results are unexpected, the user can run commands in the sessions to investigate the root cause.</span></span>

### <span data-ttu-id="2eebd-186">예 6: 연결 되지 않은 세션에서 작업 실행</span><span class="sxs-lookup"><span data-stu-id="2eebd-186">Example 6: Running a job in a disconnected session</span></span>

<span data-ttu-id="2eebd-187">이 예에서는 연결 되지 않은 세션에서 실행 되는 작업의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-187">This example shows what happens to a job that's running in a disconnected session.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

<span data-ttu-id="2eebd-188">`New-PSSession`Cmdlet은 Server01 컴퓨터에서 테스트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-188">The `New-PSSession` cmdlet creates the Test session on the Server01 computer.</span></span> <span data-ttu-id="2eebd-189">이 명령은 세션을 `$s` 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-189">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="2eebd-190">`Invoke-Command`Cmdlet은 변수의 세션에서 명령을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-190">The `Invoke-Command` cmdlet runs a command in the session in the `$s` variable.</span></span> <span data-ttu-id="2eebd-191">이 명령은 **AsJob** 매개 변수를 사용 하 여 명령을 작업으로 실행 하 고 현재 세션에서 작업 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-191">The command uses the **AsJob** parameter to run the command as a job and creates the job object in the current session.</span></span>
<span data-ttu-id="2eebd-192">이 명령은 변수에 저장 된 작업 개체를 반환 합니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-192">The command returns a job object that's saved in the `$j` variable.</span></span> <span data-ttu-id="2eebd-193">`$j`변수는 작업 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-193">The `$j` variable displays the job object.</span></span>

<span data-ttu-id="2eebd-194">변수의 session 개체가 `$s` 파이프라인에서로 전송 되 `Disconnect-PSSession` 고 세션의 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-194">The session object in the `$s` variable is sent down the pipeline to `Disconnect-PSSession` and the session is disconnected.</span></span>

<span data-ttu-id="2eebd-195">`$j`변수가 표시 되 고 변수에서 작업 개체의 연결이 끊어질 때의 영향을 보여 줍니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-195">The `$j` variable is displayed and shows the effect of disconnecting the job object in the `$j` variable.</span></span> <span data-ttu-id="2eebd-196">이제 작업 상태가 Disconnected입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-196">The job state is now Disconnected.</span></span>

<span data-ttu-id="2eebd-197">는 `Receive-Job` 변수의 작업에서 실행 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-197">The `Receive-Job` is run on the job in the `$j` variable.</span></span> <span data-ttu-id="2eebd-198">출력은 세션 및 작업의 연결을 끊기 전에 작업에서 출력 반환을 시작 했다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-198">The output shows that the job began to return output before the session and the job were disconnected.</span></span>

<span data-ttu-id="2eebd-199">`Connect-PSSession`Cmdlet은 동일한 클라이언트 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-199">The `Connect-PSSession` cmdlet is run in the same client session.</span></span> <span data-ttu-id="2eebd-200">명령은 Server01 컴퓨터의 테스트 세션에 다시 연결 하 여 해당 세션을 변수에 저장 합니다 `$s2` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-200">The command reconnects to the Test session on the Server01 computer and saves the session in the `$s2` variable.</span></span>

<span data-ttu-id="2eebd-201">`Receive-PSSession`Cmdlet은 세션에서 실행 중인 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-201">The `Receive-PSSession` cmdlet gets the results of the job that was running in the session.</span></span> <span data-ttu-id="2eebd-202">명령이 동일한 세션에서 실행 되기 때문에는 `Receive-PSSession` 기본적으로 결과를 작업으로 반환 하 고 동일한 작업 개체를 다시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-202">Because the command is run in the same session, `Receive-PSSession` returns the results as a job by default and reuses the same job object.</span></span> <span data-ttu-id="2eebd-203">이 명령은 작업을 `$j2` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-203">The command saves the job in the `$j2` variable.</span></span> <span data-ttu-id="2eebd-204">`Receive-Job`Cmdlet은 변수의 작업 결과를 가져옵니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-204">The `Receive-Job` cmdlet gets the results of the job in the `$j` variable.</span></span>

## <span data-ttu-id="2eebd-205">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2eebd-205">PARAMETERS</span></span>

### <span data-ttu-id="2eebd-206">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="2eebd-206">-AllowRedirection</span></span>

<span data-ttu-id="2eebd-207">이 cmdlet이이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-207">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="2eebd-208">**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-208">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="2eebd-209">기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-209">By default, PowerShell doesn't redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="2eebd-210">또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-210">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="2eebd-211">Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-211">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="2eebd-212">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-212">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-213">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="2eebd-213">-ApplicationName</span></span>

<span data-ttu-id="2eebd-214">응용 프로그램을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-214">Specifies an application.</span></span> <span data-ttu-id="2eebd-215">이 cmdlet은 지정 된 응용 프로그램을 사용 하는 세션에만 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-215">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="2eebd-216">연결 URI의 애플리케이션 이름 세그먼트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-216">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="2eebd-217">예를 들어 다음 연결 URI에서 WSMan은 응용 프로그램 이름 `http://localhost:5985/WSMAN` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-217">For example, in the following connection URI, WSMan is the application name: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="2eebd-218">세션의 응용 프로그램 이름은 세션의 **Runspace.ConnectionInfo.AppName** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-218">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="2eebd-219">매개 변수의 값은 세션을 선택 및 필터링 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-219">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="2eebd-220">세션에서 사용 하는 응용 프로그램은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-220">It doesn't change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-221">-인증</span><span class="sxs-lookup"><span data-stu-id="2eebd-221">-Authentication</span></span>

<span data-ttu-id="2eebd-222">연결이 끊어진 세션에 다시 연결 하기 위해 명령에서 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-222">Specifies the mechanism that's used to authenticate the user credentials in the command to reconnect to a disconnected session.</span></span> <span data-ttu-id="2eebd-223">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-223">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2eebd-224">기본값</span><span class="sxs-lookup"><span data-stu-id="2eebd-224">Default</span></span>
- <span data-ttu-id="2eebd-225">Basic</span><span class="sxs-lookup"><span data-stu-id="2eebd-225">Basic</span></span>
- <span data-ttu-id="2eebd-226">Credssp</span><span class="sxs-lookup"><span data-stu-id="2eebd-226">Credssp</span></span>
- <span data-ttu-id="2eebd-227">다이제스트</span><span class="sxs-lookup"><span data-stu-id="2eebd-227">Digest</span></span>
- <span data-ttu-id="2eebd-228">Kerberos</span><span class="sxs-lookup"><span data-stu-id="2eebd-228">Kerberos</span></span>
- <span data-ttu-id="2eebd-229">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2eebd-229">Negotiate</span></span>
- <span data-ttu-id="2eebd-230">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="2eebd-230">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="2eebd-231">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-231">The default value is Default.</span></span>

<span data-ttu-id="2eebd-232">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-232">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="2eebd-233">사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스 (예: 원격 네트워크 공유 액세스)에 대 한 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-233">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="2eebd-234">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-234">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="2eebd-235">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-235">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-236">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="2eebd-236">-CertificateThumbprint</span></span>

<span data-ttu-id="2eebd-237">연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-237">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="2eebd-238">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-238">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="2eebd-239">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-239">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="2eebd-240">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정으로는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-240">Certificates can be mapped only to local user accounts, and don't work with domain accounts.</span></span>

<span data-ttu-id="2eebd-241">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-241">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-242">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2eebd-242">-ComputerName</span></span>

<span data-ttu-id="2eebd-243">연결이 끊긴 세션을 저장할 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-243">Specifies the computer on which the disconnected session is stored.</span></span> <span data-ttu-id="2eebd-244">세션은 서버 쪽 또는 연결 끝에 있는 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-244">Sessions are stored on the computer that's at the server-side, or receiving end of a connection.</span></span> <span data-ttu-id="2eebd-245">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-245">The default is the local computer.</span></span>

<span data-ttu-id="2eebd-246">한 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-246">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one computer.</span></span>
<span data-ttu-id="2eebd-247">와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-247">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="2eebd-248">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ), 또는 localhost를 입력 합니다 `$env:COMPUTERNAME` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-248">To specify the local computer, type the computer name, a dot (`.`), `$env:COMPUTERNAME`, or localhost.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-249">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="2eebd-249">-ConfigurationName</span></span>

<span data-ttu-id="2eebd-250">세션 구성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-250">Specifies the name of a session configuration.</span></span> <span data-ttu-id="2eebd-251">이 cmdlet은 지정 된 세션 구성을 사용 하는 세션에만 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-251">This cmdlet connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="2eebd-252">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-252">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="2eebd-253">구성 이름만 지정하는 경우 다음 스키마 URI가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-253">If you specify only the configuration name, the following schema URI is prepended:</span></span>

<span data-ttu-id="2eebd-254">`http://schemas.microsoft.com/powershell`.</span><span class="sxs-lookup"><span data-stu-id="2eebd-254">`http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="2eebd-255">세션의 구성 이름은 세션의 **ConfigurationName** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-255">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="2eebd-256">매개 변수의 값은 세션을 선택 및 필터링 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-256">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="2eebd-257">세션에서 사용 하는 세션 구성을 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-257">It doesn't change the session configuration that the session uses.</span></span>

<span data-ttu-id="2eebd-258">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](./About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-258">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-259">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2eebd-259">-ConnectionUri</span></span>

<span data-ttu-id="2eebd-260">연결이 끊어진 세션에 다시 연결 하는 데 사용 되는 연결 끝점을 정의 하는 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-260">Specifies a URI that defines the connection endpoint that is used to reconnect to the disconnected session.</span></span>

<span data-ttu-id="2eebd-261">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-261">The URI must be fully qualified.</span></span> <span data-ttu-id="2eebd-262">문자열 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-262">The string's format is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="2eebd-263">기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-263">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="2eebd-264">연결 URI를 지정 하지 않으면 **UseSSL** , **ComputerName** , **Port** 및 **ApplicationName** 매개 변수를 사용 하 여 연결 uri 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-264">If you don't specify a connection URI, you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="2eebd-265">URI의 **Transport** 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-265">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="2eebd-266">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션이 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-266">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with standard ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="2eebd-267">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-267">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="2eebd-268">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-268">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-269">-Credential</span><span class="sxs-lookup"><span data-stu-id="2eebd-269">-Credential</span></span>

<span data-ttu-id="2eebd-270">연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-270">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="2eebd-271">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-271">The default is the current user.</span></span>

<span data-ttu-id="2eebd-272">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-272">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2eebd-273">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-273">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2eebd-274">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-274">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2eebd-275">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="2eebd-275">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-276">-Id</span><span class="sxs-lookup"><span data-stu-id="2eebd-276">-Id</span></span>

<span data-ttu-id="2eebd-277">연결 되지 않은 세션의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-277">Specifies the ID of a disconnected session.</span></span> <span data-ttu-id="2eebd-278">**Id** 매개 변수는 연결이 끊어진 세션이 이전에 현재 세션에 연결 된 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-278">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="2eebd-279">이 매개 변수는 유효 하지만, 세션이 로컬 컴퓨터에 저장 되어 있지만 현재 세션에 연결 되지 않은 경우 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-279">This parameter is valid, but not effective, when the session is stored on the local computer, but wasn't connected to the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-280">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="2eebd-280">-InstanceId</span></span>

<span data-ttu-id="2eebd-281">연결이 끊긴 세션의 인스턴스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-281">Specifies the instance ID of the disconnected session.</span></span> <span data-ttu-id="2eebd-282">인스턴스 ID는 로컬 또는 원격 컴퓨터의 **PSSession** 을 고유 하 게 식별 하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-282">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span> <span data-ttu-id="2eebd-283">인스턴스 ID는 **PSSession** 의 **InstanceID** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-283">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-284">-JobName</span><span class="sxs-lookup"><span data-stu-id="2eebd-284">-JobName</span></span>

<span data-ttu-id="2eebd-285">에서 반환 하는 작업의 이름을 지정 합니다 `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-285">Specifies a friendly name for the job that `Receive-PSSession` returns.</span></span>

<span data-ttu-id="2eebd-286">`Receive-PSSession`**Outtarget** 매개 변수 값이 job 이거나 연결이 끊어진 세션에서 실행 중인 작업이 현재 세션에서 시작 된 경우 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-286">`Receive-PSSession` returns a job when the value of the **OutTarget** parameter is Job or the job that's running in the disconnected session was started in the current session.</span></span>

<span data-ttu-id="2eebd-287">연결 되지 않은 세션에서 실행 중인 작업이 현재 세션에서 시작 된 경우 PowerShell은 세션에서 원래 작업 개체를 재사용 하 고 **JobName** 매개 변수의 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-287">If the job that's running in the disconnected session was started in the current session, PowerShell reuses the original job object in the session and ignores the value of the **JobName** parameter.</span></span>

<span data-ttu-id="2eebd-288">연결 되지 않은 세션에서 실행 중인 작업이 다른 세션에서 시작 된 경우 PowerShell에서 새 작업 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-288">If the job that's running in the disconnected session was started in a different session, PowerShell creates a new job object.</span></span> <span data-ttu-id="2eebd-289">기본 이름이 사용되지만 이 매개 변수를 사용하여 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-289">It uses a default name, but you can use this parameter to change the name.</span></span>

<span data-ttu-id="2eebd-290">**Outtarget** 매개 변수의 기본값 또는 명시적 값이 Job이 아닌 경우 명령은 성공 하지만 **JobName** 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-290">If the default value or explicit value of the **OutTarget** parameter isn't Job, the command succeeds, but the **JobName** parameter has no effect.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-291">-Name</span><span class="sxs-lookup"><span data-stu-id="2eebd-291">-Name</span></span>

<span data-ttu-id="2eebd-292">연결이 끊긴 세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-292">Specifies the friendly name of the disconnected session.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-293">-OutTarget</span><span class="sxs-lookup"><span data-stu-id="2eebd-293">-OutTarget</span></span>

<span data-ttu-id="2eebd-294">세션 결과가 반환되는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-294">Determines how the session results are returned.</span></span> <span data-ttu-id="2eebd-295">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-295">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2eebd-296">**작업**.</span><span class="sxs-lookup"><span data-stu-id="2eebd-296">**Job**.</span></span> <span data-ttu-id="2eebd-297">작업 개체에 결과를 비동기적으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-297">Returns the results asynchronously in a job object.</span></span> <span data-ttu-id="2eebd-298">**JobName** 매개 변수를 사용하여 작업의 이름이나 새 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-298">You can use the **JobName** parameter to specify a name or new name for the job.</span></span>
- <span data-ttu-id="2eebd-299">**호스트**.</span><span class="sxs-lookup"><span data-stu-id="2eebd-299">**Host**.</span></span> <span data-ttu-id="2eebd-300">결과를 명령줄에 반환합니다(동기적).</span><span class="sxs-lookup"><span data-stu-id="2eebd-300">Returns the results to the command line (synchronously).</span></span> <span data-ttu-id="2eebd-301">명령을 다시 시작 중이거나 결과가 다수의 개체로 구성된 경우 응답이 지연될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-301">If the command is being resumed or the results consist of a large number of objects, the response might be delayed.</span></span>

<span data-ttu-id="2eebd-302">**Outtarget** 매개 변수의 기본값은 Host입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-302">The default value of the **OutTarget** parameter is Host.</span></span> <span data-ttu-id="2eebd-303">연결이 끊어진 세션에서 수신 중인 명령이 현재 세션에서 시작 된 경우 **Outtarget** 매개 변수의 기본값은 명령이 시작 된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-303">If the command that's being received in a disconnected session was started in the current session, the default value of the **OutTarget** parameter is the form in which the command was started.</span></span> <span data-ttu-id="2eebd-304">명령이 작업으로 시작 된 경우 기본적으로 작업으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-304">If the command was started as a job, by default, it's returned as a job.</span></span> <span data-ttu-id="2eebd-305">그렇지 않으면 기본적으로 호스트 프로그램에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-305">Otherwise, it's returned to the host program by default.</span></span>

<span data-ttu-id="2eebd-306">일반적으로 호스트 프로그램은 반환된 개체를 명령줄에 지연 없이 표시하지만 이 동작은 경우에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-306">Typically, the host program displays returned objects at the command line without delay, but this behavior can vary.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-307">-Port</span><span class="sxs-lookup"><span data-stu-id="2eebd-307">-Port</span></span>

<span data-ttu-id="2eebd-308">세션에 다시 연결 하는 데 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-308">Specifies the remote computer's network port that's used to reconnect to the session.</span></span> <span data-ttu-id="2eebd-309">원격 컴퓨터에 연결 하려면 연결에서 사용 하는 포트에서 수신 대기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-309">To connect to a remote computer, it must be listening on the port that the connection uses.</span></span> <span data-ttu-id="2eebd-310">기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-310">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="2eebd-311">대체 포트를 사용 하기 전에 해당 포트에서 수신 대기 하도록 원격 컴퓨터의 WinRM 수신기를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-311">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen on that port.</span></span> <span data-ttu-id="2eebd-312">수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-312">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="2eebd-313">필요한 경우가 아니면 **Port** 매개 변수를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-313">Don't use the **Port** parameter unless it's necessary.</span></span> <span data-ttu-id="2eebd-314">명령에 설정 된 포트는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-314">The port that's set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="2eebd-315">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-315">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-316">-Session</span><span class="sxs-lookup"><span data-stu-id="2eebd-316">-Session</span></span>

<span data-ttu-id="2eebd-317">연결이 끊긴 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-317">Specifies the disconnected session.</span></span> <span data-ttu-id="2eebd-318">**Pssession이** 포함 된 변수 또는 **pssession** 을 만들거나 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-318">Enter a variable that contains the **PSSession** or a command that creates or gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-319">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="2eebd-319">-SessionOption</span></span>

<span data-ttu-id="2eebd-320">세션에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-320">Specifies advanced options for the session.</span></span> <span data-ttu-id="2eebd-321">Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-321">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="2eebd-322">옵션의 기본값은 설정 된 경우 기본 설정 변수의 값에 따라 결정 됩니다 `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-322">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="2eebd-323">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-323">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="2eebd-324">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-324">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="2eebd-325">그러나 세션 구성에 설정 된 최대값, 할당량 또는 제한 보다 우선 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-325">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="2eebd-326">기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-326">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="2eebd-327">**$PSSessionOption** 기본 설정 변수에 대 한 자세한 내용은 [about_Preference_Variables](./About/about_Preference_Variables.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-327">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span> <span data-ttu-id="2eebd-328">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](./About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-328">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-329">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="2eebd-329">-UseSSL</span></span>

<span data-ttu-id="2eebd-330">이 cmdlet은 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 연결이 끊어진 세션에 연결 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-330">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="2eebd-331">기본적으로 SSL은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-331">By default, SSL isn't used.</span></span>

<span data-ttu-id="2eebd-332">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-332">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="2eebd-333">**UseSSL** 은 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 보내는 추가 보호입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-333">**UseSSL** is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="2eebd-334">이 매개 변수를 사용 하 고 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-334">If you use this parameter and SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-335">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2eebd-335">-Confirm</span></span>

<span data-ttu-id="2eebd-336">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-336">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-337">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2eebd-337">-WhatIf</span></span>

<span data-ttu-id="2eebd-338">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-338">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2eebd-339">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-339">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2eebd-340">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2eebd-340">CommonParameters</span></span>

<span data-ttu-id="2eebd-341">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2eebd-341">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2eebd-342">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-342">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2eebd-343">입력</span><span class="sxs-lookup"><span data-stu-id="2eebd-343">INPUTS</span></span>

### <span data-ttu-id="2eebd-344">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-344">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="2eebd-345">Cmdlet에서 반환 된 개체와 같이 session 개체를이 cmdlet으로 파이프 할 수 있습니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-345">You can pipe session objects to this cmdlet, such as objects returned by the `Get-PSSession` cmdlet.</span></span>

### <span data-ttu-id="2eebd-346">System.Int32</span><span class="sxs-lookup"><span data-stu-id="2eebd-346">System.Int32</span></span>

<span data-ttu-id="2eebd-347">세션 Id를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-347">You can pipe session Ids to this cmdlet.</span></span>

### <span data-ttu-id="2eebd-348">System.Guid</span><span class="sxs-lookup"><span data-stu-id="2eebd-348">System.Guid</span></span>

<span data-ttu-id="2eebd-349">이 cmdlet은 세션의 인스턴스 Id를 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-349">You can pipe the instance Ids of sessions this cmdlet.</span></span>

### <span data-ttu-id="2eebd-350">System.String</span><span class="sxs-lookup"><span data-stu-id="2eebd-350">System.String</span></span>

<span data-ttu-id="2eebd-351">세션 이름을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-351">You can pipe session names to this cmdlet.</span></span>

## <span data-ttu-id="2eebd-352">출력</span><span class="sxs-lookup"><span data-stu-id="2eebd-352">OUTPUTS</span></span>

### <span data-ttu-id="2eebd-353">System.object 또는 PSObject</span><span class="sxs-lookup"><span data-stu-id="2eebd-353">System.Management.Automation.Job or PSObject</span></span>

<span data-ttu-id="2eebd-354">이 cmdlet은 연결 되지 않은 세션에서 실행 된 명령의 결과를 반환 합니다 (있는 경우).</span><span class="sxs-lookup"><span data-stu-id="2eebd-354">This cmdlet returns the results of commands that ran in the disconnected session, if any.</span></span> <span data-ttu-id="2eebd-355">**Outtarget** 매개 변수의 값 또는 기본값이 job 인 경우은 `Receive-PSSession` 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-355">If the value or default value of the **OutTarget** parameter is Job, `Receive-PSSession` returns a job object.</span></span> <span data-ttu-id="2eebd-356">그러지 않으면 해당 명령 결과를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-356">Otherwise, it returns objects that represent that command results.</span></span>

## <span data-ttu-id="2eebd-357">참고</span><span class="sxs-lookup"><span data-stu-id="2eebd-357">NOTES</span></span>

<span data-ttu-id="2eebd-358">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-358">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="2eebd-359">`Receive-PSSession` 연결을 끊은 세션 에서만 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-359">`Receive-PSSession` gets results only from sessions that were disconnected.</span></span> <span data-ttu-id="2eebd-360">PowerShell 3.0 이상 버전을 실행 하는 컴퓨터에서는 연결 또는 종료 된 세션만 연결을 끊고 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-360">Only sessions that are connected to, or terminate at, computers that run PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

<span data-ttu-id="2eebd-361">연결 되지 않은 세션에서 실행 중 이었던 명령이 결과를 생성 하지 않거나 결과가 이미 다른 세션으로 반환 된 경우에서 `Receive-PSSession` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-361">If the commands that were running in the disconnected session didn't generate results or if the results were already returned to another session, `Receive-PSSession` doesn't generate any output.</span></span>

<span data-ttu-id="2eebd-362">세션의 출력 버퍼링 모드는 세션의 연결이 끊어질 때 세션의 명령이 출력을 관리 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-362">A session's output buffering mode determines how commands in the session manage output when the session is disconnected.</span></span> <span data-ttu-id="2eebd-363">세션의 **OutputBufferingMode** 옵션 값이 Drop이 고 출력 버퍼가 가득 차면 명령이 출력을 삭제 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-363">When the value of the **OutputBufferingMode** option of the session is Drop and the output buffer is full, the command starts to delete output.</span></span> <span data-ttu-id="2eebd-364">`Receive-PSSession` 이 출력을 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-364">`Receive-PSSession` can't recover this output.</span></span> <span data-ttu-id="2eebd-365">출력 버퍼링 모드 옵션에 대 한 자세한 내용은 [새-PSSessionOption](New-PSSessionOption.md) 및 [new-pstransportoption](New-PSTransportOption.md) cmdlet에 대 한 도움말 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eebd-365">For more information about the output buffering mode option, see the help articles for the [New-PSSessionOption](New-PSSessionOption.md) and [New-PSTransportOption](New-PSTransportOption.md) cmdlets.</span></span>

<span data-ttu-id="2eebd-366">**Pssession** 에 연결 하거나 결과를 수신할 때 **pssession** 의 유휴 시간 제한 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-366">You can't change the idle time-out value of a **PSSession** when you connect to the **PSSession** or receive results.</span></span> <span data-ttu-id="2eebd-367">의 **sessionoption** 매개 변수는 `Receive-PSSession` **IdleTimeout** 값을 포함 하는 **sessionoption** 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-367">The **SessionOption** parameter of `Receive-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="2eebd-368">그러나 **IdleTimeout** PSSession에 연결 하거나 결과를 수신할 때 **Sessionoption** 개체의 idletimeout 값과 **idletimeout** 값은 `$PSSessionOption` 무시 됩니다. **PSSession**</span><span class="sxs-lookup"><span data-stu-id="2eebd-368">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when it connects to a **PSSession** or receiving results.</span></span>

- <span data-ttu-id="2eebd-369">또는 cmdlet을 사용 하 **PSSession** 고 pssession에서 연결을 끊으면 pssession **을 만들 때 pssession** 의 유휴 시간 제한 시간을 설정 하 고 변경할 수 있습니다 `New-PSSession` `Invoke-Command` . **PSSession**</span><span class="sxs-lookup"><span data-stu-id="2eebd-369">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>
- <span data-ttu-id="2eebd-370">**PSSession** 의 **IdleTimeout** 속성은 연결이 끊어진 세션이 원격 컴퓨터에서 유지 되는 기간을 결정 하기 때문에 연결이 끊어진 세션에 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-370">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="2eebd-371">연결이 끊긴 세션은 연결이 끊긴 세션에서 명령을 실행 중인 경우에도 연결이 끊긴 순간부터 유휴 상태로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-371">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="2eebd-372">Cmdlet의 **AsJob** 매개 변수를 사용 하 여 원격 세션에서 작업 시작을 시작 하면 작업이 `Invoke-Command` 원격 세션에서 실행 되는 경우에도 현재 세션에서 작업 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-372">If you start a start a job in a remote session by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is created in the current session, even though the job runs in the remote session.</span></span> <span data-ttu-id="2eebd-373">원격 세션의 연결을 끊으면 현재 세션의 작업 개체를 작업에서 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-373">If you disconnect the remote session, the job object in the current session is disconnected from the job.</span></span> <span data-ttu-id="2eebd-374">작업 개체는 반환 된 결과를 포함 하지만 연결 되지 않은 세션의 작업에서 새 결과를 수신 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-374">The job object contains any results that were returned to it, but doesn't receive new results from the job in the disconnected session.</span></span>

<span data-ttu-id="2eebd-375">다른 클라이언트가 실행 중인 작업을 포함 하는 세션에 연결 하는 경우 원래 세션의 원래 작업 개체에 전달 된 결과를 새로 연결 된 세션에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-375">If a different client connects to the session that contains the running job, the results that were delivered to the original job object in the original session aren't available in the newly connected session.</span></span> <span data-ttu-id="2eebd-376">원래 작업 개체에 전달되지 않은 결과만 다시 연결된 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-376">Only results that were not delivered to the original job object are available in the reconnected session.</span></span>

<span data-ttu-id="2eebd-377">마찬가지로, 세션에서 스크립트를 시작한 다음 세션에서 연결을 끊는 경우에는 세션에 연결 하는 다른 클라이언트에서 연결을 끊기 전에 스크립트가 세션에 전달 하는 결과를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-377">Similarly, if you start a script in a session and then disconnect from the session, any results that the script delivers to the session before disconnecting aren't available to another client that connects to the session.</span></span>

<span data-ttu-id="2eebd-378">연결을 끊을 세션에서 데이터 손실을 방지 하려면 cmdlet의 **InDisconnectedSession** 매개 변수를 사용 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="2eebd-378">To prevent data loss in sessions that you intend to disconnect, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="2eebd-379">이 매개 변수는 결과가 현재 세션에 반환되지 않도록 하기 때문에 세션을 다시 연결할 때 모든 결과를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-379">Because this parameter prevents results from being returned to the current session, all results are available when the session is reconnected.</span></span>

<span data-ttu-id="2eebd-380">Cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` 원격 세션에서 명령을 실행 하 여 데이터 손실을 방지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-380">You can also prevent data loss by using the `Invoke-Command` cmdlet to run a `Start-Job` command in the remote session.</span></span> <span data-ttu-id="2eebd-381">이 경우 작업 개체가 원격 세션에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-381">In this case, the job object is created in the remote session.</span></span> <span data-ttu-id="2eebd-382">Cmdlet을 사용 `Receive-PSSession` 하 여 작업 결과를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-382">You can't use the `Receive-PSSession` cmdlet to get the job results.</span></span> <span data-ttu-id="2eebd-383">대신 cmdlet을 사용 하 여 `Connect-PSSession` 세션에 연결한 다음 cmdlet을 사용 하 여 `Invoke-Command` `Receive-Job` 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-383">Instead, use the `Connect-PSSession` cmdlet to connect to the session and then use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session.</span></span>

<span data-ttu-id="2eebd-384">실행 중인 작업을 포함 하는 세션의 연결을 끊은 다음 다시 연결 하면 작업의 연결이 끊어지고 동일한 세션에 다시 연결 된 경우에만 원래 작업 개체가 다시 사용 되며, 다시 연결 하는 명령에서 새 작업 이름을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-384">When a session that contains a running job is disconnected and then reconnected, the original job object is reused only if the job is disconnected and reconnected to the same session, and the command to reconnect doesn't specify a new job name.</span></span> <span data-ttu-id="2eebd-385">세션이 다른 클라이언트 세션에 다시 연결 되어 있거나 새 작업 이름이 지정 된 경우 PowerShell에서 새 세션에 대 한 새 작업 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-385">If the session is reconnected to a different client session or a new job name is specified, PowerShell creates a new job object for the new session.</span></span>

<span data-ttu-id="2eebd-386">**PSSession** 의 연결을 끊으면 세션 상태가 Disconnected이 고 Availability가 None입니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-386">When you disconnect a **PSSession** , the session state is Disconnected and the availability is None.</span></span>

- <span data-ttu-id="2eebd-387">**State** 속성 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-387">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="2eebd-388">연결 끊김 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-388">A value of Disconnected means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="2eebd-389">그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-389">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="2eebd-390">다른 세션에 연결되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-390">It might be connected to a different session.</span></span>
  <span data-ttu-id="2eebd-391">세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-391">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>
- <span data-ttu-id="2eebd-392">**가용성** 값 None은 세션에 연결할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-392">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="2eebd-393">사용 중 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2eebd-393">A value of Busy indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span>
- <span data-ttu-id="2eebd-394">세션의 **State** 속성 값에 대 한 자세한 내용은 MSDN Library에서 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2eebd-394">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate) in the MSDN library.</span></span>
- <span data-ttu-id="2eebd-395">세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2eebd-395">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="2eebd-396">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2eebd-396">RELATED LINKS</span></span>

[<span data-ttu-id="2eebd-397">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="2eebd-397">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="2eebd-398">about_Remote</span><span class="sxs-lookup"><span data-stu-id="2eebd-398">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="2eebd-399">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="2eebd-399">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="2eebd-400">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="2eebd-400">about_Session_Configurations</span></span>](./About/about_Session_Configurations.md)

[<span data-ttu-id="2eebd-401">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-401">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="2eebd-402">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-402">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="2eebd-403">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-403">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="2eebd-404">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-404">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="2eebd-405">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2eebd-405">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="2eebd-406">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-406">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="2eebd-407">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="2eebd-407">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="2eebd-408">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="2eebd-408">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="2eebd-409">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="2eebd-409">Remove-PSSession</span></span>](Remove-PSSession.md)
