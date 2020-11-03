---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: 7694154c4724bef35aeb1ccdc46aee6a1875cf57
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218225"
---
# <span data-ttu-id="e80e6-103">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-103">Disconnect-PSSession</span></span>

## <span data-ttu-id="e80e6-104">개요</span><span class="sxs-lookup"><span data-stu-id="e80e6-104">SYNOPSIS</span></span>
<span data-ttu-id="e80e6-105">세션에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-105">Disconnects from a session.</span></span>

## <span data-ttu-id="e80e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e80e6-106">SYNTAX</span></span>

### <span data-ttu-id="e80e6-107">세션(기본값)</span><span class="sxs-lookup"><span data-stu-id="e80e6-107">Session (Default)</span></span>

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e80e6-108">속성</span><span class="sxs-lookup"><span data-stu-id="e80e6-108">Name</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e80e6-109">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e80e6-109">InstanceId</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e80e6-110">Id</span><span class="sxs-lookup"><span data-stu-id="e80e6-110">Id</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e80e6-111">설명</span><span class="sxs-lookup"><span data-stu-id="e80e6-111">DESCRIPTION</span></span>

<span data-ttu-id="e80e6-112">`Disconnect-PSSession`Cmdlet은 `New-PSSession` 현재 세션에서 cmdlet을 사용 하 여 시작한 것과 같은 PowerShell 세션 ("PSSession")의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-112">The `Disconnect-PSSession` cmdlet disconnects a PowerShell session ("PSSession"), such as one started by using the `New-PSSession` cmdlet, from the current session.</span></span> <span data-ttu-id="e80e6-113">그 결과로 PSSession은 연결이 끊긴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-113">As a result, the PSSession is in a disconnected state.</span></span> <span data-ttu-id="e80e6-114">현재 세션 또는 로컬 컴퓨터의 다른 세션이나 다른 컴퓨터에서 연결이 끊긴 PSSession에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-114">You can connect to the disconnected PSSession from the current session or from another session on the local computer or a different computer.</span></span>

<span data-ttu-id="e80e6-115">`Disconnect-PSSession`Cmdlet은 현재 세션에 연결 된 오픈 pssession만 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-115">The `Disconnect-PSSession` cmdlet disconnects only open PSSessions that are connected to the current session.</span></span> <span data-ttu-id="e80e6-116">`Disconnect-PSSession` cmdlet을 사용 하 여 시작 된 끊어진 PSSessions 또는 대화형 pssession의 연결을 끊을 수 없으며 `Enter-PSSession` , 다른 세션에 연결 된 pssession의 연결을 끊을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-116">`Disconnect-PSSession` cannot disconnect broken or closed PSSessions, or interactive PSSessions started by using the `Enter-PSSession` cmdlet, and it cannot disconnect PSSessions that are connected to other sessions.</span></span>

<span data-ttu-id="e80e6-117">연결이 끊어진 PSSession에 다시 연결 하려면 `Connect-PSSession` 또는 cmdlet을 사용 `Receive-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-117">To reconnect to a disconnected PSSession, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span>

<span data-ttu-id="e80e6-118">PSSession이 시간 초과되었거나 출력 버퍼가 가득 차서 PSSession의 명령이 차단된 경우가 아니면 PSSession의 연결이 끊겨도 PSSession의 명령은 완료될 때까지 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-118">When a PSSession is disconnected, the commands in the PSSession continue to run until they complete, unless the PSSession times out or the commands in the PSSession are blocked by a full output buffer.</span></span> <span data-ttu-id="e80e6-119">유휴 시간 제한을 변경하려면 **IdleTimeoutSec** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-119">To change the idle timeout, use the **IdleTimeoutSec** parameter.</span></span> <span data-ttu-id="e80e6-120">출력 버퍼링 모드를 변경 하려면 **OutputBufferingMode** 매개 변수를 사용 합니다. 또한 Cmdlet의 **InDisconnectedSession** 매개 변수를 사용 하 여 연결 되지 않은 `Invoke-Command` 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-120">To change the output buffering mode, use the **OutputBufferingMode** parameter You can also use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet to run a command in a disconnected session.</span></span>

<span data-ttu-id="e80e6-121">연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e80e6-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="e80e6-122">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-122">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="e80e6-123">예제</span><span class="sxs-lookup"><span data-stu-id="e80e6-123">EXAMPLES</span></span>

### <span data-ttu-id="e80e6-124">예 1-이름별로 세션 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="e80e6-124">Example 1 - Disconnect a session by name</span></span>

<span data-ttu-id="e80e6-125">이 명령은 현재 세션에서 Server01 컴퓨터에 있는 UpdateSession PSSession의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-125">This command disconnects the UpdateSession PSSession on the Server01 computer from the current session.</span></span> <span data-ttu-id="e80e6-126">이 명령은 **Name** 매개 변수를 사용 하 여 PSSession을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-126">The command uses the **Name** parameter to identify the PSSession.</span></span>

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="e80e6-127">출력은 연결 끊기 시도가 성공했음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-127">The output shows that the attempt to disconnect was successful.</span></span> <span data-ttu-id="e80e6-128">세션 상태가 Disconnected이고 Availability가 None이므로 세션이 사용되고 있지 않으며 다시 연결할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-128">The session state is Disconnected and the Availability is None, which indicates that the session is not busy and can be reconnected.</span></span>

### <span data-ttu-id="e80e6-129">예 2-특정 컴퓨터에서 세션 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="e80e6-129">Example 2 - Disconnect a session from a specific computer</span></span>

<span data-ttu-id="e80e6-130">이 명령은 현재 세션에서 Server12 컴퓨터에 있는 ITTask PSSession의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-130">This command disconnects the ITTask PSSession on the Server12 computer from the current session.</span></span>
<span data-ttu-id="e80e6-131">ITTask 세션은 현재 세션에서 만들어졌으며 Server12 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-131">The ITTask session was created in the current session and connects to the Server12 computer.</span></span> <span data-ttu-id="e80e6-132">이 명령은 cmdlet을 사용 하 여 세션을 가져오고 cmdlet을 사용 하 여 `Get-PSSession` `Disconnect-PSSession` 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-132">The command uses the `Get-PSSession` cmdlet to get the session and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span>

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

<span data-ttu-id="e80e6-133">이 `Disconnect-PSSession` 명령은 **OutputBufferingMode** 매개 변수를 사용 하 여 출력 모드를 **Drop** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-133">The `Disconnect-PSSession` command uses the **OutputBufferingMode** parameter to set the output mode to **Drop**.</span></span> <span data-ttu-id="e80e6-134">이 설정은 세션 출력 버퍼가 가득 차도 세션에서 실행 중인 스크립트를 계속 실행할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-134">This setting ensures that the script that is running in the session can continue to run even if the session output buffer is full.</span></span> <span data-ttu-id="e80e6-135">스크립트가 파일 공유의 보고서에 출력을 쓰기 때문에 다른 출력이 영향 없이 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-135">Because the script writes its output to a report on a file share, other output can be lost without consequence.</span></span>

<span data-ttu-id="e80e6-136">또한 이 명령은 **IdleTimeoutSec** 매개 변수를 사용하여 세션의 시간 제한을 24시간으로 연장합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-136">The command also uses the **IdleTimeoutSec** parameter to extend the idle timeout of the session to 24 hours.</span></span> <span data-ttu-id="e80e6-137">이 설정은 이 관리자나 다른 관리자가 세션에 다시 연결하여 스크립트가 실행되었는지 확인하고 필요한 경우 문제를 해결할 수 있는 시간을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-137">This setting allows time for this administrator or other administrators to reconnect to the session to verify that the script ran and troubleshoot if needed.</span></span>

### <span data-ttu-id="e80e6-138">예 3-여러 컴퓨터에서 여러 PSSessions 사용</span><span class="sxs-lookup"><span data-stu-id="e80e6-138">Example 3 - Using multiple PSSessions on multiple computers</span></span>

<span data-ttu-id="e80e6-139">이 일련의 명령은 `Disconnect-PSSession` 엔터프라이즈 시나리오에서 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-139">This series of commands shows how the `Disconnect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="e80e6-140">이 경우 새 기술자가 원격 컴퓨터의 세션에서 스크립트를 시작한 후 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-140">In this case, a new technician starts a script in a session on a remote computer and runs into a problem.</span></span> <span data-ttu-id="e80e6-141">보다 경험이 많은 관리자가 세션에 연결하여 문제를 해결할 수 있도록 기술자가 세션에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-141">The technician disconnects from the session so that a more experienced manager can connect to the session and resolve the problem.</span></span>

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

<span data-ttu-id="e80e6-142">기술자는 먼저 여러 원격 컴퓨터에서 세션을 만들고 각 세션에서 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-142">The technician begins by creating sessions on several remote computers and running a script in each session.</span></span> <span data-ttu-id="e80e6-143">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 세 개의 원격 컴퓨터에서 ITTask 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-143">The first command uses the `New-PSSession` cmdlet to create the ITTask session on three remote computers.</span></span> <span data-ttu-id="e80e6-144">이 명령은 세션을 $s 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-144">The command saves the sessions in the $s variable.</span></span> <span data-ttu-id="e80e6-145">두 번째 명령은 cmdlet의 **FilePath** 매개 변수를 사용 하 여 `Invoke-Command` $s 변수의 세션에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-145">The second command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run a script in the sessions in the $s variable.</span></span>

<span data-ttu-id="e80e6-146">Srv1 컴퓨터에서 실행되는 스크립트가 예기치 않은 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-146">The script running on the Srv1 computer generates unexpected errors.</span></span> <span data-ttu-id="e80e6-147">기술자가 관리자에게 지원을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-147">The technician contacts his manager and asks for assistance.</span></span> <span data-ttu-id="e80e6-148">관리자가 검토할 수 있도록 기술 자가 세션에서 연결을 끊도록 지시 합니다. 두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` Srv1 컴퓨터의 ITTask 세션을 가져온 다음 cmdlet을 사용 하 여 `Disconnect-PSSession` 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-148">The manager directs the technician to disconnect from the session so he can investigate.The second command uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span> <span data-ttu-id="e80e6-149">이 명령은 다른 컴퓨터의 ITTask 세션에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-149">This command does not affect the ITTask sessions on the other computers.</span></span>

<span data-ttu-id="e80e6-150">세 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` ITTask 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-150">The third command uses the `Get-PSSession` cmdlet to get the ITTask sessions.</span></span> <span data-ttu-id="e80e6-151">출력은 Srv2 및 Srv30 컴퓨터의 ITTask 세션이 연결 끊기 명령의 영향을 받지 않았음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-151">The output shows that the ITTask sessions on the Srv2 and Srv30 computers were not affected by the command to disconnect.</span></span>

<span data-ttu-id="e80e6-152">관리자는 자신의 가정용 컴퓨터에 로그온 하 고, 회사 네트워크에 연결 하 고, Windows PowerShell을 시작 하 고, cmdlet을 사용 하 여 `Get-PSSession` Srv1 컴퓨터의 ITTask 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-152">The manager logs on to his home computer, connects to his corporate network, starts Windows PowerShell, and uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="e80e6-153">기술자 자격 증명을 사용하여 세션에 액세스한</span><span class="sxs-lookup"><span data-stu-id="e80e6-153">He uses the credentials of the technician to access the session.</span></span>

<span data-ttu-id="e80e6-154">그런 다음, 관리자는 cmdlet을 사용 하 여 `Connect-PSSession` Srv1 컴퓨터의 ITTask 세션에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-154">Next, the manager uses the `Connect-PSSession` cmdlet to connect to the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="e80e6-155">이 명령은 세션을 $s 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-155">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="e80e6-156">관리자는 cmdlet을 사용 하 여 `Invoke-Command` 변수의 세션에서 일부 진단 명령을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-156">The manager uses the `Invoke-Command` cmdlet to run some diagnostic commands in the session in the `$s` variable.</span></span> <span data-ttu-id="e80e6-157">스크립트가 필요한 디렉터리를 찾지 못해 실패했음을 발견합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-157">He recognizes that the script failed because it did not find a required directory.</span></span>
<span data-ttu-id="e80e6-158">관리자는 함수를 사용 하 여 `MkDir` 디렉터리를 만든 다음 스크립트를 다시 시작 하 `Get-PatchStatus.ps1` 고 세션에서 연결을 끊습니다. 관리자는 해당 결과를 기술 지원 담당자에 게 보고 하 고, 세션에 다시 연결 하 여 작업을 완료 하 고, `Get-PatchStatus.ps1` 필요한 디렉터리가 없는 경우 해당 디렉터리를 만드는 스크립트에 명령을 추가 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-158">The manager uses the `MkDir` function to create the directory, and then he restarts the `Get-PatchStatus.ps1` script and disconnects from the session.The manager reports his findings to the technician, suggests that he reconnect to the session to complete the tasks, and asks him to add a command to the `Get-PatchStatus.ps1` script that creates the required directory if it does not exist.</span></span>

### <span data-ttu-id="e80e6-159">예 4-PSSession에 대 한 제한 시간 값 변경</span><span class="sxs-lookup"><span data-stu-id="e80e6-159">Example 4 - Change the timeout value for a PSSession</span></span>

<span data-ttu-id="e80e6-160">이 예제에서는 세션 연결을 끊을 수 있도록 세션의 **IdleTimeout** 속성 값을 수정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-160">This example shows how to correct the value of the **IdleTimeout** property of a session so that it can be disconnected.</span></span>

<span data-ttu-id="e80e6-161">세션의 유휴 시간 제한 속성은 연결이 끊긴 세션이 삭제되기 전에 유지되는 기간을 결정하므로 연결이 끊긴 세션에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-161">The idle timeout property of a session is critical to disconnected sessions, because it determines how long a disconnected session is maintained before it is deleted.</span></span> <span data-ttu-id="e80e6-162">세션을 만들 때 및 세션 연결을 끊을 때 유휴 시간 제한 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-162">You can set the idle timeout option when you create a session and when you disconnect it.</span></span> <span data-ttu-id="e80e6-163">세션의 유휴 시간 제한에 대 한 기본값은 `$PSSessionOption` 로컬 컴퓨터의 기본 설정 변수 및 원격 컴퓨터의 세션 구성에 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-163">The default values for the idle timeout of a session are set in the `$PSSessionOption` preference variable on the local computer and in the session configuration on the remote computer.</span></span> <span data-ttu-id="e80e6-164">세션에 대해 설정된 값이 세션 구성에서 설정된 값보다 우선하지만 세션 값은 세션 구성에서 설정된 할당량(예: **MaxIdleTimeoutMs** 값)을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-164">Values set for the session take precedence over values set in the session configuration, but session values cannot exceed quotas set in the session configuration, such as the **MaxIdleTimeoutMs** value.</span></span>

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

<span data-ttu-id="e80e6-165">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSessionOption` 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-165">The first command uses the `New-PSSessionOption` cmdlet to create a session option object.</span></span> <span data-ttu-id="e80e6-166">**IdleTimeout** 매개 변수를 사용하여 유휴 시간 제한을 48시간(172800000밀리초)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-166">It uses the **IdleTimeout** parameter to set an idle timeout of 48 hours (172800000 milliseconds).</span></span> <span data-ttu-id="e80e6-167">또한 세션 옵션 개체를 $Timeout 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-167">The command saves the session option object in the $Timeout variable.</span></span>

<span data-ttu-id="e80e6-168">두 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에서 ITTask 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-168">The second command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="e80e6-169">이 명령은 세션을 $s 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-169">The command save the session in the $s variable.</span></span> <span data-ttu-id="e80e6-170">**SessionOption** 매개 변수 값은 $Timeout 변수에 있는 48시간 유휴 시간 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-170">The value of the **SessionOption** parameter is the 48-hour idle timeout in the $Timeout variable.</span></span>

<span data-ttu-id="e80e6-171">세 번째 명령은 $s 변수에 있는 ITTask 세션의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-171">The third command disconnects the ITTask session in the $s variable.</span></span> <span data-ttu-id="e80e6-172">세션의 유휴 시간 제한 값이 세션 구성의 **MaxIdleTimeoutMs** 할당량을 초과하기 때문에 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-172">The command fails because the idle timeout value of the session exceeds the **MaxIdleTimeoutMs** quota in the session configuration.</span></span> <span data-ttu-id="e80e6-173">세션 연결이 끊길 때까지 유휴 시간 제한이 사용되지 않았으므로 세션이 사용 중인 동안에는 이 위반이 검색되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-173">Because the idle timeout is not used until the session is disconnected, this violation can go undetected while the session is in use.</span></span>

<span data-ttu-id="e80e6-174">네 번째 명령은 cmdlet을 사용 `Invoke-Command` 하 여 `Get-PSSessionConfiguration` Server01 컴퓨터의 Microsoft PowerShell 세션 구성에 대 한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-174">The fourth command uses the `Invoke-Command` cmdlet to run a `Get-PSSessionConfiguration` command for the Microsoft.PowerShell session configuration on the Server01 computer.</span></span> <span data-ttu-id="e80e6-175">이 명령은 cmdlet을 사용 `Format-List` 하 여 세션 구성의 모든 속성을 목록으로 표시 합니다. 출력은 세션 구성을 사용 하는 세션에 대해 허용 되는 최대 **IdleTimeout** 값을 설정 하는 **MaxIdleTimeoutMS** 속성이 4320만 밀리초 (12 시간) 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-175">The command uses the `Format-List` cmdlet to display all properties of the session configuration in a list.The output shows that the **MaxIdleTimeoutMS** property, which establishes the maximum permitted **IdleTimeout** value for sessions that use the session configuration, is 43200000 milliseconds (12 hours).</span></span>

<span data-ttu-id="e80e6-176">다섯 번째 명령은 $s 변수에 있는 세션의 세션 옵션 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-176">The fifth command gets the session option values of the session in the $s variable.</span></span> <span data-ttu-id="e80e6-177">여러 세션 옵션의 값은 세션의 **Runspace** 속성에 대 한 **ConnectionInfo** 속성의 속성입니다. 출력은 세션의 **IdleTimeout** 속성 값이 1억7280만 밀리초 (48 시간) 임을 보여 주며,이는 세션 구성에서 12 시간의 **MaxIdleTimeoutMs** 할당량을 위반 합니다. 이 충돌을 해결 하려면 **ConfigurationName** 매개 변수를 사용 하 여 다른 세션 구성을 선택 하거나 **IdleTimeout** 매개 변수를 사용 하 여 세션의 유휴 시간 제한을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-177">The values of many session options are properties of the **ConnectionInfo** property of the **Runspace** property of the session.The output shows that the value of the **IdleTimeout** property of the session is 172800000 milliseconds (48 hours), which violates the **MaxIdleTimeoutMs** quota of 12 hours in the session configuration.To resolve this conflict, you can use the **ConfigurationName** parameter to select a different session configuration or use the **IdleTimeout** parameter to reduce the idle timeout of the session.</span></span>

<span data-ttu-id="e80e6-178">여섯 번째 명령은 세션 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-178">The sixth command disconnects the session.</span></span> <span data-ttu-id="e80e6-179">**IdleTimeoutSec** 매개 변수를 사용하여 유휴 시간 제한을 최대값 12시간으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-179">It uses the **IdleTimeoutSec** parameter to set the idle timeout to the 12-hour maximum.</span></span>

<span data-ttu-id="e80e6-180">일곱 번째 명령은 연결이 끊긴 세션의 **IdleTimeout** 속성 값을 가져옵니다. 이 값은 밀리초 단위로 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-180">The seventh command gets the value of the **IdleTimeout** property of the disconnected session, which is measured in milliseconds.</span></span> <span data-ttu-id="e80e6-181">출력은 명령이 성공했음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-181">The output confirms that the command was successful.</span></span>

## <span data-ttu-id="e80e6-182">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e80e6-182">PARAMETERS</span></span>

### <span data-ttu-id="e80e6-183">-Id</span><span class="sxs-lookup"><span data-stu-id="e80e6-183">-Id</span></span>

<span data-ttu-id="e80e6-184">지정한 세션 ID를 가진 세션에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-184">Disconnects from sessions with the specified session ID.</span></span> <span data-ttu-id="e80e6-185">하나 이상의 ID를 쉼표로 구분하여 입력하거나 범위 연산자(..)를 사용하여 ID 범위를 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="e80e6-185">Type one or more IDs (separated by commas), or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="e80e6-186">세션의 ID를 가져오려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-186">To get the ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="e80e6-187">인스턴스 ID는 세션의 **ID** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-187">The instance ID is stored in the **ID** property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e80e6-188">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="e80e6-188">-IdleTimeoutSec</span></span>

<span data-ttu-id="e80e6-189">연결이 끊긴 PSSession의 유휴 시간 제한 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-189">Changes the idle timeout value of the disconnected PSSession.</span></span> <span data-ttu-id="e80e6-190">값을 초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e80e6-190">Enter a value in seconds.</span></span> <span data-ttu-id="e80e6-191">최소값은 60 (1 분)입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-191">The minimum value is 60 (1 minute).</span></span>

<span data-ttu-id="e80e6-192">유휴 시간 제한은 원격 컴퓨터에서 연결이 끊긴 PSSession을 유지 관리하는 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-192">The idle timeout determines how long the disconnected PSSession is maintained on the remote computer.</span></span> <span data-ttu-id="e80e6-193">시간 제한이 만료되면 PSSession이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-193">When the timeout expires, the PSSession is deleted.</span></span>

<span data-ttu-id="e80e6-194">연결이 끊긴 PSSession은 연결이 끊긴 세션에서 명령을 실행 중인 경우에도 연결이 끊긴 순간부터 유휴 상태로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-194">Disconnected PSSessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="e80e6-195">세션의 유휴 시간 제한에 대한 기본값은 세션 구성의 **IdleTimeoutMs** 속성 값에 의해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-195">The default value for the idle timeout of a session is set by the value of the **IdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="e80e6-196">기본값은 7200000밀리초(2시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-196">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="e80e6-197">이 매개 변수 값은 $PSSessionOption 기본 설정 변수의 **IdleTimeout** 속성 값 및 세션 구성의 기본 유휴 시간 제한 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-197">The value of this parameter takes precedence over the value of the **IdleTimeout** property of the $PSSessionOption preference variable and the default idle timeout value in the session configuration.</span></span> <span data-ttu-id="e80e6-198">그러나 세션 구성의 **MaxIdleTimeoutMs** 속성 값을 초과할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-198">However, this value cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="e80e6-199">**MaxIdleTimeoutMs** 의 기본값은 12시간(43200000밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-199">The default value of **MaxIdleTimeoutMs** is 12 hours (43200000 milliseconds).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e80e6-200">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e80e6-200">-InstanceId</span></span>

<span data-ttu-id="e80e6-201">지정한 인스턴스 ID를 가진 세션에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-201">Disconnects from sessions with the specified instance IDs.</span></span>

<span data-ttu-id="e80e6-202">인스턴스 ID는 로컬 또는 원격 컴퓨터의 세션을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-202">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="e80e6-203">인스턴스 ID는 여러 컴퓨터의 세션 간에도 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-203">The instance ID is unique, even across multiple sessions on multiple computers.</span></span>

<span data-ttu-id="e80e6-204">세션의 인스턴스 ID를 가져오려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-204">To get the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="e80e6-205">인스턴스 ID는 세션의 **InstanceID** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-205">The instance ID is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e80e6-206">-Name</span><span class="sxs-lookup"><span data-stu-id="e80e6-206">-Name</span></span>

<span data-ttu-id="e80e6-207">지정한 이름을 가진 세션에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-207">Disconnects from sessions with the specified friendly names.</span></span> <span data-ttu-id="e80e6-208">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-208">Wildcards are permitted.</span></span>

<span data-ttu-id="e80e6-209">세션의 이름을 가져오려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-209">To get the friendly name of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="e80e6-210">이름은 세션의 **Name** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-210">The friendly name is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e80e6-211">-Session</span><span class="sxs-lookup"><span data-stu-id="e80e6-211">-Session</span></span>

<span data-ttu-id="e80e6-212">지정한 PSSession에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-212">Disconnects from the specified PSSessions.</span></span> <span data-ttu-id="e80e6-213">Cmdlet에서 반환 하는 것과 같은 PSSession 개체를 입력 `New-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-213">Enter PSSession objects, such as those that the `New-PSSession` cmdlet returns.</span></span> <span data-ttu-id="e80e6-214">PSSession 개체를로 파이프 할 수도 있습니다 `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-214">You can also pipe a PSSession object to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="e80e6-215">`Get-PSSession`Cmdlet은 연결이 끊어진 pssession 및 다른 컴퓨터의 다른 세션에 연결 된 pssession을 포함 하 여 원격 컴퓨터에서 종료 되는 모든 pssession을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-215">The `Get-PSSession` cmdlet can get all PSSessions that terminate at a remote computer, including PSSessions that are disconnected and PSSessions that are connected to other sessions on other computers.</span></span> <span data-ttu-id="e80e6-216">`Disconnect-PSSession` 현재 세션에 연결 된 PSSession만 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-216">`Disconnect-PSSession` disconnects only PSSession that are connected to the current session.</span></span> <span data-ttu-id="e80e6-217">다른 pssession을에 파이프 하면 `Disconnect-PSSession` `Disconnect-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-217">If you pipe other PSSessions to `Disconnect-PSSession`, the `Disconnect-PSSession` command fails.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e80e6-218">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e80e6-218">-ThrottleLimit</span></span>

<span data-ttu-id="e80e6-219">명령에 대 한 제한 제한을 설정 합니다 `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-219">Sets the throttle limit for the `Disconnect-PSSession` command.</span></span>

<span data-ttu-id="e80e6-220">제한 한도는 이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-220">The throttle limit is the maximum number of concurrent connections that can be established to run this command.</span></span> <span data-ttu-id="e80e6-221">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-221">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="e80e6-222">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-222">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e80e6-223">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="e80e6-223">-OutputBufferingMode</span></span>

<span data-ttu-id="e80e6-224">출력 버퍼가 가득 찰 경우 연결이 끊긴 세션에서 명령 출력을 관리하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-224">Determines how command output is managed in the disconnected session when the output buffer is full.</span></span> <span data-ttu-id="e80e6-225">기본값은 **Block** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-225">The default value is **Block**.</span></span>

<span data-ttu-id="e80e6-226">연결된 세션의 명령이 출력을 반환하여 출력 버퍼가 가득 찰 경우 이 매개 변수 값에 의해 세션 연결이 끊긴 동안 명령을 계속 실행할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-226">If the command in the disconnected session is returning output and the output buffer fills, the value of this parameter effectively determines whether the command continues to run while the session is disconnected.</span></span> <span data-ttu-id="e80e6-227">값이 **Block** 이면 세션을 다시 연결할 때까지 명령이 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-227">A value of **Block** suspends the command until the session is reconnected.</span></span> <span data-ttu-id="e80e6-228">값이 **Drop** 이면 데이터가 손실될 수는 있지만 명령을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-228">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="e80e6-229">**Drop** 값을 사용할 경우 명령 출력을 디스크의 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-229">When using the **Drop** value, redirect the command output to a file on disk.</span></span>

<span data-ttu-id="e80e6-230">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-230">Valid values are:</span></span>

- <span data-ttu-id="e80e6-231">**차단** : 출력 버퍼가 가득 차면 버퍼가 명확 해질 때까지 실행이 일시 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-231">**Block** : When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="e80e6-232">**Drop** : 출력 버퍼가 가득 차면 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-232">**Drop** : When the output buffer is full, execution continues.</span></span> <span data-ttu-id="e80e6-233">새 출력이 저장되면 가장 오래된 출력을 버립니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-233">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="e80e6-234">**없음** : 출력 버퍼링 모드를 지정 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-234">**None** : No output buffering mode is specified.</span></span> <span data-ttu-id="e80e6-235">세션 구성의 **OutputBufferingMode** 속성 값을 연결이 끊긴 세션에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-235">The value of the **OutputBufferingMode** property of the session configuration is used for the disconnected session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e80e6-236">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e80e6-236">-Confirm</span></span>

<span data-ttu-id="e80e6-237">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-237">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e80e6-238">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e80e6-238">-WhatIf</span></span>

<span data-ttu-id="e80e6-239">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-239">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e80e6-240">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-240">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e80e6-241">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e80e6-241">CommonParameters</span></span>

<span data-ttu-id="e80e6-242">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e80e6-242">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e80e6-243">자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e80e6-243">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e80e6-244">입력</span><span class="sxs-lookup"><span data-stu-id="e80e6-244">INPUTS</span></span>

### <span data-ttu-id="e80e6-245">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-245">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="e80e6-246">세션을로 파이프 할 수 있습니다 `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e80e6-246">You can pipe a session to `Disconnect-PSSession`.</span></span>

## <span data-ttu-id="e80e6-247">출력</span><span class="sxs-lookup"><span data-stu-id="e80e6-247">OUTPUTS</span></span>

### <span data-ttu-id="e80e6-248">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-248">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="e80e6-249">`Disconnect-PSSession` 연결을 끊은 세션을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-249">`Disconnect-PSSession` returns an object that represents the session that it disconnected.</span></span>

## <span data-ttu-id="e80e6-250">참고</span><span class="sxs-lookup"><span data-stu-id="e80e6-250">NOTES</span></span>

- <span data-ttu-id="e80e6-251">`Disconnect-PSSession`이 cmdlet은 로컬 및 원격 컴퓨터에서 PowerShell 3.0 이상을 실행 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-251">The `Disconnect-PSSession` cmdlet works only when the local and remote computers are running PowerShell 3.0 or later.</span></span>
- <span data-ttu-id="e80e6-252">연결 되지 않은 세션에서 cmdlet을 사용 하는 경우이 `Disconnect-PSSession` 명령은 세션에 영향을 주지 않으며 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-252">If you use the `Disconnect-PSSession` cmdlet on a disconnected session, the command has no effect on the session and it does not generate errors.</span></span>
- <span data-ttu-id="e80e6-253">대화형 보안 토큰이 있는 연결이 끊긴 루프백 세션( **EnableNetworkAccess** 매개 변수로 만든 세션)은 세션을 만든 컴퓨터에서만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-253">Disconnected loopback sessions with interactive security tokens (those created with the **EnableNetworkAccess** parameter) can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="e80e6-254">이 제한은 악의적인 액세스로부터 컴퓨터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-254">This restriction protects the computer from malicious access.</span></span>
- <span data-ttu-id="e80e6-255">PSSession의 연결을 끊을 경우 세션 상태는 **Disconnected** 이고 가용성은 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-255">When you disconnect a PSSession, the session state is **Disconnected** and the availability is **None**.</span></span>

  <span data-ttu-id="e80e6-256">**State** 속성 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-256">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="e80e6-257">따라서 값 **Disconnected** 는 PSSession이 현재 세션에 연결되어 있지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-257">Therefore, a value of **Disconnected** means that the PSSession is not connected to the current session.</span></span> <span data-ttu-id="e80e6-258">그렇다고 PSSession의 연결이 모든 세션에서 끊어졌다는 것을 의미하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-258">However, it does not mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="e80e6-259">다른 세션에 연결되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-259">It might be connected to a different session.</span></span> <span data-ttu-id="e80e6-260">세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-260">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="e80e6-261">**Availability** 값이 **None** 이면 세션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-261">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="e80e6-262">값이 **Busy** 이면 PSSession이 다른 세션에 연결되어 있어서 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e80e6-262">A value of **Busy** indicates that you cannot connect to the PSSession because it is connected to another session.</span></span>

  <span data-ttu-id="e80e6-263">세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState 열거형](/dotnet/api/system.management.automation.runspaces.runspacestate)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e80e6-263">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="e80e6-264">세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability 열거형](/dotnet/api/system.management.automation.runspaces.runspaceavailability)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e80e6-264">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="e80e6-265">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e80e6-265">RELATED LINKS</span></span>

[<span data-ttu-id="e80e6-266">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-266">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="e80e6-267">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-267">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="e80e6-268">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-268">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="e80e6-269">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-269">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e80e6-270">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e80e6-270">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="e80e6-271">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-271">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e80e6-272">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="e80e6-272">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="e80e6-273">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="e80e6-273">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="e80e6-274">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-274">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="e80e6-275">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e80e6-275">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="e80e6-276">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e80e6-276">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="e80e6-277">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e80e6-277">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="e80e6-278">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e80e6-278">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="e80e6-279">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="e80e6-279">about_Remote_Disconnected_Sessions</span></span>](About/about_Remote_Disconnected_Sessions.md)
