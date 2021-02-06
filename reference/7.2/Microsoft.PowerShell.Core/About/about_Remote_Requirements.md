---
description: PowerShell에서 원격 명령을 실행 하기 위한 시스템 요구 사항 및 구성 요구 사항에 대해 설명 합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 4a994ded51195e5932af7bb4af0b2e6fb3a67857
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603256"
---
# <a name="about-remote-requirements"></a><span data-ttu-id="7acea-103">원격 요구 사항 정보</span><span class="sxs-lookup"><span data-stu-id="7acea-103">About Remote Requirements</span></span>

## <a name="short-description"></a><span data-ttu-id="7acea-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="7acea-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7acea-105">PowerShell에서 원격 명령을 실행 하기 위한 시스템 요구 사항 및 구성 요구 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-105">Describes the system requirements and configuration requirements for running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7acea-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="7acea-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="7acea-107">이 항목에서는 원격 연결을 설정 하 고 PowerShell에서 원격 명령을 실행 하기 위한 시스템 요구 사항, 사용자 요구 사항 및 리소스 요구 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-107">This topic describes the system requirements, user requirements, and resource requirements for establishing remote connections and running remote commands in PowerShell.</span></span> <span data-ttu-id="7acea-108">또한 원격 작업을 구성 하는 방법에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-108">It also provides instructions for configuring remote operations.</span></span>

<span data-ttu-id="7acea-109">참고: 대부분의 cmdlet (Get-wmiobject, get-Process, Get-EventLog 및 Get-WinEvent cmdlet 포함)은 Microsoft .NET Framework 메서드를 사용 하 여 개체를 검색 함으로써 원격 컴퓨터에서 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-109">Note: Many cmdlets (including the Get-Service, Get-Process, Get-WMIObject, Get-EventLog, and Get-WinEvent cmdlets) get objects from remote computers by using Microsoft .NET Framework methods to retrieve the objects.</span></span> <span data-ttu-id="7acea-110">PowerShell 원격 인프라를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-110">They do not use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="7acea-111">이 문서의 요구 사항은 이러한 cmdlet에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-111">The requirements in this document do not apply to these cmdlets.</span></span>

<span data-ttu-id="7acea-112">ComputerName 매개 변수가 있지만 PowerShell 원격을 사용 하지 않는 cmdlet을 찾으려면 cmdlet의 ComputerName 매개 변수에 대 한 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7acea-112">To find the cmdlets that have a ComputerName parameter but do not use PowerShell remoting, read the description of the ComputerName parameter of the cmdlets.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="7acea-113">시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7acea-113">SYSTEM REQUIREMENTS</span></span>

<span data-ttu-id="7acea-114">Windows PowerShell 3.0에서 원격 세션을 실행 하려면 로컬 컴퓨터와 원격 컴퓨터에 다음이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-114">To run remote sessions on Windows PowerShell 3.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="7acea-115">Windows PowerShell 3.0 이상</span><span class="sxs-lookup"><span data-stu-id="7acea-115">Windows PowerShell 3.0 or later</span></span>
- <span data-ttu-id="7acea-116">Microsoft .NET Framework 4 이상</span><span class="sxs-lookup"><span data-stu-id="7acea-116">The Microsoft .NET Framework 4 or later</span></span>
- <span data-ttu-id="7acea-117">Windows 원격 관리 3.0</span><span class="sxs-lookup"><span data-stu-id="7acea-117">Windows Remote Management 3.0</span></span>

<span data-ttu-id="7acea-118">Windows PowerShell 2.0에서 원격 세션을 실행 하려면 로컬 컴퓨터와 원격 컴퓨터에 다음이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-118">To run remote sessions on Windows PowerShell 2.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="7acea-119">Windows PowerShell 2.0 이상</span><span class="sxs-lookup"><span data-stu-id="7acea-119">Windows PowerShell 2.0 or later</span></span>
- <span data-ttu-id="7acea-120">Microsoft .NET Framework 2.0 이상</span><span class="sxs-lookup"><span data-stu-id="7acea-120">The Microsoft .NET Framework 2.0 or later</span></span>
- <span data-ttu-id="7acea-121">Windows 원격 관리 2.0</span><span class="sxs-lookup"><span data-stu-id="7acea-121">Windows Remote Management 2.0</span></span>

<span data-ttu-id="7acea-122">Windows PowerShell 2.0 및 Windows PowerShell 3.0을 실행 하는 컴퓨터 간에 원격 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-122">You can create remote sessions between computers running Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="7acea-123">그러나 Windows PowerShell 3.0 에서만 실행 되는 기능 (예: 세션 연결을 끊고 다시 연결 하는 기능)은 두 컴퓨터에서 모두 Windows PowerShell 3.0을 실행 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-123">However, features that run only on Windows PowerShell 3.0, such as the ability to disconnect and reconnect to sessions, are available only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="7acea-124">설치 된 PowerShell 버전의 버전 번호를 찾으려면 $PSVersionTable 자동 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-124">To find the version number of an installed version of PowerShell, use the $PSVersionTable automatic variable.</span></span>

<span data-ttu-id="7acea-125">Windows 원격 관리 (WinRM) 3.0 및 Microsoft .NET Framework 4는 windows 8, Windows Server 2012 및 최신 버전의 Windows 운영 체제에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-125">Windows Remote Management (WinRM) 3.0 and Microsoft .NET Framework 4 are included in Windows 8, Windows Server 2012, and newer releases of the Windows operating system.</span></span> <span data-ttu-id="7acea-126">WinRM 3.0은 이전 운영 체제용 Windows Management Framework 3.0에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-126">WinRM 3.0 is included in Windows Management Framework 3.0 for older operating systems.</span></span> <span data-ttu-id="7acea-127">컴퓨터에 필요한 WinRM 또는 Microsoft .NET Framework 버전이 없는 경우 설치에 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-127">If the computer does not have the required version of WinRM or the Microsoft .NET Framework, the installation fails.</span></span>

## <a name="user-permissions"></a><span data-ttu-id="7acea-128">사용자 권한</span><span class="sxs-lookup"><span data-stu-id="7acea-128">USER PERMISSIONS</span></span>

<span data-ttu-id="7acea-129">원격 세션을 만들고 원격 명령을 실행 하려면 기본적으로 현재 사용자가 원격 컴퓨터에서 Administrators 그룹의 구성원 이거나 관리자의 자격 증명을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-129">To create remote sessions and run remote commands, by default, the current user must be a member of the Administrators group on the remote computer or provide the credentials of an administrator.</span></span> <span data-ttu-id="7acea-130">그러지 않으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-130">Otherwise, the command fails.</span></span>

<span data-ttu-id="7acea-131">세션을 만들고 원격 컴퓨터 (또는 로컬 컴퓨터의 원격 세션)에서 명령을 실행 하는 데 필요한 권한은 세션이 연결 되는 원격 컴퓨터에서 세션 구성 ("끝점"이 라고도 함)에 의해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-131">The permissions required to create sessions and run commands on a remote computer (or in a remote session on the local computer) are established by the session configuration (also known as an "endpoint") on the remote computer to which the session connects.</span></span> <span data-ttu-id="7acea-132">특히 세션 구성에 대 한 보안 설명자는 세션 구성에 대 한 액세스 권한이 있는 사용자와 연결 하는 데 사용할 수 있는 사람을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-132">Specifically, the security descriptor on the session configuration determines who has access to the session configuration and who can use it to connect.</span></span>

<span data-ttu-id="7acea-133">기본 세션 구성의 보안 설명자 (Microsoft.powershell32, microsoft. PowerShell, Microsoft. powershell)는 Administrators 그룹의 구성원 에게만 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-133">The security descriptors on the default session configurations, Microsoft.PowerShell, Microsoft.PowerShell32, and Microsoft.PowerShell.Workflow, allow access only to members of the Administrators group.</span></span>

<span data-ttu-id="7acea-134">현재 사용자에 게 세션 구성을 사용할 수 있는 권한이 없는 경우 명령을 실행 (임시 세션 사용) 하거나 원격 컴퓨터에서 영구 세션을 만드는 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-134">If the current user doesn't have permission to use the session configuration, the command to run a command (which uses a temporary session) or create a persistent session on the remote computer fails.</span></span> <span data-ttu-id="7acea-135">사용자는 세션을 만드는 cmdlet의 ConfigurationName 매개 변수를 사용 하 여 다른 세션 구성을 선택할 수 있습니다 (사용할 수 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="7acea-135">The user can use the ConfigurationName parameter of cmdlets that create sessions to select a different session configuration, if one is available.</span></span>

<span data-ttu-id="7acea-136">컴퓨터에서 Administrators 그룹의 구성원은 기본 세션 구성의 보안 설명자를 변경 하 고 다른 보안 설명자를 사용 하 여 새 세션 구성을 만들어 원격으로 컴퓨터에 연결할 수 있는 권한을 가진 사용자를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-136">Members of the Administrators group on a computer can determine who has permission to connect to the computer remotely by changing the security descriptors on the default session configurations and by creating new session configurations with different security descriptors.</span></span>

<span data-ttu-id="7acea-137">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7acea-137">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="windows-network-locations"></a><span data-ttu-id="7acea-138">WINDOWS 네트워크 위치</span><span class="sxs-lookup"><span data-stu-id="7acea-138">WINDOWS NETWORK LOCATIONS</span></span>

<span data-ttu-id="7acea-139">Windows PowerShell 3.0부터 Enable-PSRemoting cmdlet은 개인, 도메인 및 공용 네트워크에서 Windows의 클라이언트 및 서버 버전에 대 한 원격 기능을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-139">Beginning in Windows PowerShell 3.0, the Enable-PSRemoting cmdlet can enable remoting on client and server versions of Windows on private, domain, and public networks.</span></span>

<span data-ttu-id="7acea-140">개인 및 도메인 네트워크가 포함 된 Windows의 서버 버전에서 Enable-PSRemoting cmdlet은 무제한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-140">On server versions of Windows with private and domain networks, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span> <span data-ttu-id="7acea-141">또한 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-141">It also creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="7acea-142">이 로컬 서브넷 방화벽 규칙은 공용 네트워크의 Windows 서버 버전에서 기본적으로 사용 하도록 설정 되지만 Enable-PSRemoting 변경 되거나 삭제 된 경우에는 규칙을 다시 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-142">This local subnet firewall rule is enabled by default on server versions of Windows on public networks, but Enable-PSRemoting reapplies the rule in case it was changed or deleted.</span></span>

<span data-ttu-id="7acea-143">개인 및 도메인 네트워크가 포함 된 Windows 클라이언트 버전에서 기본적으로 Enable-PSRemoting cmdlet은 무제한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-143">On client versions of Windows with private and domain networks, by default, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span>

<span data-ttu-id="7acea-144">공용 네트워크를 사용 하 여 Windows 클라이언트 버전에서 원격 기능을 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet의 SkipNetworkProfileCheck 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-144">To enable remoting on client versions of Windows with public networks, use the SkipNetworkProfileCheck parameter of the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="7acea-145">동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-145">It creates a firewall rule that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="7acea-146">공용 네트워크에 대 한 로컬 서브넷 제한을 제거 하 고 Windows의 클라이언트 및 서버 버전의 모든 위치에서 원격 액세스를 허용 하려면 NetSecurity 모듈의 Set-NetFirewallRule cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-146">To remove the local subnet restriction on public networks and allow remote access from all locations on client and server versions of Windows, use the Set-NetFirewallRule cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="7acea-147">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-147">Run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="7acea-148">Windows PowerShell 2.0에서는 Windows server 버전의 Enable-PSRemoting 모든 네트워크에서 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-148">In Windows PowerShell 2.0, on server versions of Windows, Enable-PSRemoting creates firewall rules that permit remote access on all networks.</span></span>

<span data-ttu-id="7acea-149">Windows PowerShell 2.0의 클라이언트 버전 Windows에서 Enable-PSRemoting 개인 및 도메인 네트워크에만 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-149">In Windows PowerShell 2.0, on client versions of Windows, Enable-PSRemoting creates firewall rules only on private and domain networks.</span></span> <span data-ttu-id="7acea-150">네트워크 위치가 공용 인 경우 Enable-PSRemoting 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-150">If the network location is public, Enable-PSRemoting fails.</span></span>

## <a name="run-as-administrator"></a><span data-ttu-id="7acea-151">관리자 권한으로 실행</span><span class="sxs-lookup"><span data-stu-id="7acea-151">RUN AS ADMINISTRATOR</span></span>

<span data-ttu-id="7acea-152">다음 원격 작업을 수행 하려면 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-152">Administrator privileges are required for the following remoting operations:</span></span>

- <span data-ttu-id="7acea-153">로컬 컴퓨터에 대 한 원격 연결 설정</span><span class="sxs-lookup"><span data-stu-id="7acea-153">Establishing a remote connection to the local computer.</span></span> <span data-ttu-id="7acea-154">이를 일반적으로 "루프백" 시나리오 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-154">This is commonly known as a "loopback" scenario.</span></span>

- <span data-ttu-id="7acea-155">로컬 컴퓨터의 세션 구성 관리</span><span class="sxs-lookup"><span data-stu-id="7acea-155">Managing session configurations on the local computer.</span></span>

- <span data-ttu-id="7acea-156">로컬 컴퓨터에서 WS-Management 설정 보기 및 변경</span><span class="sxs-lookup"><span data-stu-id="7acea-156">Viewing and changing WS-Management settings on the local computer.</span></span> <span data-ttu-id="7acea-157">다음은 WSMAN: 드라이브의 LocalHost 노드에 있는 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-157">These are the settings in the LocalHost node of the WSMAN: drive.</span></span>

<span data-ttu-id="7acea-158">이러한 작업을 수행 하려면 로컬 컴퓨터에서 Administrators 그룹의 구성원 인 경우에도 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-158">To perform these tasks, you must start PowerShell with the "Run as administrator" option even if you are a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="7acea-159">Windows 7 및 Windows Server 2008 R2에서 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-159">In Windows 7 and in Windows Server 2008 R2, to start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="7acea-160">시작, 모든 프로그램, 보조 프로그램을 차례로 클릭 한 다음 Windows PowerShell 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-160">Click Start, click All Programs, click Accessories, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="7acea-161">Windows PowerShell을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-161">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="7acea-162">"관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 하려면:</span><span class="sxs-lookup"><span data-stu-id="7acea-162">To start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="7acea-163">시작, 모든 프로그램을 차례로 클릭 한 다음 Windows PowerShell 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-163">Click Start, click All Programs, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="7acea-164">Windows PowerShell을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-164">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="7acea-165">"관리자 권한으로 실행" 옵션은 바로 가기를 포함 하 여 Windows PowerShell에 대 한 다른 Windows 탐색기 항목 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-165">The "Run as administrator" option is also available in other Windows Explorer entries for Windows PowerShell, including shortcuts.</span></span> <span data-ttu-id="7acea-166">항목을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 클릭 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-166">Just right-click the item, and then click "Run as administrator".</span></span>

<span data-ttu-id="7acea-167">Cmd.exe와 같은 다른 프로그램에서 Windows PowerShell을 시작 하는 경우 "관리자 권한으로 실행" 옵션을 사용 하 여 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-167">When you start Windows PowerShell from another program such as Cmd.exe, use the "Run as administrator" option to start the program.</span></span>

## <a name="how-to-configure-your-computer-for-remoting"></a><span data-ttu-id="7acea-168">원격 기능을 사용할 수 있도록 컴퓨터를 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="7acea-168">HOW TO CONFIGURE YOUR COMPUTER FOR REMOTING</span></span>

<span data-ttu-id="7acea-169">지원 되는 모든 버전의 Windows를 실행 하는 컴퓨터는 구성 없이 PowerShell에서 원격 연결을 설정 하 고 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-169">Computers running all supported versions of Windows can establish remote connections to and run remote commands in PowerShell without any configuration.</span></span> <span data-ttu-id="7acea-170">그러나 연결을 수신 하 고 사용자가 로컬 및 원격 사용자 관리 PowerShell 세션 ("PSSessions")을 만들고 로컬 컴퓨터에서 명령을 실행 하도록 허용 하려면 컴퓨터에서 PowerShell 원격 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-170">However, to receive connections, and allow users to create local and remote user-managed PowerShell sessions ("PSSessions") and run commands on the local computer, you must enable PowerShell remoting on the computer.</span></span>

<span data-ttu-id="7acea-171">Windows server 2012 이상 버전의 Windows Server는 기본적으로 PowerShell 원격 기능을 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-171">Windows Server 2012 and newer releases of Windows Server are enabled for PowerShell remoting by default.</span></span> <span data-ttu-id="7acea-172">설정이 변경 되 면 Enable-PSRemoting cmdlet을 실행 하 여 기본 설정을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-172">If the settings are changed, you can restore the default settings by running the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="7acea-173">지원 되는 다른 모든 Windows 버전에서 PowerShell 원격을 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-173">On all other supported versions of Windows, you need to run the Enable-PSRemoting cmdlet to enable PowerShell remoting.</span></span>

<span data-ttu-id="7acea-174">PowerShell의 원격 기능은 WS-MANAGEMENT (Web Services for Management) 프로토콜의 Microsoft 구현인 WinRM 서비스에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-174">The remoting features of PowerShell are supported by the WinRM service, which is the Microsoft implementation of the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="7acea-175">PowerShell 원격을 사용 하도록 설정 하는 경우 WS-Management의 기본 구성을 변경 하 고 사용자가 WS-MANAGEMENT에 연결할 수 있도록 하는 시스템 구성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-175">When you enable PowerShell remoting, you change the default configuration of WS-Management and add system configuration that allow users to connect to WS-Management.</span></span>

<span data-ttu-id="7acea-176">원격 명령을 받도록 PowerShell을 구성 하려면:</span><span class="sxs-lookup"><span data-stu-id="7acea-176">To configure PowerShell to receive remote commands:</span></span>

1. <span data-ttu-id="7acea-177">"관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-177">Start PowerShell with the "Run as administrator" option.</span></span>
2. <span data-ttu-id="7acea-178">명령 프롬프트에 다음을 입력합니다. `Enable-PSRemoting`</span><span class="sxs-lookup"><span data-stu-id="7acea-178">At the command prompt, type: `Enable-PSRemoting`</span></span>

<span data-ttu-id="7acea-179">원격 서비스가 올바르게 구성 되었는지 확인 하려면 로컬 컴퓨터에서 원격 세션을 만드는 다음 명령과 같은 테스트 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-179">To verify that remoting is configured correctly, run a test command such as the following command, which creates a remote session on the local computer.</span></span>

```powershell
New-PSSession
```

<span data-ttu-id="7acea-180">원격 구성이 올바르게 구성 된 경우이 명령은 로컬 컴퓨터에서 세션을 만들고 세션을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-180">If remoting is configured correctly, the command will create a session on the local computer and return an object that represents the session.</span></span> <span data-ttu-id="7acea-181">출력은 다음 샘플 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-181">The output should resemble the following sample output:</span></span>

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

<span data-ttu-id="7acea-182">명령이 실패 하는 경우 도움이 필요 하면 [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7acea-182">If the command fails, for assistance, see [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span></span>

## <a name="understand-policies"></a><span data-ttu-id="7acea-183">정책 이해</span><span class="sxs-lookup"><span data-stu-id="7acea-183">UNDERSTAND POLICIES</span></span>

<span data-ttu-id="7acea-184">원격으로 작업 하는 경우 로컬 컴퓨터와 원격 컴퓨터에 하나씩 PowerShell의 두 인스턴스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-184">When you work remotely, you use two instances of PowerShell, one on the local computer and one on the remote computer.</span></span> <span data-ttu-id="7acea-185">따라서 작업은 로컬 및 원격 컴퓨터의 Windows 정책 및 PowerShell 정책의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-185">As a result, your work is affected by the Windows policies and the PowerShell policies on the local and remote computers.</span></span>

<span data-ttu-id="7acea-186">일반적으로 연결을 설정할 때와 연결 하기 전에 로컬 컴퓨터의 정책이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-186">In general, before you connect and as you are establishing the connection, the policies on the local computer are in effect.</span></span> <span data-ttu-id="7acea-187">연결을 사용 하는 경우 원격 컴퓨터의 정책이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-187">When you are using the connection, the policies on the remote computer are in effect.</span></span>

## <a name="basic-authentication-limitations-on-linux-and-macos"></a><span data-ttu-id="7acea-188">Linux 및 macOS에 대 한 기본 인증 제한 사항</span><span class="sxs-lookup"><span data-stu-id="7acea-188">Basic Authentication Limitations on Linux and macOS</span></span>

<span data-ttu-id="7acea-189">Linux 또는 macOS 시스템에서 Windows로 연결 하는 경우 HTTP를 통한 기본 인증이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-189">When connecting from a Linux or macOS system to Windows, Basic Authentication over HTTP is not supported.</span></span> <span data-ttu-id="7acea-190">대상 서버에 인증서를 설치 하 여 HTTPS를 통해 기본 인증을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-190">Basic Authentication can be used over HTTPS by installing a certificate on the target server.</span></span> <span data-ttu-id="7acea-191">인증서에는 호스트 이름과 일치 하는 CN 이름이 있어야 하며, 만료 되거나 해지 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-191">The certificate must have a CN name that matches the hostname, is not expired or revoked.</span></span> <span data-ttu-id="7acea-192">자체 서명 된 인증서는 테스트 목적으로 사용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-192">A self-signed certificate may be used for testing purposes.</span></span>

<span data-ttu-id="7acea-193">자세한 내용은 [방법: HTTPS에 대해 WINRM 구성](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7acea-193">See [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) for additional details.</span></span>

<span data-ttu-id="7acea-194">관리자 권한 명령 프롬프트에서 실행 되는 다음 명령을 사용 하 여 Windows에서 설치 된 인증서를 사용 하 여 HTTPS 수신기를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-194">The following command, run from an elevated command prompt, will configure the HTTPS listener on Windows with the installed certificate.</span></span>

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

<span data-ttu-id="7acea-195">Linux 또는 macOS 쪽에서 인증에 대해 기본을 선택 하 고-UseSSl을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-195">On the Linux or macOS side, select Basic for authentication and -UseSSl.</span></span>

> <span data-ttu-id="7acea-196">참고: 도메인 계정에는 기본 인증을 사용할 수 없습니다. 로컬 계정이 필요 하며 계정은 Administrators 그룹에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-196">NOTE: Basic authentication cannot be used with domain accounts; a local account is required and the account must be in the Administrators group.</span></span>

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

<span data-ttu-id="7acea-197">HTTPS를 통한 기본 인증 대신 Negotiate를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-197">An alternative to Basic Authentication over HTTPS is Negotiate.</span></span> <span data-ttu-id="7acea-198">이로 인해 HTTP를 통해 클라이언트와 서버 및 페이로드 간의 NTLM 인증이 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-198">This results in NTLM authentication between the client and server and payload is encrypted over HTTP.</span></span>

<span data-ttu-id="7acea-199">다음은 New-PSSession과 함께 Negotiate를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-199">The following illustrates using Negotiate with New-PSSession:</span></span>

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> <span data-ttu-id="7acea-200">Windows Server에는 기본 제공 관리자 이외의 관리자가 NTLM을 사용 하 여 연결할 수 있도록 하는 추가 레지스트리 설정이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7acea-200">Windows Server requires an additional registry setting to enable administrators, other than the built in administrator, to connect using NTLM.</span></span>
> <span data-ttu-id="7acea-201">[원격 연결에 대 한 인증](/windows/win32/winrm/authentication-for-remote-connections) 에서 인증 협상에서 LocalAccountTokenFilterPolicy 레지스트리 설정을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7acea-201">Refer to the LocalAccountTokenFilterPolicy registry setting under Negotiate Authentication in [Authentication for Remote Connections](/windows/win32/winrm/authentication-for-remote-connections)</span></span>

## <a name="see-also"></a><span data-ttu-id="7acea-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7acea-202">SEE ALSO</span></span>

[<span data-ttu-id="7acea-203">about_Remote</span><span class="sxs-lookup"><span data-stu-id="7acea-203">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="7acea-204">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="7acea-204">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="7acea-205">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="7acea-205">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="7acea-206">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7acea-206">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="7acea-207">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="7acea-207">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="7acea-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7acea-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

