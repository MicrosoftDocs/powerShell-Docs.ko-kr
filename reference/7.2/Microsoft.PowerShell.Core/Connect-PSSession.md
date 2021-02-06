---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: fda672ba4f6dafc9f955ef8025c386f7732d81bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601060"
---
# <span data-ttu-id="8f0da-102">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-102">Connect-PSSession</span></span>

## <span data-ttu-id="8f0da-103">개요</span><span class="sxs-lookup"><span data-stu-id="8f0da-103">SYNOPSIS</span></span>
<span data-ttu-id="8f0da-104">연결이 끊긴 세션에 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-104">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="8f0da-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8f0da-105">SYNTAX</span></span>

### <span data-ttu-id="8f0da-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="8f0da-106">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-107">세션</span><span class="sxs-lookup"><span data-stu-id="8f0da-107">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-108">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="8f0da-108">ComputerNameGuid</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-109">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="8f0da-109">ComputerName</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-110">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="8f0da-110">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8f0da-111">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8f0da-112">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8f0da-113">Id</span><span class="sxs-lookup"><span data-stu-id="8f0da-113">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8f0da-114">설명</span><span class="sxs-lookup"><span data-stu-id="8f0da-114">DESCRIPTION</span></span>

<span data-ttu-id="8f0da-115">`Connect-PSSession`이 cmdlet은 연결을 끊은 사용자 관리 PowerShell 세션 (**pssessions**)에 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-115">The `Connect-PSSession` cmdlet reconnects to user-managed PowerShell sessions (**PSSessions**) that were disconnected.</span></span> <span data-ttu-id="8f0da-116">이 cmdlet은 cmdlet의 cmdlet 또는 InDisconnectedSession 매개 변수를 사용 하는 등의 방법으로 의도적으로 연결 되지 않은 세션에서 작동 `Disconnect-PSSession` 하며,  `Invoke-Command` 일시적인 네트워크 중단 등으로 인해 실수로 연결 해제 된 세션 에서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-116">It works on sessions that are disconnected intentionally, such as by using the `Disconnect-PSSession` cmdlet or the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="8f0da-117">`Connect-PSSession` 동일한 사용자가 시작한 연결이 끊어진 세션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-117">`Connect-PSSession` can connect to any disconnected session that was started by the same user.</span></span> <span data-ttu-id="8f0da-118">여기에는 다른 컴퓨터의 다른 세션에서 시작 되거나 연결 해제 된 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-118">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="8f0da-119">그러나 `Connect-PSSession` 은 (는) cmdlet을 사용 하 여 시작 된 끊어진 세션 또는 대화형 세션에 연결할 수 없습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-119">However, `Connect-PSSession` cannot connect to broken or closed sessions, or interactive sessions started by using the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="8f0da-120">또한 세션을 만든 사용자의 자격 증명을 제공할 수 없는 경우 다른 사용자가 시작한 세션에 세션을 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-120">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="8f0da-121">연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="8f0da-122">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-122">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="8f0da-123">예제</span><span class="sxs-lookup"><span data-stu-id="8f0da-123">EXAMPLES</span></span>

### <span data-ttu-id="8f0da-124">예 1: 세션에 다시 연결</span><span class="sxs-lookup"><span data-stu-id="8f0da-124">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="8f0da-125">이 명령은 Server01 컴퓨터의 ITTask 세션에 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-125">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="8f0da-126">출력은 명령이 성공했음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-126">The output shows that the command was successful.</span></span> <span data-ttu-id="8f0da-127">세션의 **상태가** 열리고 **가용성** 을 사용할 수 있습니다 .이는 세션에서 명령을 실행할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-127">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="8f0da-128">예 2: 연결 끊기 및 다시 연결 효과</span><span class="sxs-lookup"><span data-stu-id="8f0da-128">Example 2: Effect of disconnecting and reconnecting</span></span>

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

<span data-ttu-id="8f0da-129">이 예제에서는 세션의 연결을 끊고 세션에 다시 연결할 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-129">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="8f0da-130">첫 번째 명령은 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-130">The first command uses the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="8f0da-131">**ComputerName** 매개 변수가 없을 경우 명령은 현재 세션에서 만들어진 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-131">Without the **ComputerName** parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="8f0da-132">출력은 명령이 로컬 컴퓨터의 백업 세션을 가져옴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-132">The output shows that the command gets the Backups session on the local computer.</span></span> <span data-ttu-id="8f0da-133">세션 **상태가** 열리고 **가용성** 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-133">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="8f0da-134">두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 현재 세션에서 만들어진 **PSSession** 개체를 가져오고, cmdlet을 사용 하 여 `Disconnect-PSSession` 세션의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-134">The second command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Disconnect-PSSession` cmdlet to disconnect the sessions.</span></span> <span data-ttu-id="8f0da-135">출력은 백업 세션의 연결이 끊겼음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-135">The output shows that the Backups session was disconnected.</span></span> <span data-ttu-id="8f0da-136">세션 **상태가** Disconnected이 고 **Availability** 가 None입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-136">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="8f0da-137">세 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 현재 세션에서 만들어진 **PSSession** 개체를 가져오고, cmdlet을 사용 하 여 `Connect-PSSession` 세션을 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-137">The third command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Connect-PSSession` cmdlet to reconnect the sessions.</span></span> <span data-ttu-id="8f0da-138">출력은 백업 세션이 다시 연결되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-138">The output shows that the Backups session was reconnected.</span></span> <span data-ttu-id="8f0da-139">세션 **상태가** 열리고 **가용성** 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-139">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="8f0da-140">연결이 끊어지지 않은 세션에서 cmdlet을 사용 하는 경우이 `Connect-PSSession` 명령은 세션에 영향을 주지 않으며 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-140">If you use the `Connect-PSSession` cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="8f0da-141">예 3: 엔터프라이즈 시나리오의 일련의 명령</span><span class="sxs-lookup"><span data-stu-id="8f0da-141">Example 3: Series of commands in an enterprise scenario</span></span>

<span data-ttu-id="8f0da-142">이 일련의 명령은 `Connect-PSSession` 엔터프라이즈 시나리오에서 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-142">This series of commands shows how the `Connect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="8f0da-143">여기서는 시스템 관리자가 원격 컴퓨터의 세션에서 장기 실행 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-143">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span> <span data-ttu-id="8f0da-144">관리자가 작업을 시작한 후 세션에서 연결을 끊고 집으로 갑니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-144">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="8f0da-145">나중에 관리자가 가정용 컴퓨터에 로그온 하 여 작업이 완료 될 때까지 실행 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-145">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

<span data-ttu-id="8f0da-146">관리자는 원격 컴퓨터에서 세션을 만들고 세션에서 스크립트를 실행 하 여 시작 합니다. 첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 원격 컴퓨터에서 ITTask 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-146">The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 remote computer.</span></span> <span data-ttu-id="8f0da-147">**ConfigurationName** 매개 변수를 사용하여 ITTasks 세션 구성을 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="8f0da-147">The command uses the **ConfigurationName** parameter to specify the ITTasks session configuration.</span></span> <span data-ttu-id="8f0da-148">이 명령은 세션을 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-148">The command saves the sessions in the `$s` variable.</span></span>

<span data-ttu-id="8f0da-149">두 번째 명령 `Invoke-Command` cmdlet은 변수의 세션에서 백그라운드 작업을 시작 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-149">The second command `Invoke-Command` cmdlet to start a background job in the session in the `$s` variable.</span></span> <span data-ttu-id="8f0da-150">**FilePath** 매개 변수를 사용하여 백그라운드 작업에서 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-150">It uses the **FilePath** parameter to run the script in the background job.</span></span>

<span data-ttu-id="8f0da-151">세 번째 명령은 cmdlet을 사용 하 여 `Disconnect-PSSession` 변수의 세션에서 연결을 끊습니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-151">The third command uses the `Disconnect-PSSession` cmdlet to disconnect from the session in the `$s` variable.</span></span> <span data-ttu-id="8f0da-152">이 명령은 Drop 값과 함께 **OutputBufferingMode** 매개 변수를 사용 하 여 세션에 출력을 전달 하 여 스크립트가 차단 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-152">The command uses the **OutputBufferingMode** parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session.</span></span> <span data-ttu-id="8f0da-153">**IdleTimeoutSec** 매개 변수를 사용 하 여 세션 제한 시간을 15 시간으로 연장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-153">It uses the **IdleTimeoutSec** parameter to extend the session time-out to 15 hours.</span></span> <span data-ttu-id="8f0da-154">명령이 완료 되 면 관리자가 자신의 컴퓨터를 잠그고 저녁에 대해 홈으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-154">When the command is completed, the administrator locks her computer and goes home for the evening.</span></span>

<span data-ttu-id="8f0da-155">나중에 관리자가 가정용 컴퓨터를 시작 하 고, 회사 네트워크에 로그온 하 고, PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-155">Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell.</span></span> <span data-ttu-id="8f0da-156">네 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` Server01 컴퓨터의 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-156">The fourth command uses the `Get-PSSession` cmdlet to get the sessions on the Server01 computer.</span></span> <span data-ttu-id="8f0da-157">이 명령은 ITTask 세션을 찾습니다. 다섯 번째 명령은 cmdlet을 사용 하 여 `Connect-PSSession` ITTask 세션에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-157">The command finds the ITTask session.The fifth command uses the `Connect-PSSession` cmdlet to connect to the ITTask session.</span></span> <span data-ttu-id="8f0da-158">이 명령은 세션을 `$s` 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-158">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="8f0da-159">여섯 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Job` 변수의 세션에서 명령을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-159">The sixth command uses the `Invoke-Command` cmdlet to run a `Get-Job` command in the session in the `$s` variable.</span></span> <span data-ttu-id="8f0da-160">출력은 작업이 성공적으로 완료 되었음을 보여 줍니다. 일곱 번째 명령은 cmdlet을 사용 하 여 세션에서 `Invoke-Command` `Receive-Job` 변수의 명령을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-160">The output shows that the job finished successfully.The seventh command uses the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session in the `$s` variable in the session.</span></span> <span data-ttu-id="8f0da-161">이 명령은 결과를 `$BackupSpecs` 변수에 저장 합니다. 여덟 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` 세션에서 다른 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-161">The command saves the results in the `$BackupSpecs` variable.The eighth command uses the `Invoke-Command` cmdlet to runs another script in the session.</span></span> <span data-ttu-id="8f0da-162">이 명령은 `$BackupSpecs` 세션의 변수 값을 스크립트에 대 한 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-162">The command uses the value of the `$BackupSpecs` variable in the session as input to the script.</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="8f0da-163">아홉 번째 명령은 변수의 세션에서 연결을 끊습니다 `$s` . 관리자가 PowerShell을 닫고 컴퓨터를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-163">The ninth command disconnects from the session in the `$s` variable.The administrator closes PowerShell and closes the computer.</span></span> <span data-ttu-id="8f0da-164">관리자는 다음 날 세션에 다시 연결하고 회사 컴퓨터에서 스크립트 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-164">She can reconnect to the session on the next day and check the script status from her work computer.</span></span>

## <span data-ttu-id="8f0da-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8f0da-165">PARAMETERS</span></span>

### <span data-ttu-id="8f0da-166">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="8f0da-166">-AllowRedirection</span></span>

<span data-ttu-id="8f0da-167">이 cmdlet이이 연결을 대체 URI로 리디렉션할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-167">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="8f0da-168">**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-168">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="8f0da-169">기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-169">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="8f0da-170">또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-170">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="8f0da-171">Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 **$PSSessionOption** 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-171">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="8f0da-172">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-172">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-173">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="8f0da-173">-ApplicationName</span></span>

<span data-ttu-id="8f0da-174">애플리케이션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-174">Specifies the name of an application.</span></span> <span data-ttu-id="8f0da-175">이 cmdlet은 지정 된 응용 프로그램을 사용 하는 세션에만 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-175">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="8f0da-176">연결 URI의 애플리케이션 이름 세그먼트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-176">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="8f0da-177">예를 들어, 다음 연결 URI에서 응용 프로그램 이름은 WSMan입니다 `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-177">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="8f0da-178">세션의 응용 프로그램 이름은 세션의 **Runspace.ConnectionInfo.AppName** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-178">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="8f0da-179">이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-179">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="8f0da-180">세션에서 사용하는 애플리케이션을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-180">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-181">-인증</span><span class="sxs-lookup"><span data-stu-id="8f0da-181">-Authentication</span></span>

<span data-ttu-id="8f0da-182">연결이 끊어진 세션에 다시 연결 하기 위해 명령에서 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-182">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="8f0da-183">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-183">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8f0da-184">기본값</span><span class="sxs-lookup"><span data-stu-id="8f0da-184">Default</span></span>
- <span data-ttu-id="8f0da-185">Basic</span><span class="sxs-lookup"><span data-stu-id="8f0da-185">Basic</span></span>
- <span data-ttu-id="8f0da-186">Credssp</span><span class="sxs-lookup"><span data-stu-id="8f0da-186">Credssp</span></span>
- <span data-ttu-id="8f0da-187">다이제스트</span><span class="sxs-lookup"><span data-stu-id="8f0da-187">Digest</span></span>
- <span data-ttu-id="8f0da-188">Kerberos</span><span class="sxs-lookup"><span data-stu-id="8f0da-188">Kerberos</span></span>
- <span data-ttu-id="8f0da-189">Negotiate</span><span class="sxs-lookup"><span data-stu-id="8f0da-189">Negotiate</span></span>
- <span data-ttu-id="8f0da-190">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="8f0da-190">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="8f0da-191">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-191">The default value is Default.</span></span>

<span data-ttu-id="8f0da-192">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-192">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="8f0da-193">사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-193">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="8f0da-194">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-194">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="8f0da-195">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-195">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-196">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="8f0da-196">-CertificateThumbprint</span></span>

<span data-ttu-id="8f0da-197">연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-197">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="8f0da-198">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-198">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="8f0da-199">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-199">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="8f0da-200">로컬 사용자 계정에만 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-200">They can be mapped only to local user accounts.</span></span> <span data-ttu-id="8f0da-201">도메인 계정에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-201">They do not work with domain accounts.</span></span>

<span data-ttu-id="8f0da-202">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-202">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8f0da-203">-ComputerName</span></span>

<span data-ttu-id="8f0da-204">연결이 끊긴 세션을 저장할 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-204">Specifies the computers on which the disconnected sessions are stored.</span></span> <span data-ttu-id="8f0da-205">세션은 연결의 서버 쪽 또는 수신 끝에 있는 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-205">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="8f0da-206">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-206">The default is the local computer.</span></span>

<span data-ttu-id="8f0da-207">한 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-207">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span> <span data-ttu-id="8f0da-208">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-208">Wildcard characters are not permitted.</span></span> <span data-ttu-id="8f0da-209">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-209">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-210">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="8f0da-210">-ConfigurationName</span></span>

<span data-ttu-id="8f0da-211">지정한 세션 구성을 사용하는 세션에만 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-211">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="8f0da-212">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-212">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="8f0da-213">구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-213">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="8f0da-214">세션의 구성 이름은 세션의 **ConfigurationName** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-214">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="8f0da-215">이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-215">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="8f0da-216">세션에서 사용하는 세션 구성을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-216">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="8f0da-217">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-217">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-218">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8f0da-218">-ConnectionUri</span></span>

<span data-ttu-id="8f0da-219">연결이 끊어진 세션에 대 한 연결 끝점의 Uri를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-219">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="8f0da-220">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-220">The URI must be fully qualified.</span></span> <span data-ttu-id="8f0da-221">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-221">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="8f0da-222">기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-222">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="8f0da-223">연결 URI를 지정 하지 않으면 **UseSSL** 및 **Port** 매개 변수를 사용 하 여 연결 uri 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-223">If you do not specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="8f0da-224">URI의 **Transport** 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-224">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="8f0da-225">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-225">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="8f0da-226">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-226">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="8f0da-227">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-227">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-228">-Credential</span><span class="sxs-lookup"><span data-stu-id="8f0da-228">-Credential</span></span>

<span data-ttu-id="8f0da-229">연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-229">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="8f0da-230">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-230">The default is the current user.</span></span>

<span data-ttu-id="8f0da-231">또는와 같은 사용자 이름을 입력 `User01` `Domain01\User01` 하거나 `PSCredential` cmdlet에 의해 생성 된 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-231">Type a user name, such as `User01` or `Domain01\User01`, or enter a `PSCredential` object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8f0da-232">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-232">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="8f0da-233">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-233">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8f0da-234">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="8f0da-234">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-235">-Id</span><span class="sxs-lookup"><span data-stu-id="8f0da-235">-Id</span></span>

<span data-ttu-id="8f0da-236">연결이 끊긴 세션의 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-236">Specifies the IDs of the disconnected sessions.</span></span> <span data-ttu-id="8f0da-237">**Id** 매개 변수는 연결이 끊어진 세션이 이전에 현재 세션에 연결 된 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-237">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="8f0da-238">이 매개 변수는 유효하지만, 세션이 로컬 컴퓨터에 저장되어 있지만 현재 세션에 연결되지 않은 경우 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-238">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-239">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="8f0da-239">-InstanceId</span></span>

<span data-ttu-id="8f0da-240">연결이 끊긴 세션의 인스턴스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-240">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="8f0da-241">인스턴스 ID는 로컬 또는 원격 컴퓨터의 **PSSession** 을 고유 하 게 식별 하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-241">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="8f0da-242">인스턴스 ID는 **PSSession** 의 **InstanceID** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-242">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-243">-Name</span><span class="sxs-lookup"><span data-stu-id="8f0da-243">-Name</span></span>

<span data-ttu-id="8f0da-244">연결이 끊긴 세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-244">Specifies the friendly names of the disconnected sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-245">-Port</span><span class="sxs-lookup"><span data-stu-id="8f0da-245">-Port</span></span>

<span data-ttu-id="8f0da-246">세션에 다시 연결하는 데 사용할 원격 컴퓨터의 네트워크 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-246">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span> <span data-ttu-id="8f0da-247">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-247">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="8f0da-248">기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-248">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="8f0da-249">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-249">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="8f0da-250">수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-250">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="8f0da-251">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-251">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="8f0da-252">이 명령에 설정된 포트는 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-252">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="8f0da-253">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-253">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-254">-Session</span><span class="sxs-lookup"><span data-stu-id="8f0da-254">-Session</span></span>

<span data-ttu-id="8f0da-255">연결이 끊긴 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-255">Specifies the disconnected sessions.</span></span> <span data-ttu-id="8f0da-256">**Pssession** 개체를 포함 하는 변수를 입력 하거나 **pssession** 개체를 만들거나 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-256">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-257">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="8f0da-257">-SessionOption</span></span>

<span data-ttu-id="8f0da-258">세션에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-258">Specifies advanced options for the session.</span></span> <span data-ttu-id="8f0da-259">Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-259">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="8f0da-260">옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-260">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="8f0da-261">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-261">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="8f0da-262">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-262">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="8f0da-263">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-263">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="8f0da-264">기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="8f0da-264">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="8f0da-265">**$PSSessionOption** 기본 설정 변수에 대 한 자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-265">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="8f0da-266">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-266">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-267">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="8f0da-267">-ThrottleLimit</span></span>

<span data-ttu-id="8f0da-268">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-268">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="8f0da-269">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-269">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="8f0da-270">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-270">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-271">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="8f0da-271">-UseSSL</span></span>

<span data-ttu-id="8f0da-272">이 cmdlet은 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 연결이 끊어진 세션에 연결 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-272">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="8f0da-273">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-273">By default, SSL is not used.</span></span>

<span data-ttu-id="8f0da-274">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-274">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="8f0da-275">**UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-275">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="8f0da-276">이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-276">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f0da-277">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8f0da-277">-Confirm</span></span>

<span data-ttu-id="8f0da-278">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-278">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8f0da-279">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8f0da-279">-WhatIf</span></span>

<span data-ttu-id="8f0da-280">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-280">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8f0da-281">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-281">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8f0da-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8f0da-282">CommonParameters</span></span>

<span data-ttu-id="8f0da-283">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8f0da-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8f0da-284">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8f0da-285">입력</span><span class="sxs-lookup"><span data-stu-id="8f0da-285">INPUTS</span></span>

### <span data-ttu-id="8f0da-286">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-286">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="8f0da-287">세션 (**PSSession**)을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-287">You can pipe a session (**PSSession**) to this cmdlet.</span></span>

## <span data-ttu-id="8f0da-288">출력</span><span class="sxs-lookup"><span data-stu-id="8f0da-288">OUTPUTS</span></span>

### <span data-ttu-id="8f0da-289">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-289">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="8f0da-290">이 cmdlet은 다시 연결 된 세션을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-290">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="8f0da-291">참고</span><span class="sxs-lookup"><span data-stu-id="8f0da-291">NOTES</span></span>

- <span data-ttu-id="8f0da-292">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-292">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="8f0da-293">`Connect-PSSession` 는 연결이 끊어진 세션, 즉 **상태** 속성의 값이 disconnected 인 세션에만 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-293">`Connect-PSSession` reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="8f0da-294">Windows PowerShell 3.0 이상 버전을 실행 하는 컴퓨터에 연결 되었거나 종료 된 세션만 연결을 끊고 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-294">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

- <span data-ttu-id="8f0da-295">연결이 끊어지지 않은 세션에서를 사용 하는 경우이 `Connect-PSSession` 명령은 세션에 영향을 주지 않으며 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-295">If you use `Connect-PSSession` on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>

- <span data-ttu-id="8f0da-296">**EnableNetworkAccess** 매개 변수를 사용 하 여 만든 대화형 토큰을 사용 하 여 연결 되지 않은 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-296">Disconnected loopback sessions with interactive tokens, which are created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="8f0da-297">이 제한은 악의적인 액세스로부터 컴퓨터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-297">This restriction protects the computer from malicious access.</span></span>

- <span data-ttu-id="8f0da-298">**PSSession** 의 **State** 속성 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-298">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="8f0da-299">따라서 **연결 끊김** 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-299">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="8f0da-300">그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-300">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="8f0da-301">다른 세션에 연결되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-301">It might be connected to a different session.</span></span> <span data-ttu-id="8f0da-302">세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-302">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="8f0da-303">**가용성** 값 None은 세션에 연결할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-303">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="8f0da-304">사용 중 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-304">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="8f0da-305">세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState 열거형](/dotnet/api/system.management.automation.runspaces.runspacestate)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-305">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="8f0da-306">세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability 열거형](/dotnet/api/system.management.automation.runspaces.runspaceavailability)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0da-306">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

- <span data-ttu-id="8f0da-307">**Pssession** 에 연결할 때 **pssession** 의 유휴 시간 제한 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-307">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="8f0da-308">의 **sessionoption** 매개 변수는 `Connect-PSSession` **IdleTimeout** 값을 포함 하는 **sessionoption** 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-308">The **SessionOption** parameter of `Connect-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="8f0da-309">그러나 PSSession에 연결 하는 경우 **Sessionoption** 개체의 **idletimeout** 값과 해당 변수의 **idletimeout** 값은 `$PSSessionOption` 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-309">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="8f0da-310">또는 cmdlet을 사용 하 고 pssession에서 연결을 끊으면 pssession **을 만들 때 pssession** 의 유휴 시간 제한 시간을 설정 하 고 변경할 수 있습니다 `New-PSSession` `Invoke-Command` . </span><span class="sxs-lookup"><span data-stu-id="8f0da-310">You can set and change the idle time-out of a **PSSession** when you create the **PSSession**, by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="8f0da-311">**PSSession** 의 **IdleTimeout** 속성은 연결이 끊어진 세션이 원격 컴퓨터에서 유지 되는 기간을 결정 하기 때문에 연결이 끊어진 세션에 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-311">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="8f0da-312">연결이 끊긴 세션은 연결이 끊긴 세션에서 명령을 실행 중인 경우에도 연결이 끊긴 순간부터 유휴 상태로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0da-312">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="8f0da-313">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8f0da-313">RELATED LINKS</span></span>

[<span data-ttu-id="8f0da-314">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-314">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="8f0da-315">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-315">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="8f0da-316">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-316">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="8f0da-317">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-317">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="8f0da-318">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f0da-318">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="8f0da-319">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-319">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="8f0da-320">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="8f0da-320">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="8f0da-321">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="8f0da-321">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="8f0da-322">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-322">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="8f0da-323">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f0da-323">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="8f0da-324">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f0da-324">Remove-PSSession</span></span>](Remove-PSSession.md)
