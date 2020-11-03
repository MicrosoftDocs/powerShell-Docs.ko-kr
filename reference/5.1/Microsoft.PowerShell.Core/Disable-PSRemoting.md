---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212105"
---
# <span data-ttu-id="b415c-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="b415c-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="b415c-104">개요</span><span class="sxs-lookup"><span data-stu-id="b415c-104">SYNOPSIS</span></span>
<span data-ttu-id="b415c-105">PowerShell 끝점이 원격 연결을 받지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="b415c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b415c-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b415c-107">설명</span><span class="sxs-lookup"><span data-stu-id="b415c-107">DESCRIPTION</span></span>

<span data-ttu-id="b415c-108">`Disable-PSRemoting`Cmdlet은 로컬 컴퓨터의 모든 Windows PowerShell 세션 끝점 구성에 대 한 원격 액세스를 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-108">The `Disable-PSRemoting` cmdlet blocks remote access to all Windows PowerShell session endpoint configurations on the local computer.</span></span> <span data-ttu-id="b415c-109">여기에는 PowerShell 6 이상에서 만든 모든 끝점이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-109">This includes any endpoints created by PowerShell 6 or higher.</span></span>

<span data-ttu-id="b415c-110">모든 세션 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-110">To re-enable remote access to all session configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="b415c-111">여기에는 PowerShell 6 이상에서 만든 모든 끝점이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-111">This includes any endpoints created by PowerShell 6 or higher.</span></span> <span data-ttu-id="b415c-112">선택한 세션 구성에 대 한 원격 액세스를 사용 하도록 설정 하려면 cmdlet의 **Accessmode** 매개 변수를 사용 합니다 `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="b415c-112">To enable remote access to selected session configurations, use the **AccessMode** parameter of the `Set-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="b415c-113">`Enable-PSSessionConfiguration`및 cmdlet을 사용 하 여 `Disable-PSSessionConfiguration` 모든 사용자에 대 한 세션 구성을 사용 하거나 사용 하지 않도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-113">You can also use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets to enable and disable session configurations for all users.</span></span> <span data-ttu-id="b415c-114">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b415c-114">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b415c-115">실행 후 `Disable-PSRemoting` 에도 로컬 컴퓨터에서 루프백 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-115">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="b415c-116">루프백 연결은 동일한 로컬 컴퓨터에서 시작 하 여 연결 하는 PowerShell 원격 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-116">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="b415c-117">외부 원본의 원격 세션은 차단 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-117">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="b415c-118">루프백 연결의 경우 **EnableNetworkAccess** 매개 변수를 따라 암시적 자격 증명을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-118">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="b415c-119">루프백 연결에 대 한 자세한 내용은 [새 PSSession](New-PSSession.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b415c-119">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="b415c-120">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-120">To run this cmdlet, start Windows PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="b415c-121">예제</span><span class="sxs-lookup"><span data-stu-id="b415c-121">EXAMPLES</span></span>

### <span data-ttu-id="b415c-122">예 1: 모든 세션 구성에 대 한 원격 액세스 방지</span><span class="sxs-lookup"><span data-stu-id="b415c-122">Example 1: Prevent remote access to all session configurations</span></span>

<span data-ttu-id="b415c-123">이 예제에서는 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-123">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="b415c-124">예 2: 확인 메시지 없이 모든 세션 구성에 대 한 원격 액세스 방지</span><span class="sxs-lookup"><span data-stu-id="b415c-124">Example 2: Prevent remote access to all session configurations without confirmation prompt</span></span>

<span data-ttu-id="b415c-125">이 예제에서는 메시지를 표시 하지 않고 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-125">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="b415c-126">예 3:이 cmdlet을 실행 한 결과</span><span class="sxs-lookup"><span data-stu-id="b415c-126">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="b415c-127">이 예에서는 cmdlet을 사용 하는 경우의 결과를 보여 줍니다 `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="b415c-127">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="b415c-128">이 명령 시퀀스를 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-128">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="b415c-129">세션 구성을 사용 하지 않도록 설정 하면 `New-PSSession` cmdlet이 로컬 컴퓨터 ("루프백"이 라고도 함)에 대 한 원격 세션을 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-129">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="b415c-130">로컬 컴퓨터에서 원격 액세스를 사용할 수 없으므로 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-130">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### <span data-ttu-id="b415c-131">예제 4:이 cmdlet을 실행 한 결과 및 Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="b415c-131">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="b415c-132">이 예에서는 및 cmdlet을 사용 하는의 세션 구성에 미치는 영향을 보여 줍니다 `Disable-PSRemoting` `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="b415c-132">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="b415c-133">`Disable-PSRemoting` 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-133">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="b415c-134">**Force** 매개 변수는 모든 사용자 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-134">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="b415c-135">`Get-PSSessionConfiguration`및 `Format-Table` cmdlet은 컴퓨터에 세션 구성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-135">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="b415c-136">출력은 네트워크 토큰이 있는 모든 원격 사용자가 끝점 구성에 대 한 액세스를 거부 한다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-136">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="b415c-137">로컬 컴퓨터의 Administrators 그룹은 로컬로 (루프백이 라고도 함) 연결 되 고 암시적 자격 증명을 사용 하는 동안 끝점 구성에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-137">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="b415c-138">`Enable-PSRemoting`Cmdlet은 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-138">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="b415c-139">**Force** 매개 변수는 모든 사용자 프롬프트를 표시 하지 않고 WinRM 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-139">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="b415c-140">새 출력은 **Accessdenied** 된 보안 설명자가 모든 세션 구성에서 제거 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-140">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="b415c-141">예 5: 비활성화 된 세션 끝점 구성을 사용 하는 루프백 연결</span><span class="sxs-lookup"><span data-stu-id="b415c-141">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="b415c-142">이 예제에서는 끝점 구성을 사용 하지 않도록 설정 하는 방법을 보여 주고 사용 하지 않는 끝점에 대 한 루프백 연결을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-142">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="b415c-143">`Disable-PSRemoting` 모든 PowerShell 세션 끝점 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-143">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="b415c-144">을 처음 사용 하는 경우 `New-PSSession` 로컬 컴퓨터에 대 한 원격 세션을 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-144">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="b415c-145">이 유형의 연결은 네트워크 스택을 통과 하며 루프백이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-145">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="b415c-146">따라서 **액세스 거부** 오류가 발생 하 여 비활성화 된 끝점에 대 한 연결 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-146">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="b415c-147">두 번째를 사용 하는 경우에 `New-PSSession` 도 로컬 컴퓨터에 대 한 원격 세션을 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-147">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="b415c-148">이 경우 네트워크 스택을 우회 하는 루프백 연결 이기 때문에 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-148">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="b415c-149">다음 조건이 충족 되 면 루프백 연결이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-149">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="b415c-150">연결할 컴퓨터 이름은 ' localhost '입니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-150">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="b415c-151">자격 증명은 전달 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-151">No credentials are passed in.</span></span> <span data-ttu-id="b415c-152">현재 로그인 한 사용자 (암시적 자격 증명)가 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-152">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="b415c-153">**EnableNetworkAccess** 스위치 매개 변수가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-153">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="b415c-154">루프백 연결에 대 한 자세한 내용은 [새 PSSession](New-PSSession.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b415c-154">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="b415c-155">예제 6: 사용자 지정 보안 설명자가 있는 세션 구성에 대 한 원격 액세스 방지</span><span class="sxs-lookup"><span data-stu-id="b415c-155">Example 6: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="b415c-156">이 예제에서는 cmdlet이 `Disable-PSRemoting` 사용자 지정 보안 설명자를 사용 하 여 세션 구성을 포함 하는 모든 세션 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 합니다</span><span class="sxs-lookup"><span data-stu-id="b415c-156">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="b415c-157">`Register-PSSessionConfiguration`**테스트** 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-157">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="b415c-158">**FilePath** 매개 변수는 세션을 사용자 지정 하는 세션 구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-158">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="b415c-159">**ShowSecurityDescriptorUI** 매개 변수는 세션 구성에 대 한 사용 권한을 설정 하는 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-159">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="b415c-160">권한 대화 상자에서 표시 된 사용자에 대 한 사용자 지정 전체 액세스 권한을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-160">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="b415c-161">`Get-PSSessionConfiguration`및 `Format-Table` cmdlet은 세션 구성과 해당 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-161">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="b415c-162">출력은 **테스트** 세션 구성에서 표시 된 사용자에 대 한 대화형 액세스 및 특별 한 사용 권한을 허용 한다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-162">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="b415c-163">`Disable-PSRemoting` 모든 세션 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-163">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="b415c-164">이제 `Get-PSSessionConfiguration` 및 `Format-Table` cmdlet은 모든 네트워크 사용자에 대 한 **accessdenied** 보안 설명자가 **테스트** 세션 구성을 비롯 한 모든 세션 구성에 추가 됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-164">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="b415c-165">다른 보안 설명자는 변경 되지 않지만 "network_deny_all" 보안 설명자가 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-165">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="b415c-166">이는를 사용 하 여 `New-PSSession` **테스트** 세션 구성에 연결 하려고 할 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-166">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="b415c-167">예 7: 선택한 세션 구성에 대 한 원격 액세스 다시 설정</span><span class="sxs-lookup"><span data-stu-id="b415c-167">Example 7: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="b415c-168">이 예제에서는 선택한 세션 구성에 대해서만 원격 액세스를 사용하도록 다시 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-168">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="b415c-169">모든 세션 구성을 사용 하지 않도록 설정한 후 특정 세션을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-169">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="b415c-170">`Set-PSSessionConfiguration`이 cmdlet은 microsoft를 변경 하는 데 사용 됩니다 **. ServerManager** 세션 구성.</span><span class="sxs-lookup"><span data-stu-id="b415c-170">The `Set-PSSessionConfiguration` cmdlet is used to change the **microsoft.ServerManager** session configuration.</span></span> <span data-ttu-id="b415c-171">값이 **remote** 인 **accessmode** 매개 변수는 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-171">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

## <span data-ttu-id="b415c-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b415c-172">PARAMETERS</span></span>

### <span data-ttu-id="b415c-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b415c-173">-Confirm</span></span>

<span data-ttu-id="b415c-174">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-174">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b415c-175">-Force</span><span class="sxs-lookup"><span data-stu-id="b415c-175">-Force</span></span>
<span data-ttu-id="b415c-176">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-176">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b415c-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b415c-177">-WhatIf</span></span>

<span data-ttu-id="b415c-178">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b415c-179">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b415c-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b415c-180">CommonParameters</span></span>

<span data-ttu-id="b415c-181">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b415c-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b415c-182">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b415c-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b415c-183">입력</span><span class="sxs-lookup"><span data-stu-id="b415c-183">INPUTS</span></span>

### <span data-ttu-id="b415c-184">없음</span><span class="sxs-lookup"><span data-stu-id="b415c-184">None</span></span>

<span data-ttu-id="b415c-185">개체를이 cmdlet으로 파이프 할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-185">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="b415c-186">출력</span><span class="sxs-lookup"><span data-stu-id="b415c-186">OUTPUTS</span></span>

### <span data-ttu-id="b415c-187">없음</span><span class="sxs-lookup"><span data-stu-id="b415c-187">None</span></span>

<span data-ttu-id="b415c-188">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-188">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b415c-189">참고</span><span class="sxs-lookup"><span data-stu-id="b415c-189">NOTES</span></span>

- <span data-ttu-id="b415c-190">세션 구성을 사용 하지 않도록 설정 해도 또는 cmdlet에서 수행한 모든 변경 내용은 실행 취소 되지 않습니다 `Enable-PSRemoting` `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="b415c-190">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="b415c-191">다음 변경 작업을 수동으로 실행 취소해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-191">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="b415c-192">WinRM 서비스를 중지하고 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-192">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="b415c-193">모든 IP 주소에서 요청을 수락하는 수신기를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-193">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="b415c-194">WS-Management 통신에 대해 방화벽 예외를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-194">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="b415c-195">LocalAccountTokenFilterPolicy 값을 0으로 복원하여 컴퓨터에서 Administrators 그룹의 구성원에 대한 원격 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-195">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

  <span data-ttu-id="b415c-196">세션 구성은 세션에 대한 환경을 정의하는 설정 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-196">A session configuration is a group of settings that define the environment for a session.</span></span> <span data-ttu-id="b415c-197">컴퓨터에 연결되는 모든 세션은 컴퓨터에 등록된 세션 구성 중 하나를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-197">Every session that connects to the computer must use one of the session configurations that are registered on the computer.</span></span> <span data-ttu-id="b415c-198">모든 세션 구성에 대한 원격 액세스를 거부하면 원격 사용자가 컴퓨터에 연결되는 세션을 설정하는 것을 효과적으로 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-198">By denying remote access to all session configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

  <span data-ttu-id="b415c-199">Windows PowerShell 2.0에서는 `Disable-PSRemoting` 모든 세션 구성의 보안 설명자에 Deny_All 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-199">In Windows PowerShell 2.0, `Disable-PSRemoting` adds a Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="b415c-200">이 설정은 모든 사용자가 로컬 컴퓨터에 사용자 관리 세션을 만들 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-200">This setting prevents all users from creating user-managed sessions to the local computer.</span></span> <span data-ttu-id="b415c-201">Windows PowerShell 3.0에서는 `Disable-PSRemoting` 모든 세션 구성의 보안 설명자에 Network_Deny_All 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-201">In Windows PowerShell 3.0, `Disable-PSRemoting` adds a Network_Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="b415c-202">이 설정은 다른 컴퓨터의 사용자가 로컬 컴퓨터에서 사용자 관리 세션을 만들 수 없도록 하지만 로컬 컴퓨터의 사용자가 사용자 관리 루프백 세션을 만들 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b415c-202">This setting prevents users on other computers from creating user-managed sessions on the local computer, but allows users of the local computer to create user-managed loopback sessions.</span></span>

  <span data-ttu-id="b415c-203">Windows PowerShell 2.0에서는와 `Disable-PSRemoting` 동일 합니다 `Disable-PSSessionConfiguration -Name *` .</span><span class="sxs-lookup"><span data-stu-id="b415c-203">In Windows PowerShell 2.0, `Disable-PSRemoting` is the equivalent of `Disable-PSSessionConfiguration -Name *`.</span></span> <span data-ttu-id="b415c-204">Windows PowerShell 3.0 이상 릴리스에서는 다음에 `Disable-PSRemoting` 해당 합니다. `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span><span class="sxs-lookup"><span data-stu-id="b415c-204">In Windows PowerShell 3.0 and later releases, `Disable-PSRemoting` is the equivalent of `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span></span>

## <span data-ttu-id="b415c-205">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b415c-205">RELATED LINKS</span></span>

[<span data-ttu-id="b415c-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b415c-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="b415c-207">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="b415c-207">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="b415c-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b415c-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="b415c-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b415c-209">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b415c-210">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b415c-210">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="b415c-211">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b415c-211">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="b415c-212">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b415c-212">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="b415c-213">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="b415c-213">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
