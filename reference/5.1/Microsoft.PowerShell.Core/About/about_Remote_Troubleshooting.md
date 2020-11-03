---
description: PowerShell에서 원격 작업의 문제를 해결 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: 33661392583393b69723449a914ace84f394fc94
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93225282"
---
# <a name="about-remote-troubleshooting"></a><span data-ttu-id="db736-104">원격 문제 해결 정보</span><span class="sxs-lookup"><span data-stu-id="db736-104">About Remote Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="db736-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="db736-105">Short description</span></span>
<span data-ttu-id="db736-106">PowerShell에서 원격 작업의 문제를 해결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-106">Describes how to troubleshoot remote operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="db736-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="db736-107">Long description</span></span>

<span data-ttu-id="db736-108">이 섹션에서는 WS-Management 기술을 기반으로 하는 PowerShell의 원격 기능을 사용 하는 경우 발생할 수 있는 몇 가지 문제에 대해 설명 하 고 이러한 문제에 대 한 해결 방법을 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-108">This section describes some of the problems that you might encounter when using the remoting features of PowerShell that are based on WS-Management technology and it suggests solutions to these problems.</span></span>

<span data-ttu-id="db736-109">PowerShell 원격 기능을 사용 하기 전에 [about_Remote](about_remote.md) 및 [about_Remote_Requirements](about_Remote_Requirements.md) 에서 구성 및 기본 사용에 대 한 지침을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-109">Before using PowerShell remoting, see [about_Remote](about_remote.md) and [about_Remote_Requirements](about_Remote_Requirements.md) for guidance on configuration and basic use.</span></span> <span data-ttu-id="db736-110">또한 각 원격 cmdlet에 대 한 도움말 항목 (특히 매개 변수 설명)에는 문제를 방지 하는 데 도움이 되도록 설계 된 유용한 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-110">Also, the Help topics for each of the remoting cmdlets, particularly the parameter descriptions, have useful information that is designed to help you avoid problems.</span></span>

> [!NOTE]
> <span data-ttu-id="db736-111">WSMan: 드라이브에서 세션 구성, 신뢰할 수 있는 호스트, 포트 또는 수신기에 대 한 변경 내용을 포함 하 여 로컬 컴퓨터에 대 한 설정을 보거나 변경 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-111">To view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="troubleshooting-permission-and-authentication-issues"></a><span data-ttu-id="db736-112">권한 및 인증 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db736-112">Troubleshooting permission and authentication issues</span></span>

<span data-ttu-id="db736-113">이 섹션에서는 사용자 및 컴퓨터 권한 및 원격 요구 사항과 관련 된 원격 문제에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-113">This section discusses remoting problems that are related to user and computer permissions and remoting requirements.</span></span>

### <a name="how-to-run-as-administrator"></a><span data-ttu-id="db736-114">관리자 권한으로 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-114">How to run as administrator</span></span>

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

<span data-ttu-id="db736-115">로컬 컴퓨터에서 원격 세션을 시작 하거나 WSMan: 드라이브에서 로컬 컴퓨터에 대 한 설정을 확인 하거나 변경 하려면 (세션 구성, 신뢰할 수 있는 호스트, 포트 또는 수신기 변경 포함) **관리자 권한으로 실행** 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-115">To start a remote session on the local computer, or to view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start Windows PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="db736-116">**관리자 권한으로 실행** 옵션을 사용 하 여 Windows PowerShell을 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-116">To start Windows PowerShell with the **Run as administrator** option:</span></span>

- <span data-ttu-id="db736-117">Windows PowerShell (또는 Windows PowerShell ISE) 아이콘을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-117">Right-click a Windows PowerShell (or Windows PowerShell ISE) icon and then click **Run as administrator**.</span></span>

  <span data-ttu-id="db736-118">Windows 7 및 Windows Server 2008 r 2에서 **관리자 권한으로 실행** 옵션을 사용 하 여 windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-118">To start Windows PowerShell with the **Run as administrator** option in Windows 7 and Windows Server 2008 R2.</span></span>

- <span data-ttu-id="db736-119">Windows 작업 표시줄에서 Windows PowerShell 아이콘을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-119">In the Windows taskbar, right-click the Windows PowerShell icon, and then click **Run as administrator**.</span></span>

  <span data-ttu-id="db736-120">Windows Server 2008 r 2에서 Windows PowerShell 아이콘은 기본적으로 작업 표시줄에 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-120">In Windows Server 2008 R2, the Windows PowerShell icon is pinned to the taskbar by default.</span></span>

### <a name="how-to-enable-remoting"></a><span data-ttu-id="db736-121">원격 기능을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-121">How to enable remoting</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

<span data-ttu-id="db736-122">컴퓨터에서 원격 명령을 보낼 수 있도록 하는 구성은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-122">No configuration is required to enable a computer to send remote commands.</span></span>
<span data-ttu-id="db736-123">그러나 원격 명령을 받으려면 컴퓨터에서 PowerShell 원격을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-123">However, to receive remote commands, PowerShell remoting must be enabled on the computer.</span></span> <span data-ttu-id="db736-124">을 사용 하도록 설정 하려면 WinRM 서비스를 시작 하 고, WinRM 서비스의 시작 유형을 자동으로 설정 하 고, HTTP 및 HTTPS 연결에 대 한 수신기를 만들고, 기본 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-124">Enabling includes starting the WinRM service, setting the startup type for the WinRM service to Automatic, creating listeners for HTTP and HTTPS connections, and creating default session configurations.</span></span>

<span data-ttu-id="db736-125">Windows PowerShell remoting은 기본적으로 windows server 2012 및 최신 버전의 Windows Server에서 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-125">Windows PowerShell remoting is enabled on Windows Server 2012 and newer releases of Windows Server by default.</span></span> <span data-ttu-id="db736-126">다른 모든 시스템에서 cmdlet을 실행 `Enable-PSRemoting` 하 여 원격 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-126">On all other systems, run the `Enable-PSRemoting` cmdlet to enable remoting.</span></span> <span data-ttu-id="db736-127">또한 `Enable-PSRemoting` 원격 기능을 사용 하지 않도록 설정 된 경우 cmdlet을 실행 하 여 windows server 2012 및 최신 버전의 Windows server에서 원격 기능을 다시 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-127">You can also run the `Enable-PSRemoting` cmdlet to re-enable remoting on Windows Server 2012 and newer releases of Windows Server if remoting is disabled.</span></span>

<span data-ttu-id="db736-128">원격 명령을 받도록 컴퓨터를 구성 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-128">To configure a computer to receive remote commands, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="db736-129">다음 명령은 필요한 모든 원격 설정을 사용 하도록 설정 하 고, 세션 구성을 사용 하도록 설정 하 고, 변경 내용을 적용 하기 위해 WinRM 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-129">The following command enables all required remote settings, enables the session configurations, and restarts the WinRM service to make the changes effective.</span></span>

`Enable-PSRemoting`

<span data-ttu-id="db736-130">모든 사용자 프롬프트를 표시 하지 않으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-130">To suppress all user prompts, type:</span></span>

`Enable-PSRemoting -Force`

<span data-ttu-id="db736-131">자세한 내용은 [enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-131">For more information, see [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span></span>

### <a name="how-to-enable-remoting-in-an-enterprise"></a><span data-ttu-id="db736-132">엔터프라이즈에서 원격 기능을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-132">How to enable remoting in an enterprise</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="db736-133">단일 컴퓨터에서 원격 PowerShell 명령을 수신 하 고 연결을 허용할 수 있도록 설정 하려면 `Enable-PSRemoting` cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-133">To enable a single computer to receive remote PowerShell commands and accept connections, use the `Enable-PSRemoting` cmdlet.</span></span>

<span data-ttu-id="db736-134">기업에서 여러 컴퓨터에 대 한 원격 기능을 사용 하도록 설정 하려면 다음과 같은 크기 조정 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-134">To enable remoting for multiple computers in an enterprise, you can use the following scaled options.</span></span>

- <span data-ttu-id="db736-135">원격을 위한 수신기를 구성 하려면 **수신기의 자동 구성 허용** 그룹 정책을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-135">To configure listeners for remoting, enable the **Allow automatic configuration of listeners** group policy.</span></span>

- <span data-ttu-id="db736-136">여러 컴퓨터에서 WinRM (Windows 원격 관리의 시작 유형을 자동으로 설정 하려면 cmdlet을 사용 합니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="db736-136">To set the startup type of the Windows Remote Management (WinRM) to Automatic on multiple computers, use the `Set-Service` cmdlet.</span></span>

- <span data-ttu-id="db736-137">방화벽 예외를 사용 하도록 설정 하려면 **Windows 방화벽: 로컬 포트 예외 허용** 그룹 정책을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-137">To enable a firewall exception, use the **Windows Firewall: Allow Local Port Exceptions** group policy.</span></span>

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a><span data-ttu-id="db736-138">그룹 정책을 사용 하 여 수신기를 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-138">How to enable listeners by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="db736-139">도메인의 모든 컴퓨터에 대 한 수신기를 구성 하려면 다음 그룹 정책 경로에서 **수신기 자동 구성 허용** 정책을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-139">To configure the listeners for all computers in a domain, enable the **Allow automatic configuration of listeners** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

<span data-ttu-id="db736-140">정책을 사용 하도록 설정 하 고 IPv4 및 IPv6 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-140">Enable the policy and specify the IPv4 and IPv6 filters.</span></span> <span data-ttu-id="db736-141">와일드 카드 ( `*` )를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-141">Wildcards (`*`) are permitted.</span></span>

### <a name="how-to-enable-remoting-on-public-networks"></a><span data-ttu-id="db736-142">공용 네트워크에서 원격 기능을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-142">How to enable remoting on public networks</span></span>

```
ERROR:  Unable to check the status of the firewall
```

<span data-ttu-id="db736-143">`Enable-PSRemoting`로컬 네트워크가 public이 고 명령에서 **SkipNetworkProfileCheck** 매개 변수를 사용 하지 않는 경우 cmdlet은이 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-143">The `Enable-PSRemoting` cmdlet returns this error when the local network is public and the **SkipNetworkProfileCheck** parameter is not used in the command.</span></span>

<span data-ttu-id="db736-144">서버 버전의 Windows에서는 `Enable-PSRemoting` 모든 네트워크 위치 형식에 대해 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-144">On server versions of Windows, `Enable-PSRemoting` succeeds on all network location types.</span></span> <span data-ttu-id="db736-145">개인 및 도메인 ("홈" 및 "회사") 네트워크에 대 한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-145">It creates firewall rules that allow remote access to private and domain ("Home" and "Work") networks.</span></span> <span data-ttu-id="db736-146">공용 네트워크의 경우 동일한 로컬 서브넷의 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-146">For public networks, it creates firewall rules that allows remote access from the same local subnet.</span></span>

<span data-ttu-id="db736-147">클라이언트 버전의 Windows에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에 대해 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-147">On client versions of Windows, `Enable-PSRemoting` succeeds on private and domain networks.</span></span> <span data-ttu-id="db736-148">기본적으로 공용 네트워크에서는 실패 하지만, **SkipNetworkProfileCheck** 매개 변수를 사용 하는 경우가 `Enable-PSRemoting` 성공 하 고 동일한 로컬 서브넷의 트래픽을 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-148">By default, it fails on public networks, but if you use the **SkipNetworkProfileCheck** parameter, `Enable-PSRemoting` succeeds and creates a firewall rule that allows traffic from the same local subnet.</span></span>

<span data-ttu-id="db736-149">공용 네트워크에 대 한 로컬 서브넷 제한을 제거 하 고 모든 위치에서 원격 액세스를 허용 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-149">To remove the local subnet restriction on public networks and allow remote access from any location, run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="db736-150">`Set-NetFirewallRule`NetSecurity 모듈에서 cmdlet을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db736-150">The `Set-NetFirewallRule` cmdlet is exported by the NetSecurity module.</span></span>

> [!NOTE]
> <span data-ttu-id="db736-151">Windows PowerShell 2.0에서는 Windows의 서버 버전을 실행 하는 컴퓨터에서 `Enable-PSRemoting` 개인, 도메인 및 공용 네트워크에 대 한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-151">In Windows PowerShell 2.0, on computers running server versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access on private, domain and public networks.</span></span> <span data-ttu-id="db736-152">클라이언트 버전의 Windows를 실행 하는 컴퓨터에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에 대 한 원격 액세스만 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-152">On computers running client versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access only on private and domain networks.</span></span>

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a><span data-ttu-id="db736-153">그룹 정책을 사용 하 여 방화벽 예외를 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-153">How to enable a firewall exception by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="db736-154">도메인의 모든 컴퓨터에서에 대해 방화벽 예외를 사용 하도록 설정 하려면 다음 그룹 정책 경로에서 **Windows 방화벽: 로컬 포트 예외 허용** 정책을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-154">To enable a firewall exception for in all computers in a domain, enable the **Windows Firewall: Allow local port exceptions** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

<span data-ttu-id="db736-155">이 정책을 사용 하면 컴퓨터의 Administrators 그룹 구성원은 **제어판** 의 **Windows 방화벽** 을 사용 하 여 Windows 원격 관리 서비스에 대 한 방화벽 예외를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-155">This policy allows members of the Administrators group on the computer to use **Windows Firewall** in **Control Panel** to create a firewall exception for the Windows Remote Management service.</span></span>

<span data-ttu-id="db736-156">정책 구성이 잘못 된 경우 다음 오류가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-156">If the policy configuration is incorrect you may receive the following error:</span></span>

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

<span data-ttu-id="db736-157">정책에서 구성 오류가 발생 하면 **ListeningOn** 속성에 대해 빈 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-157">A configuration error in the policy results in an empty value for the **ListeningOn** property.</span></span> <span data-ttu-id="db736-158">다음 명령을 사용 하 여 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-158">Use the following command to check the value.</span></span>

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a><span data-ttu-id="db736-159">WinRM 서비스의 시작 유형을 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-159">How to set the startup type of the WinRM service</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="db736-160">PowerShell remoting은 Windows 원격 관리 (WinRM) 서비스에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="db736-160">PowerShell remoting depends upon the Windows Remote Management (WinRM) service.</span></span>
<span data-ttu-id="db736-161">원격 명령을 지원 하려면 서비스가 실행 중 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-161">The service must be running to support remote commands.</span></span>

<span data-ttu-id="db736-162">Windows의 서버 버전에서 WinRM (Windows 원격 관리) 서비스의 시작 유형은 자동입니다.</span><span class="sxs-lookup"><span data-stu-id="db736-162">On server versions of Windows, the startup type of the Windows Remote Management (WinRM) service is Automatic.</span></span>

<span data-ttu-id="db736-163">그러나 Windows의 클라이언트 버전에서는 WinRM 서비스가 기본적으로 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-163">However, on client versions of Windows, the WinRM service is disabled by default.</span></span>

<span data-ttu-id="db736-164">원격 컴퓨터에서 서비스의 시작 유형을 설정 하려면 cmdlet을 사용 합니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="db736-164">To set the startup type of a service on a remote computer, use the `Set-Service` cmdlet.</span></span>

<span data-ttu-id="db736-165">여러 컴퓨터에서 명령을 실행 하려면 컴퓨터 이름의 텍스트 파일 또는 CSV 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-165">To run the command on multiple computers, you can create a text file or CSV file of the computer names.</span></span>

<span data-ttu-id="db736-166">예를 들어 다음 명령은 파일에서 컴퓨터 이름 목록을 가져온 `Servers.txt` 다음 모든 컴퓨터에서 WinRM 서비스의 시작 유형을 **자동** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-166">For example, the following commands get a list of computer names from the `Servers.txt` file and then sets the startup type of the WinRM service on all of the computers to **Automatic**.</span></span>

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

<span data-ttu-id="db736-167">결과를 보려면 `Get-WMIObject` **Win32_Service** 개체와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-167">To see the results use the `Get-WMIObject` cmdlet with the **Win32_Service** object.</span></span> <span data-ttu-id="db736-168">자세한 내용은 [설정-서비스](xref:Microsoft.PowerShell.Management.Set-Service)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-168">For more information, see [Set-Service](xref:Microsoft.PowerShell.Management.Set-Service).</span></span>

### <a name="how-to-recreate-the-default-session-configurations"></a><span data-ttu-id="db736-169">기본 세션 구성을 다시 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-169">How to recreate the default session configurations</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="db736-170">로컬 컴퓨터에 연결 하 여 원격으로 명령을 실행 하려면 로컬 컴퓨터에 원격 명령에 대 한 세션 구성을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-170">To connect to the local computer and run commands remotely, the local computer must include session configurations for remote commands.</span></span>

<span data-ttu-id="db736-171">를 사용 하면 `Enable-PSRemoting` 로컬 컴퓨터에 기본 세션 구성이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="db736-171">When you use `Enable-PSRemoting`, it creates default session configurations on the local computer.</span></span> <span data-ttu-id="db736-172">원격 사용자는 원격 명령이 **ConfigurationName** 매개 변수를 포함 하지 않을 때마다 이러한 세션 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-172">Remote users use these session configurations whenever a remote command does not include the **ConfigurationName** parameter.</span></span>

<span data-ttu-id="db736-173">컴퓨터의 기본 구성이 등록 취소 되거나 삭제 된 경우 cmdlet을 사용 `Enable-PSRemoting` 하 여 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-173">If the default configurations on a computer are unregistered or deleted, use the `Enable-PSRemoting` cmdlet to recreate them.</span></span> <span data-ttu-id="db736-174">이 cmdlet은 반복적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-174">You can use this cmdlet repeatedly.</span></span> <span data-ttu-id="db736-175">기능이 이미 구성 되어 있으면 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-175">It does not generate errors if a feature is already configured.</span></span>

<span data-ttu-id="db736-176">기본 세션 구성을 변경 하 고 원래 기본 세션 구성을 복원 하려면 cmdlet을 사용 `Unregister-PSSessionConfiguration` 하 여 변경 된 세션 구성을 삭제 한 다음 cmdlet을 사용 하 여 `Enable-PSRemoting` 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-176">If you change the default session configurations and want to restore the original default session configurations, use the `Unregister-PSSessionConfiguration` cmdlet to delete the changed session configurations and then use the `Enable-PSRemoting` cmdlet to restore them.</span></span>
<span data-ttu-id="db736-177">`Enable-PSRemoting` 기존 세션 구성을 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-177">`Enable-PSRemoting` does not change existing session configurations.</span></span>

> [!NOTE]
> <span data-ttu-id="db736-178">는 `Enable-PSRemoting` 기본 세션 구성을 복원할 때 구성에 대 한 명시적인 보안 설명자를 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-178">When `Enable-PSRemoting` restores the default session configuration, it does not create explicit security descriptors for the configurations.</span></span> <span data-ttu-id="db736-179">대신, 구성은 기본적으로 보안 되는 RootSDDL의 보안 설명자를 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-179">Instead, the configurations inherit the security descriptor of the RootSDDL, which is secure by default.</span></span>

<span data-ttu-id="db736-180">RootSDDL 보안 설명자를 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-180">To see the RootSDDL security descriptor, type:</span></span>

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

<span data-ttu-id="db736-181">RootSDDL를 변경 하려면 `Set-Item` WSMan: 드라이브에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-181">To change the RootSDDL, use the `Set-Item` cmdlet in the WSMan: drive.</span></span> <span data-ttu-id="db736-182">세션 구성의 보안 설명자를 변경 하려면 `Set-PSSessionConfiguration` **SecurityDescriptorSDDL** 또는 **ShowSecurityDescriptorUI** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-182">To change the security descriptor of a session configuration, use the `Set-PSSessionConfiguration` cmdlet with the **SecurityDescriptorSDDL** or **ShowSecurityDescriptorUI** parameters.</span></span>

<span data-ttu-id="db736-183">WSMan: 드라이브에 대 한 자세한 내용은 WSMan 공급자에 대 한 도움말 항목 ("Get-help WSMan")을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="db736-183">For more information about the WSMan: drive, see the Help topic for the WSMan provider ("Get-Help wsman").</span></span>

### <a name="how-to-provide-administrator-credentials"></a><span data-ttu-id="db736-184">관리자 자격 증명을 제공 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-184">How to provide administrator credentials</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="db736-185">PSSession을 만들거나 원격 컴퓨터에서 명령을 실행 하려면 기본적으로 현재 사용자가 원격 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-185">To create a PSSession or run commands on a remote computer, by default, the current user must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="db736-186">자격 증명은 현재 사용자가 Administrators 그룹의 구성원 인 계정에 로그온 한 경우에도 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-186">Credentials are sometimes required even when the current user is logged on to an account that is a member of the Administrators group.</span></span>

<span data-ttu-id="db736-187">현재 사용자가 원격 컴퓨터에서 Administrators 그룹의 구성원 이거나 Administrators 그룹의 멤버 자격 증명을 제공할 수 있는 경우, 또는 cmdlet의 **Credential** 매개 변수를 사용 하 여 원격으로 `New-PSSession` `Enter-PSSession` `Invoke-Command` 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-187">If the current user is a member of the Administrators group on the remote computer, or can provide the credentials of a member of the Administrators group, use the **Credential** parameter of the `New-PSSession`, `Enter-PSSession` or `Invoke-Command` cmdlets to connect remotely.</span></span>

<span data-ttu-id="db736-188">예를 들어 다음 명령은 관리자의 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-188">For example, the following command provides the credentials of an Administrator.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="db736-189">**Credential** 매개 변수에 대 한 자세한 내용은 [New-pssession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 또는 [Invoke 명령을](xref:Microsoft.PowerShell.Core.Invoke-Command)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-189">For more information about the **Credential** parameter, see [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span></span>

### <a name="how-to-enable-remoting-for-non-administrative-users"></a><span data-ttu-id="db736-190">비관리자 사용자에 대해 원격 기능을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-190">How to enable remoting for non-administrative users</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="db736-191">PSSession을 설정 하거나 원격 컴퓨터에서 명령을 실행 하려면 사용자가 원격 컴퓨터에서 세션 구성을 사용할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-191">To establish a PSSession or run a command on a remote computer, the user must have permission to use the session configurations on the remote computer.</span></span>

<span data-ttu-id="db736-192">기본적으로 컴퓨터의 Administrators 그룹 구성원 에게만 기본 세션 구성을 사용할 수 있는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-192">By default, only members of the Administrators group on a computer have permission to use the default session configurations.</span></span> <span data-ttu-id="db736-193">따라서 Administrators 그룹의 멤버만이 컴퓨터에 원격으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-193">Therefore, only members of the Administrators group can connect to the computer remotely.</span></span>

<span data-ttu-id="db736-194">다른 사용자가 로컬 컴퓨터에 연결할 수 있도록 하려면 로컬 컴퓨터의 기본 세션 구성에 대 한 실행 권한을 사용자에 게 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-194">To allow other users to connect to the local computer, give the user Execute permissions to the default session configurations on the local computer.</span></span>

<span data-ttu-id="db736-195">다음 명령을 사용 하 여 로컬 컴퓨터에서 기본 Microsoft. PowerShell 세션 구성의 보안 설명자를 변경할 수 있는 속성 시트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db736-195">The following command opens a property sheet that lets you change the security descriptor of the default Microsoft.PowerShell session configuration on the local computer.</span></span>

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

<span data-ttu-id="db736-196">자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-196">For more information, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a><span data-ttu-id="db736-197">다른 도메인의 관리자가 원격 기능을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-197">How to enable remoting for administrators in other domains</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="db736-198">다른 도메인의 사용자가 로컬 컴퓨터에서 Administrators 그룹의 구성원이 면 사용자는 관리자 권한으로 로컬 컴퓨터에 원격으로 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-198">When a user in another domain is a member of the Administrators group on the local computer, the user cannot connect to the local computer remotely with Administrator privileges.</span></span> <span data-ttu-id="db736-199">기본적으로 다른 도메인의 원격 연결은 표준 사용자 권한 토큰만 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-199">By default, remote connections from other domains run with only standard user privilege tokens.</span></span>

<span data-ttu-id="db736-200">그러나 **LocalAccountTokenFilterPolicy** 레지스트리 항목을 사용 하 여 기본 동작을 변경 하 고 관리자 그룹의 멤버인 원격 사용자가 관리자 권한으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-200">However, you can use the **LocalAccountTokenFilterPolicy** registry entry to change the default behavior and allow remote users who are members of the Administrators group to run with Administrator privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="db736-201">**LocalAccountTokenFilterPolicy** 항목은 영향을 받는 모든 컴퓨터의 모든 사용자에 대해 UAC (사용자 계정 컨트롤) 원격 제한을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-201">The **LocalAccountTokenFilterPolicy** entry disables user account control (UAC) remote restrictions for all users of all affected computers.</span></span> <span data-ttu-id="db736-202">정책을 변경 하기 전에이 설정의 영향을 신중 하 게 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-202">Consider the implications of this setting carefully before changing the policy.</span></span>

<span data-ttu-id="db736-203">정책을 변경 하려면 다음 명령을 사용 하 여 **LocalAccountTokenFilterPolicy** 레지스트리 항목의 값을 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-203">To change the policy, use the following command to set the value of the **LocalAccountTokenFilterPolicy** registry entry to 1.</span></span>

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a><span data-ttu-id="db736-204">원격 명령에서 ip 주소를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-204">How to use an ip address in a remote command</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="db736-205">, Cmdlet의 **ComputerName** 매개 변수는 `New-PSSession` `Enter-PSSession` `Invoke-Command` IP 주소를 유효한 값으로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="db736-205">The **ComputerName** parameter of the `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets accepts an IP address as a valid value.</span></span> <span data-ttu-id="db736-206">그러나 Kerberos 인증은 IP 주소를 지원 하지 않기 때문에 IP 주소를 지정할 때마다 기본적으로 NTLM 인증이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-206">However, because Kerberos authentication does not support IP addresses, NTLM authentication is used by default whenever you specify an IP address.</span></span>

<span data-ttu-id="db736-207">NTLM 인증을 사용 하는 경우 원격 작업에 다음 절차가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-207">When using NTLM authentication, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="db736-208">HTTPS 전송을 사용할 컴퓨터를 구성 하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 TrustedHosts 목록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-208">Configure the computer for HTTPS transport or add the IP addresses of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="db736-209">모든 원격 명령에 **Credential** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-209">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="db736-210">현재 사용자의 자격 증명을 제출 하는 경우에도 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-210">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a><span data-ttu-id="db736-211">작업 그룹 기반 컴퓨터에서 원격으로 연결 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-211">How to connect remotely from a workgroup-based computer</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="db736-212">로컬 컴퓨터가 도메인에 있지 않은 경우 원격 작업에 다음 절차가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-212">When the local computer is not in a domain, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="db736-213">HTTPS 전송을 위해 컴퓨터를 구성 하거나 로컬 컴퓨터의 TrustedHosts 목록에 원격 컴퓨터의 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-213">Configure the computer for HTTPS transport or add the names of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="db736-214">작업 그룹 기반 컴퓨터에 암호가 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-214">Verify that a password is set on the workgroup-based computer.</span></span> <span data-ttu-id="db736-215">암호를 설정 하지 않거나 암호 값이 비어 있으면 원격 명령을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-215">If a password is not set or the password value is empty, you cannot run remote commands.</span></span>

   <span data-ttu-id="db736-216">사용자 계정에 대 한 암호를 설정 하려면 제어판의 사용자 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-216">To set password for your user account, use User Accounts in Control Panel.</span></span>

1. <span data-ttu-id="db736-217">모든 원격 명령에 **Credential** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-217">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="db736-218">현재 사용자의 자격 증명을 제출 하는 경우에도 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-218">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a><span data-ttu-id="db736-219">신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-219">How to add a computer to the trusted hosts list</span></span>

<span data-ttu-id="db736-220">TrustedHosts 항목은 컴퓨터 이름, IP 주소 및 정규화 된 도메인 이름의 쉼표로 구분 된 목록을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-220">The TrustedHosts item can contain a comma-separated list of computer names, IP addresses, and fully-qualified domain names.</span></span> <span data-ttu-id="db736-221">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-221">Wildcards are permitted.</span></span>

<span data-ttu-id="db736-222">신뢰할 수 있는 호스트 목록을 보거나 변경 하려면 WSMan: 드라이브를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-222">To view or change the trusted host list, use the WSMan: drive.</span></span> <span data-ttu-id="db736-223">호스트 항목이 `WSMan:\localhost\Client` 노드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-223">The TrustedHost item is in the `WSMan:\localhost\Client` node.</span></span>

<span data-ttu-id="db736-224">컴퓨터에서 Administrators 그룹의 구성원 에게만 컴퓨터의 신뢰할 수 있는 호스트 목록을 변경할 수 있는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-224">Only members of the Administrators group on the computer have permission to change the list of trusted hosts on the computer.</span></span>

<span data-ttu-id="db736-225">주의: TrustedHosts 항목에 대해 설정한 값은 컴퓨터의 모든 사용자에 게 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db736-225">Caution: The value that you set for the TrustedHosts item affects all users of the computer.</span></span>

<span data-ttu-id="db736-226">신뢰할 수 있는 호스트 목록을 보려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-226">To view the list of trusted hosts, use the following command:</span></span>

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

<span data-ttu-id="db736-227">또한 `Set-Location` cmdlet (alias = cd)을 사용 하 여 WSMan: 드라이브에서 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-227">You can also use the `Set-Location` cmdlet (alias = cd) to navigate though the WSMan: drive to the location.</span></span> <span data-ttu-id="db736-228">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="db736-228">For example:</span></span>

```powershell
cd WSMan:\localhost\Client; dir
```

<span data-ttu-id="db736-229">모든 컴퓨터를 신뢰할 수 있는 호스트 목록에 추가 하려면 다음 명령을 사용 합니다 .이 명령을 사용 하면 컴퓨터 이름에 \* (모두) 값이 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-229">To add all computers to the list of trusted hosts, use the following command, which places a value of \* (all) in the ComputerName</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

<span data-ttu-id="db736-230">와일드 카드 문자 ()를 사용 `*` 하 여 특정 도메인의 모든 컴퓨터를 신뢰할 수 있는 호스트 목록에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-230">You can also use a wildcard character (`*`) to add all computers in a particular domain to the list of trusted hosts.</span></span> <span data-ttu-id="db736-231">예를 들어 다음 명령은 Fabrikam 도메인의 모든 컴퓨터를 신뢰할 수 있는 호스트 목록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-231">For example, the following command adds all of the computers in the Fabrikam domain to the list of trusted hosts.</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

<span data-ttu-id="db736-232">특정 컴퓨터의 이름을 신뢰할 수 있는 호스트 목록에 추가 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-232">To add the names of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

<span data-ttu-id="db736-233">각 값 `<ComputerName>` 의 형식은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-233">where each value `<ComputerName>` must have the following format:</span></span>

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

<span data-ttu-id="db736-234">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="db736-234">For example:</span></span>

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

<span data-ttu-id="db736-235">컴퓨터 이름을 신뢰할 수 있는 호스트의 기존 목록에 추가 하려면 먼저 현재 값을 변수에 저장 한 다음 현재 값과 새 값을 포함 하는 쉼표로 구분 된 목록으로 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-235">To add a computer name to an existing list of trusted hosts, first save the current value in a variable, and then set the value to a comma-separated list that includes the current and new values.</span></span>

<span data-ttu-id="db736-236">예를 들어 신뢰할 수 있는 호스트의 기존 목록에 Server01 컴퓨터를 추가 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-236">For example, to add the Server01 computer to an existing list of trusted hosts, use the following command</span></span>

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

<span data-ttu-id="db736-237">특정 컴퓨터의 IP 주소를 신뢰할 수 있는 호스트 목록에 추가 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-237">To add the IP addresses of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

<span data-ttu-id="db736-238">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="db736-238">For example:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

<span data-ttu-id="db736-239">원격 컴퓨터의 TrustedHosts 목록에 컴퓨터를 추가 하려면 cmdlet을 사용 하 여 `Connect-WSMan` 원격 컴퓨터의 노드를 로컬 컴퓨터의 WSMan: 드라이브에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-239">To add a computer to the TrustedHosts list of a remote computer, use the `Connect-WSMan` cmdlet to add a node for the remote computer to the WSMan: drive on the local computer.</span></span> <span data-ttu-id="db736-240">그런 다음 `Set-Item` 명령을 사용 하 여 컴퓨터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-240">Then use a `Set-Item` command to add the computer.</span></span>

<span data-ttu-id="db736-241">Cmdlet에 대 한 자세한 내용은 `Connect-WSMan` [연결-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-241">For more information about the `Connect-WSMan` cmdlet, see [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span>

## <a name="troubleshooting-computer-configuration-issues"></a><span data-ttu-id="db736-242">컴퓨터 구성 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db736-242">Troubleshooting computer configuration issues</span></span>

<span data-ttu-id="db736-243">이 섹션에서는 컴퓨터, 도메인 또는 엔터프라이즈의 특정 구성과 관련 된 원격 문제에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-243">This section discusses remoting problems that are related to particular configurations of a computer, domain, or enterprise.</span></span>

### <a name="how-to-configure-remoting-on-alternate-ports"></a><span data-ttu-id="db736-244">대체 포트에서 원격 기능을 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-244">How to configure remoting on alternate ports</span></span>

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="db736-245">PowerShell remoting은 기본적으로 포트 80를 HTTP 전송에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-245">PowerShell remoting uses port 80 for HTTP transport by default.</span></span> <span data-ttu-id="db736-246">사용자가 원격 명령에서 **Connectionuri** 또는 **포트** 매개 변수를 지정 하지 않을 때마다 기본 포트가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-246">The default port is used whenever the user does not specify the **ConnectionURI** or **Port** parameters in a remote command.</span></span>

<span data-ttu-id="db736-247">PowerShell에서 사용 하는 기본 포트를 변경 하려면 `Set-Item` WSMan: 드라이브에서 cmdlet을 사용 하 여 수신기 리프 노드의 포트 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-247">To change the default port that PowerShell uses, use `Set-Item` cmdlet in the WSMan: drive to change the Port value in the listener leaf node.</span></span>

<span data-ttu-id="db736-248">예를 들어 다음 명령은 기본 포트를 8080로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-248">For example, the following command changes the default port to 8080.</span></span>

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a><span data-ttu-id="db736-249">프록시 서버를 사용 하 여 원격을 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-249">How to configure remoting with a proxy server</span></span>

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

<span data-ttu-id="db736-250">PowerShell remoting은 HTTP 프로토콜을 사용 하므로 HTTP 프록시 설정의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-250">Because PowerShell remoting uses the HTTP protocol, it is affected by HTTP proxy settings.</span></span> <span data-ttu-id="db736-251">프록시 서버가 있는 기업은 사용자가 PowerShell 원격 컴퓨터에 직접 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-251">In enterprises that have proxy servers, users cannot access a PowerShell remote computer directly.</span></span>

<span data-ttu-id="db736-252">이 문제를 해결 하려면 원격 명령의 프록시 설정 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-252">To resolve this problem, use proxy setting options in your remote command.</span></span> <span data-ttu-id="db736-253">다음 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-253">The following settings are available:</span></span>

- <span data-ttu-id="db736-254">System.management.automation.remoting.proxyaccesstype</span><span class="sxs-lookup"><span data-stu-id="db736-254">ProxyAccessType</span></span>
- <span data-ttu-id="db736-255">ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="db736-255">ProxyAuthentication</span></span>
- <span data-ttu-id="db736-256">ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="db736-256">ProxyCredential</span></span>

<span data-ttu-id="db736-257">특정 명령에 대해 이러한 옵션을 설정 하려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="db736-257">To set these options for a particular command, use the following procedure:</span></span>

1. <span data-ttu-id="db736-258">Cmdlet의 **system.management.automation.remoting.proxyaccesstype** , **Proxyauthentication** 및 **ProxyCredential** 매개 변수를 사용 `New-PSSessionOption` 하 여 엔터프라이즈에 대 한 프록시 설정을 사용 하 여 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-258">Use the **ProxyAccessType** , **ProxyAuthentication** , and **ProxyCredential** parameters of the `New-PSSessionOption` cmdlet to create a session option object with the proxy settings for your enterprise.</span></span> <span data-ttu-id="db736-259">옵션 개체는 변수를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-259">Save the option object is a variable.</span></span>

1. <span data-ttu-id="db736-260">Option 개체를 포함 하는 변수를, 또는 명령의 **sessionoption** 매개 변수 값으로 사용 `New-PSSession` `Enter-PSSession` `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-260">Use the variable that contains the option object as the value of the **SessionOption** parameter of a `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` command.</span></span>

<span data-ttu-id="db736-261">예를 들어 다음 명령은 프록시 세션 옵션을 사용 하 여 세션 옵션 개체를 만든 다음 개체를 사용 하 여 원격 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-261">For example, the following command creates a session option object with proxy session options and then uses the object to create a remote session.</span></span>

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

<span data-ttu-id="db736-262">Cmdlet에 대 한 자세한 내용은 `New-PSSessionOption` [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-262">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="db736-263">현재 세션의 모든 원격 명령에 대해 이러한 옵션을 설정 하려면 `New-PSSessionOption` 기본 설정 변수 값에 생성 되는 option 개체를 사용 `$PSSessionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-263">To set these options for all remote commands in the current session, use the option object that `New-PSSessionOption` creates in the value of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="db736-264">자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-264">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="db736-265">모든 원격 명령에 대 한 이러한 옵션을 로컬 컴퓨터의 모든 PowerShell 세션에 설정 하려면 `$PSSessionOption` 기본 설정 변수를 powershell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-265">To set these options for all remote commands all PowerShell sessions on the local computer, add the `$PSSessionOption` preference variable to your PowerShell profile.</span></span> <span data-ttu-id="db736-266">PowerShell 프로필에 대 한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-266">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a><span data-ttu-id="db736-267">64 비트 컴퓨터에서 32 비트 세션을 검색 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-267">How to detect a 32-bit session on a 64-bit computer</span></span>

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="db736-268">원격 컴퓨터에서 64 비트 버전의 Windows를 실행 중이 고 원격 명령이 32 비트 세션 구성을 사용 하는 경우 (예: Microsoft.powershell32 Windows 원격 관리 (WinRM) WOW64 프로세스를 로드 하 고 Windows에서 디렉터리에 대 한 모든 참조를 디렉터리로 자동으로 리디렉션합니다 `$env:Windir\System32` `$env:Windir\SysWOW64` .</span><span class="sxs-lookup"><span data-stu-id="db736-268">If the remote computer is running a 64-bit version of Windows, and the remote command is using a 32-bit session configuration, such as Microsoft.PowerShell32, Windows Remote Management (WinRM) loads a WOW64 process and Windows automatically redirects all references to the `$env:Windir\System32` directory to the `$env:Windir\SysWOW64` directory.</span></span>

<span data-ttu-id="db736-269">결과적으로, System32 디렉터리에 해당 하는 도구를 사용 하려고 할 때 (예:) `Defrag.exe` 디렉터리에서 도구를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-269">As a result, if you try to use tools in the System32 directory that do not have counterparts in the SysWow64 directory, such as `Defrag.exe`, the tools cannot be found in the directory.</span></span>

<span data-ttu-id="db736-270">세션에 사용 되는 프로세서 아키텍처를 찾으려면 **PROCESSOR_ARCHITECTURE** 환경 변수의 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-270">To find the processor architecture that is being used in the session, use the value of the **PROCESSOR_ARCHITECTURE** environment variable.</span></span> <span data-ttu-id="db736-271">다음 명령은 변수에서 세션의 프로세서 아키텍처를 찾습니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="db736-271">The following command finds the processor architecture of the session in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

<span data-ttu-id="db736-272">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-272">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="troubleshooting-policy-and-preference-issues"></a><span data-ttu-id="db736-273">정책 및 기본 설정 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db736-273">Troubleshooting policy and preference issues</span></span>

<span data-ttu-id="db736-274">이 섹션에서는 로컬 및 원격 컴퓨터에 설정 된 정책 및 기본 설정과 관련 된 원격 문제에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-274">This section discusses remoting problems that are related to policies and preferences set on the local and remote computers.</span></span>

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a><span data-ttu-id="db736-275">Import-PSSession 및 Import-Module에 대 한 실행 정책을 변경 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-275">How to change the execution policy for Import-PSSession and Import-Module</span></span>

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

<span data-ttu-id="db736-276">`Import-PSSession`및 `Export-PSSession` cmdlet은 서명 되지 않은 스크립트 파일 및 형식 지정 파일을 포함 하는 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-276">The `Import-PSSession` and `Export-PSSession` cmdlets create modules that contains unsigned script files and formatting files.</span></span>

<span data-ttu-id="db736-277">또는를 사용 하 여 이러한 cmdlet에서 만든 모듈을 가져오려면 `Import-PSSession` `Import-Module` 현재 세션의 실행 정책을 제한 하거나 AllSigned 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-277">To import the modules that are created by these cmdlets, either by using `Import-PSSession` or `Import-Module`, the execution policy in the current session cannot be Restricted or AllSigned.</span></span> <span data-ttu-id="db736-278">PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-278">For information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="db736-279">레지스트리에 설정 된 로컬 컴퓨터에 대 한 실행 정책을 변경 하지 않고 모듈을 가져오려면의 **Scope** 매개 변수를 사용 `Set-ExecutionPolicy` 하 여 단일 프로세스에 대 한 덜 제한적인 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-279">To import the modules without changing the execution policy for the local computer that is set in the registry, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>

<span data-ttu-id="db736-280">예를 들어 다음 명령은 실행 정책으로 프로세스를 시작 합니다 `RemoteSigned` .</span><span class="sxs-lookup"><span data-stu-id="db736-280">For example, the following command starts a process with the `RemoteSigned` execution policy.</span></span> <span data-ttu-id="db736-281">실행 정책 변경 내용은 현재 프로세스에만 영향을 미치고 PowerShell **set-executionpolicy** 레지스트리 설정을 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-281">The execution policy change affects only the current process and does not change the PowerShell **ExecutionPolicy** registry setting.</span></span>

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="db736-282">의 **set-executionpolicy** 매개 변수를 사용 하 여 `PowerShell.exe` 덜 제한적인 실행 정책으로 단일 세션을 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-282">You can also use the **ExecutionPolicy** parameter of `PowerShell.exe` to start a single session with a less restrictive execution policy.</span></span>

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="db736-283">실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-283">For more information about execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span> <span data-ttu-id="db736-284">자세한 내용을 보려면 `PowerShell.exe -?`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="db736-284">For more information, type `PowerShell.exe -?`.</span></span>

### <a name="how-to-set-and-change-quotas"></a><span data-ttu-id="db736-285">할당량을 설정 및 변경 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-285">How to set and change quotas</span></span>

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

<span data-ttu-id="db736-286">할당량을 사용 하 여 로컬 컴퓨터와 원격 컴퓨터를 과도 한 리소스 사용 (예를 들어, 우발적인 및 악성) 으로부터 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-286">You can use quotas to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span>

<span data-ttu-id="db736-287">다음 할당량은 기본 구성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-287">The following quotas are available in the basic configuration.</span></span>

- <span data-ttu-id="db736-288">Wsman 공급자 (WSMan:) 노드의 **MaxEnvelopeSizeKB** 및 **maxproviderrequests** 설정, 노드의 `WSMan:<ComputerName>` **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** 및 **MaxConnections** 설정과 같은 몇 가지 할당량 설정을 제공 합니다 `WSMan:<ComputerName>\Service` .</span><span class="sxs-lookup"><span data-stu-id="db736-288">The WSMan provider (WSMan:) provides several quota settings, such as the **MaxEnvelopeSizeKB** and **MaxProviderRequests** settings in the `WSMan:<ComputerName>` node and the **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** , and **MaxConnections** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="db736-289">Cmdlet의 **MaximumReceivedDataSizePerCommand** 및 **MaximumReceivedObjectSize** 매개 변수와 `New-PSSessionOption` 기본 설정 변수를 사용 하 여 로컬 컴퓨터를 보호할 수 있습니다 `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="db736-289">You can protect the local computer by using the **MaximumReceivedDataSizePerCommand** and **MaximumReceivedObjectSize** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="db736-290">Cmdlet의 **MaximumReceivedDataSizePerCommandMB** 및 **MaximumReceivedObjectSizeMB** 매개 변수를 사용 하는 등의 방법으로 세션 구성에 제한을 추가 하 여 원격 컴퓨터를 보호할 수 있습니다 `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="db736-290">You can protect the remote computer by adding restrictions to the session configurations, such as by using the **MaximumReceivedDataSizePerCommandMB** and **MaximumReceivedObjectSizeMB** parameters of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="db736-291">할당량이 명령과 충돌 하는 경우 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-291">When quotas conflict with a command, PowerShell generates an error.</span></span>

<span data-ttu-id="db736-292">이 오류를 해결 하려면 할당량을 준수 하도록 원격 명령을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-292">To resolve the error, change the remote command to comply with the quota.</span></span> <span data-ttu-id="db736-293">또는 할당량의 원본을 확인 하 고 할당량을 늘려 명령이 완료 될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-293">Or, determine the source of the quota, and then increase the quota to allow the command to complete.</span></span>

<span data-ttu-id="db736-294">예를 들어 다음 명령은 원격 컴퓨터의 Microsoft PowerShell 세션 구성에 있는 개체 크기 할당량을 10mb (기본값)에서 11mb로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="db736-294">For example, the following command increases the object size quota in the Microsoft.PowerShell session configuration on the remote computer from 10 MB (the default value) to 11 MB.</span></span>

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

<span data-ttu-id="db736-295">Cmdlet에 대 한 자세한 내용은 `New-PSSessionOption` 을 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="db736-295">For more information about the `New-PSSessionOption` cmdlet, see `New-PSSessionOption`.</span></span>

<span data-ttu-id="db736-296">WS-Management 할당량에 대 한 자세한 내용은 [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-296">For more information about the WS-Management quotas, see [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span></span>

### <a name="how-to-resolve-timeout-errors"></a><span data-ttu-id="db736-297">시간 제한 오류를 해결 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-297">How to resolve timeout errors</span></span>

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

<span data-ttu-id="db736-298">제한 시간을 사용 하 여 로컬 컴퓨터와 원격 컴퓨터를 과도 하 게 사용 하는 컴퓨터와 악의적인 리소스를 사용 하지 않도록 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-298">You can use timeouts to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span> <span data-ttu-id="db736-299">로컬 및 원격 컴퓨터 모두에 시간 초과가 설정 된 경우 PowerShell에서 가장 짧은 시간 제한 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-299">When timeouts are set on both the local and remote computer, PowerShell uses the shortest timeout settings.</span></span>

<span data-ttu-id="db736-300">다음 시간 제한은 기본 구성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-300">The following timeouts are available in the basic configuration.</span></span>

- <span data-ttu-id="db736-301">Wsman 공급자 (WSMan:) 노드의 **Maxtimeoutms** 설정, 노드의 `WSMan:<ComputerName>` **Enumerationtimeoutms** 및 **MaxPacketRetrievalTimeSeconds** 설정과 같은 여러 클라이언트 쪽 및 서비스 쪽 제한 시간 설정을 제공 합니다 `WSMan:<ComputerName>\Service` .</span><span class="sxs-lookup"><span data-stu-id="db736-301">The WSMan provider (WSMan:) provides several client-side and service-side timeout settings, such as the **MaxTimeoutms** setting in the `WSMan:<ComputerName>` node and the **EnumerationTimeoutms** and **MaxPacketRetrievalTimeSeconds** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="db736-302">Cmdlet의 **canceltimeout** , **IdleTimeout** , **OpenTimeout** 및 **operationtimeout** 매개 변수와 `New-PSSessionOption` `$PSSessionOption` 기본 설정 변수를 사용 하 여 로컬 컴퓨터를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-302">You can protect the local computer by using the **CancelTimeout** , **IdleTimeout** , **OpenTimeout** , and **OperationTimeout** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="db736-303">세션에 대 한 세션 구성에서 프로그래밍 방식으로 시간 제한 값을 설정 하 여 원격 컴퓨터를 보호할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-303">You can also protect the remote computer by setting timeout values programmatically in the session configuration for the session.</span></span>

<span data-ttu-id="db736-304">시간 제한 값으로 작업이 완료 되는 것을 허용 하지 않으면 PowerShell에서 작업을 종료 하 고 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-304">When a timeout value does not permit a operation to complete, PowerShell terminates the operation and generates an error.</span></span>

<span data-ttu-id="db736-305">오류를 해결 하려면 시간 제한 간격 내에 명령을 완료로 변경 하거나 시간 제한의 원본을 확인 하 고 제한 시간 간격을 늘려 명령이 완료 될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-305">To resolve the error, change the command to complete within the timeout interval or determine the source of the timeout limit and increase the timeout interval to allow the command to complete.</span></span>

<span data-ttu-id="db736-306">예를 들어 다음 명령은 cmdlet을 사용 `New-PSSessionOption` 하 여 **operationtimeout** 값이 4 분 (밀리초) 인 세션 옵션 개체를 만든 다음 세션 옵션 개체를 사용 하 여 원격 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db736-306">For example, the following commands use the `New-PSSessionOption` cmdlet to create a session option object with an **OperationTimeout** value of 4 minutes (in MS) and then use the session option object to create a remote session.</span></span>

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

<span data-ttu-id="db736-307">WS-Management 제한 시간에 대 한 자세한 내용은 WSMan 공급자 (유형)에 대 한 도움말 항목을 참조 하십시오 `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="db736-307">For more information about the WS-Management timeouts, see the Help topic for the WSMan provider (type `Get-Help WSMan`).</span></span>

<span data-ttu-id="db736-308">Cmdlet에 대 한 자세한 내용은 `New-PSSessionOption` [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-308">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="troubleshooting-unresponsive-behavior"></a><span data-ttu-id="db736-309">응답 하지 않는 동작 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db736-309">Troubleshooting unresponsive behavior</span></span>

<span data-ttu-id="db736-310">이 섹션에서는 명령이 완료 되지 않도록 하 고 PowerShell 프롬프트의 반환을 방지 하거나 지연 하는 원격 문제에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-310">This section discusses remoting problems that prevent a command from completing and prevent or delay the return of the PowerShell prompt.</span></span>

### <a name="how-to-interrupt-a-command"></a><span data-ttu-id="db736-311">명령을 중단 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-311">How to interrupt a command</span></span>

<span data-ttu-id="db736-312">사용자 인터페이스가 있는 프로그램, 입력을 요청 하는 콘솔 응용 프로그램, Win32 콘솔 API를 사용 하는 콘솔 응용 프로그램 등의 일부 네이티브 Windows 프로그램은 PowerShell 원격 호스트에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-312">Some native Windows programs, such as programs with a user interface, console applications that prompt for input, and console applications that use the Win32 console API, do not work correctly in the PowerShell remote host.</span></span>

<span data-ttu-id="db736-313">이러한 프로그램을 사용 하는 경우 출력 없음, 부분 출력 또는 완료 되지 않은 원격 명령과 같은 예기치 않은 동작이 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-313">When you use these programs, you might see unexpected behavior, such as no output, partial output, or a remote command that does not complete.</span></span>

<span data-ttu-id="db736-314">응답 하지 않는 프로그램을 종료 하려면 <kbd>CTRL</kbd> + <kbd>C</kbd>를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-314">To end an unresponsive program, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="db736-315">보고 되었을 수 있는 모든 오류를 보려면 `$error` 로컬 호스트와 원격 세션에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-315">To view any errors that might have been reported, type `$error` in the local host and the remote session.</span></span>

## <a name="how-to-recover-from-an-operation-failure"></a><span data-ttu-id="db736-316">작업 오류에서 복구 하는 방법</span><span class="sxs-lookup"><span data-stu-id="db736-316">How to recover from an operation failure</span></span>

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

<span data-ttu-id="db736-317">작업이 완료 되기 전에 종료 되 면이 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db736-317">This error is returned when an operation is terminated before it completes.</span></span>
<span data-ttu-id="db736-318">일반적으로 다른 WinRM 작업이 진행 되는 동안 WinRM 서비스를 중지 하거나 다시 시작할 때 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-318">Typically, it occurs when the WinRM service stops or restarts while other WinRM operations are in progress.</span></span>

<span data-ttu-id="db736-319">이 문제를 해결 하려면 WinRM 서비스가 실행 중인지 확인 하 고 명령을 다시 시도 하십시오.</span><span class="sxs-lookup"><span data-stu-id="db736-319">To resolve this issue, verify that the WinRM service is running and try the command again.</span></span>

1. <span data-ttu-id="db736-320">**관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-320">Start PowerShell with the **Run as administrator** option.</span></span>
1. <span data-ttu-id="db736-321">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-321">Run the following command:</span></span>

   `Start-Service WinRM`

1. <span data-ttu-id="db736-322">오류를 생성 한 명령을 다시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="db736-322">Re-run the command that generated the error.</span></span>

## <a name="linux-and-macos-limitations"></a><span data-ttu-id="db736-323">Linux 및 macOS 제한 사항</span><span class="sxs-lookup"><span data-stu-id="db736-323">Linux and macOS limitations</span></span>

### <a name="authentication"></a><span data-ttu-id="db736-324">인증</span><span class="sxs-lookup"><span data-stu-id="db736-324">Authentication</span></span>

<span data-ttu-id="db736-325">MacOS에서 기본 인증만 작동 하 고 다른 인증 체계를 사용 하려고 하면 프로세스가 충돌을 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db736-325">Only basic authentication works on macOS and attempting to use other authentication schemes may result in the process crashing.</span></span>

<span data-ttu-id="db736-326">[OMI 인증](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) 지침을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db736-326">Please see the [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="db736-327">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db736-327">SEE ALSO</span></span>

[<span data-ttu-id="db736-328">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="db736-328">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[<span data-ttu-id="db736-329">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="db736-329">Export-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[<span data-ttu-id="db736-330">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="db736-330">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="db736-331">about_Remote</span><span class="sxs-lookup"><span data-stu-id="db736-331">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="db736-332">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="db736-332">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="db736-333">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="db736-333">about_Remote_Variables</span></span>](about_Remote_Variables.md)
