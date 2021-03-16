---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 4410c8f41fffcaae9c9f447af246f335033d53a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600148"
---
# <span data-ttu-id="447d2-102">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="447d2-102">Disable-PSRemoting</span></span>

## <span data-ttu-id="447d2-103">개요</span><span class="sxs-lookup"><span data-stu-id="447d2-103">SYNOPSIS</span></span>
<span data-ttu-id="447d2-104">PowerShell 끝점이 원격 연결을 받지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-104">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="447d2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="447d2-105">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="447d2-106">설명</span><span class="sxs-lookup"><span data-stu-id="447d2-106">DESCRIPTION</span></span>

<span data-ttu-id="447d2-107">`Disable-PSRemoting`Cmdlet은 로컬 컴퓨터의 모든 PowerShell 버전 6 및 더 큰 세션 끝점 구성에 대 한 원격 액세스를 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-107">The `Disable-PSRemoting` cmdlet blocks remote access to all PowerShell version 6 and greater session endpoint configurations on the local computer.</span></span> <span data-ttu-id="447d2-108">Windows PowerShell 끝점 구성에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-108">It does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="447d2-109">Windows PowerShell 세션 끝점 구성을 사용 하지 않도록 설정 하려면 `Disable-PSRemoting` Windows powershell 세션 내에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-109">To disable Windows PowerShell session endpoint configurations, run `Disable-PSRemoting` command from within a Windows PowerShell session.</span></span>

<span data-ttu-id="447d2-110">모든 PowerShell 버전 6 및 더 큰 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-110">To re-enable remote access to all PowerShell version 6 and greater session endpoint configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="447d2-111">모든 Windows PowerShell 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 하려면 `Enable-PSRemoting` Windows powershell 세션 내에서를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-111">To re-enable remote access to all Windows PowerShell session endpoint configurations, run `Enable-PSRemoting` from within a Windows PowerShell session.</span></span>

> [!NOTE]
> <span data-ttu-id="447d2-112">로컬 Windows 컴퓨터에 대 한 모든 PowerShell 원격 액세스를 사용 하지 않도록 설정 하려면 PowerShell 버전 6 이상의 세션 내에서 또는 Windows PowerShell 세션 내에서이 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-112">If you want to disable all PowerShell remote access to a local Windows machine, you must run this command both from a within PowerShell version 6 or greater session and from within a Windows PowerShell session.</span></span> <span data-ttu-id="447d2-113">Windows PowerShell은 기본적으로 모든 Windows 컴퓨터에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-113">Windows PowerShell is installed on all Windows machines by default.</span></span>

<span data-ttu-id="447d2-114">특정 세션 끝점 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 하 고 다시 사용 하도록 설정 하려면 `Enable-PSSessionConfiguration` 및 cmdlet을 사용 `Disable-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-114">To disable and re-enable remote access to specific session endpoint configurations, use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="447d2-115">개별 끝점의 특정 액세스 구성을 설정 하려면 `Set-PSSessionConfiguration` **accessmode** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-115">To set specific access configurations of individual endpoints, use the `Set-PSSessionConfiguration` cmdlet along with the **AccessMode** parameter.</span></span> <span data-ttu-id="447d2-116">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="447d2-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="447d2-117">실행 후 `Disable-PSRemoting` 에도 로컬 컴퓨터에서 루프백 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-117">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="447d2-118">루프백 연결은 동일한 로컬 컴퓨터에서 시작 하 여 연결 하는 PowerShell 원격 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-118">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="447d2-119">외부 원본의 원격 세션은 차단 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-119">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="447d2-120">루프백 연결의 경우 **EnableNetworkAccess** 매개 변수를 따라 암시적 자격 증명을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-120">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="447d2-121">루프백 연결에 대 한 자세한 내용은 [새 PSSession](New-PSSession.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="447d2-121">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="447d2-122">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-122">This cmdlet is only available on the Windows platform.</span></span> <span data-ttu-id="447d2-123">Linux 또는 macOS 버전의 PowerShell에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-123">It is not available on Linux or macOS versions of PowerShell.</span></span> <span data-ttu-id="447d2-124">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-124">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="447d2-125">예제</span><span class="sxs-lookup"><span data-stu-id="447d2-125">EXAMPLES</span></span>

### <span data-ttu-id="447d2-126">예 1: 모든 PowerShell 세션 구성에 대 한 원격 액세스 방지</span><span class="sxs-lookup"><span data-stu-id="447d2-126">Example 1: Prevent remote access to all PowerShell session configurations</span></span>

<span data-ttu-id="447d2-127">이 예제에서는 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-127">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="447d2-128">예 2: 확인 메시지 없이 모든 PowerShell 세션 구성에 대 한 원격 액세스 방지</span><span class="sxs-lookup"><span data-stu-id="447d2-128">Example 2: Prevent remote access to all PowerShell session configurations without confirmation prompt</span></span>

<span data-ttu-id="447d2-129">이 예제에서는 메시지를 표시 하지 않고 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-129">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="447d2-130">예 3:이 cmdlet을 실행 한 결과</span><span class="sxs-lookup"><span data-stu-id="447d2-130">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="447d2-131">이 예에서는 cmdlet을 사용 하는 경우의 결과를 보여 줍니다 `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="447d2-131">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="447d2-132">이 명령 시퀀스를 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-132">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="447d2-133">세션 구성을 사용 하지 않도록 설정 하면 `New-PSSession` cmdlet이 로컬 컴퓨터 ("루프백"이 라고도 함)에 대 한 원격 세션을 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-133">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="447d2-134">로컬 컴퓨터에서 원격 액세스를 사용할 수 없으므로 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-134">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
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

### <span data-ttu-id="447d2-135">예제 4:이 cmdlet을 실행 한 결과 및 Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="447d2-135">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="447d2-136">이 예에서는 및 cmdlet을 사용 하는의 세션 구성에 미치는 영향을 보여 줍니다 `Disable-PSRemoting` `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="447d2-136">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="447d2-137">`Disable-PSRemoting` 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-137">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="447d2-138">**Force** 매개 변수는 모든 사용자 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-138">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="447d2-139">`Get-PSSessionConfiguration`및 `Format-Table` cmdlet은 컴퓨터에 세션 구성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-139">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="447d2-140">출력은 네트워크 토큰이 있는 모든 원격 사용자가 끝점 구성에 대 한 액세스를 거부 한다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-140">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="447d2-141">로컬 컴퓨터의 Administrators 그룹은 로컬로 (루프백이 라고도 함) 연결 되 고 암시적 자격 증명을 사용 하는 동안 끝점 구성에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-141">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

<span data-ttu-id="447d2-142">`Enable-PSRemoting`Cmdlet은 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-142">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="447d2-143">**Force** 매개 변수는 모든 사용자 프롬프트를 표시 하지 않고 WinRM 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-143">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="447d2-144">새 출력은 **Accessdenied** 된 보안 설명자가 모든 세션 구성에서 제거 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-144">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="447d2-145">예 5: 비활성화 된 세션 끝점 구성을 사용 하는 루프백 연결</span><span class="sxs-lookup"><span data-stu-id="447d2-145">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="447d2-146">이 예제에서는 끝점 구성을 사용 하지 않도록 설정 하는 방법을 보여 주고 사용 하지 않는 끝점에 대 한 루프백 연결을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-146">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="447d2-147">`Disable-PSRemoting` 모든 PowerShell 세션 끝점 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-147">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="447d2-148">을 처음 사용 하는 경우 `New-PSSession` 로컬 컴퓨터에 대 한 원격 세션을 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-148">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="447d2-149">**ConfigurationName** 매개 변수는 비활성화 된 PowerShell 끝점을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-149">The **ConfigurationName** parameter is used to specify a disabled PowerShell endpoint.</span></span> <span data-ttu-id="447d2-150">자격 증명은 자격 **증명 매개 변수를 통해** 명령에 명시적으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-150">Credentials are explicitly passed to the command through the **Credential** parameter.</span></span> <span data-ttu-id="447d2-151">이 유형의 연결은 네트워크 스택을 통과 하며 루프백이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-151">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="447d2-152">따라서 **액세스 거부** 오류가 발생 하 여 비활성화 된 끝점에 대 한 연결 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-152">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="447d2-153">두 번째를 사용 하는 경우에 `New-PSSession` 도 로컬 컴퓨터에 대 한 원격 세션을 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-153">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="447d2-154">이 경우 네트워크 스택을 우회 하는 루프백 연결 이기 때문에 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-154">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="447d2-155">다음 조건이 충족 되 면 루프백 연결이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-155">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="447d2-156">연결할 컴퓨터 이름은 ' localhost '입니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-156">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="447d2-157">자격 증명은 전달 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-157">No credentials are passed in.</span></span> <span data-ttu-id="447d2-158">현재 로그인 한 사용자 (암시적 자격 증명)가 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-158">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="447d2-159">**EnableNetworkAccess** 스위치 매개 변수가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-159">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="447d2-160">루프백 연결에 대 한 자세한 내용은 [새 PSSession](New-PSSession.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="447d2-160">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="447d2-161">예 6: 모든 PowerShell 원격 끝점 구성 비활성화</span><span class="sxs-lookup"><span data-stu-id="447d2-161">Example 6: Disabling all PowerShell remoting endpoint configurations</span></span>

<span data-ttu-id="447d2-162">이 예제에서는 `Disable-PSRemoting` 명령을 실행 해도 Windows PowerShell 끝점 구성에 영향을 주지 않는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-162">This example demonstrates how running the `Disable-PSRemoting` command does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="447d2-163">`Get-PSSessionConfiguration` Windows PowerShell 내에서 실행은 모든 끝점 구성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-163">`Get-PSSessionConfiguration` run within Windows PowerShell shows all endpoint configurations.</span></span> <span data-ttu-id="447d2-164">Windows PowerShell 끝점 구성은 사용 하지 않도록 설정 되어 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-164">We see that the Windows PowerShell endpoint configurations are not disabled.</span></span>

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

<span data-ttu-id="447d2-165">이러한 끝점 구성을 사용 하지 않도록 설정 하려면 `Disable-PSRemoting` Windows PowerShell 세션 내에서 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-165">To disable these endpoint configurations, the `Disable-PSRemoting` command must be run from within a Windows PowerShell session.</span></span> <span data-ttu-id="447d2-166">이제 `Get-PSSessionConfiguration` Windows PowerShell 내에서를 실행 하면 모든 끝점 구성이 사용 하지 않도록 설정 된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-166">Now, `Get-PSSessionConfiguration` run from within Windows PowerShell shows that all endpoint configurations are disabled.</span></span>

### <span data-ttu-id="447d2-167">예 7: 사용자 지정 보안 설명자가 있는 세션 구성에 대 한 원격 액세스 방지</span><span class="sxs-lookup"><span data-stu-id="447d2-167">Example 7: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="447d2-168">이 예제에서는 cmdlet이 `Disable-PSRemoting` 사용자 지정 보안 설명자를 사용 하 여 세션 구성을 포함 하는 모든 세션 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 합니다</span><span class="sxs-lookup"><span data-stu-id="447d2-168">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="447d2-169">`Register-PSSessionConfiguration`**테스트** 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-169">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="447d2-170">**FilePath** 매개 변수는 세션을 사용자 지정 하는 세션 구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-170">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="447d2-171">**ShowSecurityDescriptorUI** 매개 변수는 세션 구성에 대 한 사용 권한을 설정 하는 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-171">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="447d2-172">권한 대화 상자에서 표시 된 사용자에 대 한 사용자 지정 전체 액세스 권한을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-172">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="447d2-173">`Get-PSSessionConfiguration`및 `Format-Table` cmdlet은 세션 구성과 해당 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-173">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="447d2-174">출력은 **테스트** 세션 구성에서 표시 된 사용자에 대 한 대화형 액세스 및 특별 한 사용 권한을 허용 한다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-174">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="447d2-175">`Disable-PSRemoting` 모든 세션 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-175">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

<span data-ttu-id="447d2-176">이제 `Get-PSSessionConfiguration` 및 `Format-Table` cmdlet은 모든 네트워크 사용자에 대 한 **accessdenied** 보안 설명자가 **테스트** 세션 구성을 비롯 한 모든 세션 구성에 추가 됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-176">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="447d2-177">다른 보안 설명자는 변경 되지 않지만 "network_deny_all" 보안 설명자가 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-177">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="447d2-178">이는를 사용 하 여 `New-PSSession` **테스트** 세션 구성에 연결 하려고 할 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-178">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="447d2-179">예 8: 선택한 세션 구성에 대 한 원격 액세스 다시 사용</span><span class="sxs-lookup"><span data-stu-id="447d2-179">Example 8: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="447d2-180">이 예제에서는 선택한 세션 구성에 대해서만 원격 액세스를 사용하도록 다시 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-180">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="447d2-181">모든 세션 구성을 사용 하지 않도록 설정한 후 특정 세션을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-181">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="447d2-182">`Set-PSSessionConfiguration`Cmdlet은 **PowerShell. 6** 세션 구성을 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-182">The `Set-PSSessionConfiguration` cmdlet is used to change the **PowerShell.6** session configuration.</span></span> <span data-ttu-id="447d2-183">값이 **remote** 인 **accessmode** 매개 변수는 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-183">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
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

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## <span data-ttu-id="447d2-184">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="447d2-184">PARAMETERS</span></span>

### <span data-ttu-id="447d2-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="447d2-185">-Confirm</span></span>

<span data-ttu-id="447d2-186">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="447d2-187">-Force</span><span class="sxs-lookup"><span data-stu-id="447d2-187">-Force</span></span>

<span data-ttu-id="447d2-188">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-188">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="447d2-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="447d2-189">-WhatIf</span></span>

<span data-ttu-id="447d2-190">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-190">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="447d2-191">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="447d2-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="447d2-192">CommonParameters</span></span>

<span data-ttu-id="447d2-193">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="447d2-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="447d2-194">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="447d2-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="447d2-195">입력</span><span class="sxs-lookup"><span data-stu-id="447d2-195">INPUTS</span></span>

### <span data-ttu-id="447d2-196">없음</span><span class="sxs-lookup"><span data-stu-id="447d2-196">None</span></span>

<span data-ttu-id="447d2-197">개체를이 cmdlet으로 파이프 할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-197">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="447d2-198">출력</span><span class="sxs-lookup"><span data-stu-id="447d2-198">OUTPUTS</span></span>

### <span data-ttu-id="447d2-199">없음</span><span class="sxs-lookup"><span data-stu-id="447d2-199">None</span></span>

<span data-ttu-id="447d2-200">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-200">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="447d2-201">참고</span><span class="sxs-lookup"><span data-stu-id="447d2-201">NOTES</span></span>

<span data-ttu-id="447d2-202">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-202">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="447d2-203">세션 구성을 사용 하지 않도록 설정 해도 또는 cmdlet에서 수행한 모든 변경 내용은 실행 취소 되지 않습니다 `Enable-PSRemoting` `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="447d2-203">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="447d2-204">다음 변경 작업을 수동으로 실행 취소해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-204">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="447d2-205">WinRM 서비스를 중지하고 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-205">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="447d2-206">모든 IP 주소에서 요청을 수락하는 수신기를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-206">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="447d2-207">WS-Management 통신에 대해 방화벽 예외를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-207">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="447d2-208">LocalAccountTokenFilterPolicy 값을 0으로 복원하여 컴퓨터에서 Administrators 그룹의 구성원에 대한 원격 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-208">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

- <span data-ttu-id="447d2-209">세션 끝점 구성은 세션의 환경을 정의 하는 설정 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-209">A session endpoint configuration is a group of settings that define the environment for a session.</span></span>
  <span data-ttu-id="447d2-210">컴퓨터에 연결 되는 모든 세션은 컴퓨터에 등록 된 세션 끝점 구성 중 하나를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-210">Every session that connects to the computer must use one of the session endpoint configurations that are registered on the computer.</span></span> <span data-ttu-id="447d2-211">모든 세션 끝점 구성에 대 한 원격 액세스를 거부 하면 원격 사용자가 컴퓨터에 연결 하는 세션을 설정 하는 것을 효과적으로 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="447d2-211">By denying remote access to all session endpoint configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

## <span data-ttu-id="447d2-212">관련 링크</span><span class="sxs-lookup"><span data-stu-id="447d2-212">RELATED LINKS</span></span>

[<span data-ttu-id="447d2-213">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="447d2-213">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="447d2-214">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="447d2-214">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="447d2-215">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="447d2-215">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="447d2-216">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="447d2-216">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="447d2-217">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="447d2-217">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="447d2-218">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="447d2-218">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="447d2-219">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="447d2-219">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="447d2-220">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="447d2-220">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)