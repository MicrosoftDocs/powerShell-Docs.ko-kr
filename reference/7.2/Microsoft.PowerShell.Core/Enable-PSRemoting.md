---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: a3d9506a0fd2adbb9cc093fb24f99e922dc8a938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599352"
---
# <span data-ttu-id="4060f-102">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="4060f-102">Enable-PSRemoting</span></span>

## <span data-ttu-id="4060f-103">개요</span><span class="sxs-lookup"><span data-stu-id="4060f-103">SYNOPSIS</span></span>
<span data-ttu-id="4060f-104">원격 명령을 받도록 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-104">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="4060f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4060f-105">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4060f-106">설명</span><span class="sxs-lookup"><span data-stu-id="4060f-106">DESCRIPTION</span></span>

<span data-ttu-id="4060f-107">`Enable-PSRemoting`Cmdlet은 WS-Management 기술을 사용 하 여 전송 된 PowerShell 원격 명령을 받도록 컴퓨터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-107">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="4060f-108">WS-Management 기반 PowerShell remoting은 현재 Windows 플랫폼 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-108">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="4060f-109">PowerShell remoting은 Windows Server 플랫폼에서 기본적으로 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-109">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="4060f-110">`Enable-PSRemoting`를 사용 하 여 지원 되는 다른 버전의 Windows에서 PowerShell 원격을 사용 하도록 설정 하 고, 사용 하지 않도록 설정 된 경우 원격 기능을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="4060f-111">명령을 수신 하는 각 컴퓨터에서이 명령을 한 번만 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="4060f-112">명령을 전송 하는 컴퓨터에서는 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="4060f-113">구성에서 수신기를 시작 하 여 원격 연결을 허용 하므로 필요한 경우에만 수신기를 실행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-113">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="4060f-114">컴퓨터가 공용 네트워크에 있을 때 Windows 클라이언트 버전에서 PowerShell 원격을 사용 하도록 설정 하는 것은 일반적으로 허용 되지 않지만 **SkipNetworkProfileCheck** 매개 변수를 사용 하 여이 제한을 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-114">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="4060f-115">자세한 내용은 **SkipNetworkProfileCheck** 매개 변수에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4060f-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="4060f-116">단일 컴퓨터에 여러 PowerShell 설치가 함께 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-116">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="4060f-117">를 실행 하면 `Enable-PSRemoting` 에서 cmdlet을 실행 하는 특정 설치 버전에 대 한 원격 끝점이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-117">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="4060f-118">따라서 `Enable-PSRemoting` powershell 6.2를 실행 하는 동안를 실행 하는 경우 powershell 6.2를 실행 하는 원격 끝점이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-118">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="4060f-119">`Enable-PSRemoting`Powershell 7-preview를 실행 하는 동안를 실행 하는 경우 powershell 7-preview를 실행 하는 원격 끝점이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-119">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="4060f-120">`Enable-PSRemoting` 필요에 따라 두 개의 원격 끝점 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-120">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="4060f-121">끝점 구성이 이미 있는 경우 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-121">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="4060f-122">만들어진 구성은 동일 하지만 이름이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-122">The created configurations are identical but have different names.</span></span> <span data-ttu-id="4060f-123">하나는 세션을 호스팅하는 PowerShell 버전에 해당 하는 단순한 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-123">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="4060f-124">다른 구성 이름에는 세션을 호스트 하는 PowerShell 버전에 대 한 자세한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-124">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="4060f-125">예를 들어 `Enable-PSRemoting` powershell 6.2에서 실행 하는 경우 **powershell. 6**, **6.2.2** 라는 두 개의 구성 된 끝점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-125">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6**, **PowerShell.6.2.2**.</span></span>
<span data-ttu-id="4060f-126">이렇게 하면 단순한 이름 **powershell. 6** 을 사용 하 여 최신 powershell 6 호스트 버전에 대 한 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-126">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6**.</span></span> <span data-ttu-id="4060f-127">또는 더 긴 이름 **6.2.2** 을 사용 하 여 특정 powershell 호스트 버전에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-127">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2**.</span></span>

<span data-ttu-id="4060f-128">새로 활성화 된 원격 끝점을 사용 하려면  `Invoke-Command` , `New-PSSession` , cmdlet을 사용 하 여 원격 연결을 만들 때 ConfigurationName 매개 변수를 이름으로 지정 해야 합니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4060f-128">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="4060f-129">자세한 내용은 예 4를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4060f-129">For more information, see Example 4.</span></span>

<span data-ttu-id="4060f-130">`Enable-PSRemoting`Cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-130">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="4060f-131">다음 작업을 수행 하는 [set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-131">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="4060f-132">WinRM 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-132">Starts the WinRM service.</span></span>
  - <span data-ttu-id="4060f-133">WinRM 서비스의 시작 유형을 자동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-133">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="4060f-134">모든 IP 주소에서 요청을 수락 하는 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-134">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="4060f-135">WS-Management 통신에 대 한 방화벽 예외를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-135">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="4060f-136">필요한 경우 간단 하 고 긴 이름 세션 끝점 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-136">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="4060f-137">모든 세션 구성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-137">Enables all session configurations.</span></span>
  - <span data-ttu-id="4060f-138">모든 세션 구성의 보안 설명자를 변경 하 여 원격 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-138">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="4060f-139">WinRM 서비스를 다시 시작 하 여 위의 변경 내용이 적용 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-139">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="4060f-140">Windows 플랫폼에서이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-140">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="4060f-141">이 cmdlet은 Linux 또는 MacOS 버전의 PowerShell에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-141">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="4060f-142">이 cmdlet은 Windows PowerShell에서 만든 원격 끝점 구성에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-142">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="4060f-143">PowerShell 버전 6 이상을 사용 하 여 만든 끝점에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-143">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="4060f-144">Windows PowerShell에서 호스트 되는 PowerShell 원격 끝점을 사용 하거나 사용 하지 않도록 설정 하려면 `Enable-PSRemoting` Windows powershell 세션에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-144">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="4060f-145">예제</span><span class="sxs-lookup"><span data-stu-id="4060f-145">EXAMPLES</span></span>

### <span data-ttu-id="4060f-146">예 1: 원격 명령을 받도록 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="4060f-146">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="4060f-147">이 명령은 원격 명령을 수신하도록 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-147">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="4060f-148">예 2: 확인 메시지 없이 원격 명령을 받도록 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="4060f-148">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="4060f-149">이 명령은 원격 명령을 수신하도록 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-149">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="4060f-150">**Force** 매개 변수를 사용 하면 사용자 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-150">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="4060f-151">예제 3: 클라이언트에서 원격 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="4060f-151">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="4060f-152">이 예제에서는 Windows 운영 체제 클라이언트 버전의 공용 네트워크에서 원격 액세스를 허용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-152">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="4060f-153">방화벽 규칙의 이름은 서로 다른 버전의 Windows에 대해 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-153">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="4060f-154">`Get-NetFirewallRule`규칙 목록을 보려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-154">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="4060f-155">방화벽 규칙을 사용 하도록 설정 하기 전에 규칙의 보안 설정을 확인 하 여 구성이 환경에 적합 한지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-155">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

<span data-ttu-id="4060f-156">기본적으로에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에서 원격 액세스를 허용 하는 네트워크 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-156">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="4060f-157">이 명령은 **SkipNetworkProfileCheck** 매개 변수를 사용하여 동일한 로컬 서브넷에 있는 공용 네트워크에서의 원격 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-157">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="4060f-158">명령은 **Force** 매개 변수를 지정 하 여 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-158">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="4060f-159">**SkipNetworkProfileCheck** 매개 변수는 기본적으로 동일한 로컬 서브넷에 있는 공용 네트워크에서의 원격 액세스를 허용 하는 Windows 운영 체제의 서버 버전에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-159">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="4060f-160">`Set-NetFirewallRule` **Netsecurity** 모듈의 cmdlet은 원격 위치의 공용 네트워크에서 원격 액세스를 허용 하는 방화벽 규칙을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-160">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="4060f-161">여기에는 다른 서브넷의 위치가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-161">This includes locations in different subnets.</span></span>

### <span data-ttu-id="4060f-162">예제 4: 새로 활성화 된 끝점 구성에 대 한 원격 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="4060f-162">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="4060f-163">이 예제에서는 컴퓨터에서 PowerShell 원격을 사용 하도록 설정 하 고 구성 된 끝점 이름을 찾고 끝점 중 하나에 대 한 원격 세션을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-163">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="4060f-164">첫 번째 명령은 컴퓨터에서 PowerShell 원격을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-164">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="4060f-165">두 번째 명령은 끝점 구성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-165">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="4060f-166">세 번째 명령은 이름을 기준으로 **powershell. 6** 끝점을 지정 하 여 동일한 컴퓨터에 대 한 원격 powershell 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-166">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="4060f-167">원격 세션은 최신 PowerShell 6 버전 (6.2.2)을 사용 하 여 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-167">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="4060f-168">마지막 명령은 `$PSVersionTable` 원격 세션의 변수에 액세스 하 여 세션을 호스트 하는 PowerShell 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-168">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> <span data-ttu-id="4060f-169">방화벽 규칙의 이름은 Windows 버전에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-169">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="4060f-170">Cmdlet을 사용 `Get-NetFirewallRule` 하 여 시스템에 있는 규칙의 이름을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-170">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="4060f-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4060f-171">PARAMETERS</span></span>

### <span data-ttu-id="4060f-172">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4060f-172">-Confirm</span></span>

<span data-ttu-id="4060f-173">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-173">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4060f-174">-Force</span><span class="sxs-lookup"><span data-stu-id="4060f-174">-Force</span></span>

<span data-ttu-id="4060f-175">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-175">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4060f-176">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="4060f-176">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="4060f-177">이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 Windows 운영 체제의 클라이언트 버전에서 원격 기능을 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-177">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="4060f-178">이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-178">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="4060f-179">이 매개 변수는 기본적으로 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있는 Windows 운영 체제의 서버 버전에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-179">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="4060f-180">서버 버전에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우 `Enable-PSRemoting` 이 매개 변수 값에 관계 없이을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-180">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="4060f-181">로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` **netsecurity** 모듈에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-181">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="4060f-182">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-182">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="4060f-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4060f-183">-WhatIf</span></span>

<span data-ttu-id="4060f-184">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-184">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4060f-185">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4060f-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4060f-186">CommonParameters</span></span>

<span data-ttu-id="4060f-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4060f-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4060f-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4060f-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4060f-189">입력</span><span class="sxs-lookup"><span data-stu-id="4060f-189">INPUTS</span></span>

### <span data-ttu-id="4060f-190">없음</span><span class="sxs-lookup"><span data-stu-id="4060f-190">None</span></span>

<span data-ttu-id="4060f-191">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-191">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4060f-192">출력</span><span class="sxs-lookup"><span data-stu-id="4060f-192">OUTPUTS</span></span>

### <span data-ttu-id="4060f-193">System.String</span><span class="sxs-lookup"><span data-stu-id="4060f-193">System.String</span></span>

<span data-ttu-id="4060f-194">이 cmdlet은 결과를 설명 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-194">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="4060f-195">참고</span><span class="sxs-lookup"><span data-stu-id="4060f-195">NOTES</span></span>

<span data-ttu-id="4060f-196">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-196">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="4060f-197">서버 버전의 Windows 운영 체제에서는 `Enable-PSRemoting` 원격 액세스를 허용 하는 개인 및 도메인 네트워크에 대 한 방화벽 규칙을 만들고, 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-197">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="4060f-198">클라이언트 버전의 Windows 운영 체제에서는 `Enable-PSRemoting` 무제한의 원격 액세스를 허용 하는 개인 및 도메인 네트워크에 대 한 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-198">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="4060f-199">공용 네트워크에 대해 동일한 로컬 서브넷에서의 원격 액세스를 허용하는 방화벽 규칙을 만들려면 **SkipNetworkProfileCheck** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-199">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="4060f-200">클라이언트 또는 서버 버전의 Windows 운영 체제에서 로컬 서브넷 제한을 제거 하 고 원격 액세스를 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만들려면 `Set-NetFirewallRule` NetSecurity 모듈에서 cmdlet을 사용 하 여 다음 명령을 실행 합니다. `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="4060f-200">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="4060f-201">`Enable-PSRemoting` 모든 세션 구성의 **Enabled** 속성 값을로 설정 하 여 모든 세션 구성을 사용 하도록 설정 `$True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-201">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="4060f-202">`Enable-PSRemoting`**Deny_All** 및 **Network_Deny_All** 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-202">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="4060f-203">로컬에서 사용 하도록 예약 된 세션 구성에 대 한 원격 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4060f-203">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="4060f-204">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4060f-204">RELATED LINKS</span></span>

[<span data-ttu-id="4060f-205">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4060f-205">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="4060f-206">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4060f-206">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="4060f-207">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4060f-207">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="4060f-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4060f-208">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="4060f-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4060f-209">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="4060f-210">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="4060f-210">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="4060f-211">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="4060f-211">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="4060f-212">about_Remote</span><span class="sxs-lookup"><span data-stu-id="4060f-212">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="4060f-213">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="4060f-213">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)