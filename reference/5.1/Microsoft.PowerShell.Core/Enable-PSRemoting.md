---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2020
ms.locfileid: "93218041"
---
# <span data-ttu-id="ac769-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ac769-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="ac769-104">개요</span><span class="sxs-lookup"><span data-stu-id="ac769-104">SYNOPSIS</span></span>
<span data-ttu-id="ac769-105">원격 명령을 받도록 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="ac769-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ac769-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ac769-107">설명</span><span class="sxs-lookup"><span data-stu-id="ac769-107">DESCRIPTION</span></span>

<span data-ttu-id="ac769-108">`Enable-PSRemoting`Cmdlet은 WS-Management 기술을 사용 하 여 전송 된 PowerShell 원격 명령을 받도록 컴퓨터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span>

<span data-ttu-id="ac769-109">Windows Server 2012에서는 PowerShell remoting이 기본적으로 사용 하도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-109">PowerShell remoting is enabled by default on Windows Server 2012.</span></span> <span data-ttu-id="ac769-110">`Enable-PSRemoting`를 사용 하 여 지원 되는 다른 windows 버전에서 PowerShell 원격을 사용 하도록 설정 하 고 Windows Server 2012에서 원격 기능을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting on Windows Server 2012 if it becomes disabled.</span></span>

<span data-ttu-id="ac769-111">명령을 수신 하는 각 컴퓨터에서이 명령을 한 번만 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="ac769-112">명령을 전송 하는 컴퓨터에서는 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="ac769-113">구성에서 수신기를 시작 하기 때문에 필요한 경우에만 실행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-113">Because the configuration starts listeners, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="ac769-114">PowerShell 3.0부터 `Enable-PSRemoting` 이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 Windows 클라이언트 버전에서 powershell 원격 기능을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-114">Beginning in PowerShell 3.0, the `Enable-PSRemoting` cmdlet can enable PowerShell remoting on client versions of Windows when the computer is on a public network.</span></span> <span data-ttu-id="ac769-115">자세한 내용은 **SkipNetworkProfileCheck** 매개 변수에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac769-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="ac769-116">`Enable-PSRemoting`Cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-116">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="ac769-117">다음 작업을 수행 하는 [set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-117">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="ac769-118">WinRM 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-118">Starts the WinRM service.</span></span>
  - <span data-ttu-id="ac769-119">WinRM 서비스의 시작 유형을 자동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-119">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="ac769-120">모든 IP 주소에서 요청을 수락 하는 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-120">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="ac769-121">WS-Management 통신에 대 한 방화벽 예외를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-121">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="ac769-122">아직 등록 되지 않은 경우 **microsoft. powershell** 및 **microsoft 워크플로** 세션 구성을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-122">Registers the **Microsoft.PowerShell** and **Microsoft.PowerShell.Workflow** session configurations, if it they are not already registered.</span></span>
  - <span data-ttu-id="ac769-123">**Microsoft.powershell32** 세션 구성이 아직 등록 되지 않은 경우 64 비트 컴퓨터에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-123">Registers the **Microsoft.PowerShell32** session configuration on 64-bit computers, if it is not already registered.</span></span>
  - <span data-ttu-id="ac769-124">모든 세션 구성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-124">Enables all session configurations.</span></span>
  - <span data-ttu-id="ac769-125">모든 세션 구성의 보안 설명자를 변경 하 여 원격 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-125">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="ac769-126">WinRM 서비스를 다시 시작 하 여 위의 변경 내용이 적용 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-126">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="ac769-127">Windows 플랫폼에서이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-127">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="ac769-128">Linux 또는 MacOS 버전의 PowerShell에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-128">This does not apply to Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="ac769-129">PowerShell 3.0 및 PowerShell 2.0이 모두 있는 시스템에서는 PowerShell 2.0을 사용 하 여 및 cmdlet을 실행 하지 마세요 `Enable-PSRemoting` `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="ac769-129">On systems that have both PowerShell 3.0 and PowerShell 2.0, do not use PowerShell 2.0 to run the `Enable-PSRemoting` and `Disable-PSRemoting` cmdlets.</span></span> <span data-ttu-id="ac769-130">명령이 성공한 것처럼 보일 수 있지만 원격 기능이 올바르게 구성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-130">The commands might appear to succeed, but the remoting is not configured correctly.</span></span> <span data-ttu-id="ac769-131">원격 명령 및 원격 기능을 사용 하거나 사용 하지 않도록 설정 하려고 하면 실패할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-131">Remote commands and later attempts to enable and disable remoting, are likely to fail.</span></span>

## <span data-ttu-id="ac769-132">예제</span><span class="sxs-lookup"><span data-stu-id="ac769-132">EXAMPLES</span></span>

### <span data-ttu-id="ac769-133">예 1: 원격 명령을 받도록 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="ac769-133">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="ac769-134">이 명령은 원격 명령을 수신하도록 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-134">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

### <span data-ttu-id="ac769-135">예 2: 확인 메시지 없이 원격 명령을 받도록 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="ac769-135">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="ac769-136">이 명령은 원격 명령을 수신하도록 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-136">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="ac769-137">**Force** 매개 변수를 사용 하면 사용자 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-137">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

### <span data-ttu-id="ac769-138">예제 3: 클라이언트에서 원격 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="ac769-138">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="ac769-139">이 예제에서는 Windows 운영 체제 클라이언트 버전의 공용 네트워크에서 원격 액세스를 허용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-139">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="ac769-140">방화벽 규칙의 이름은 서로 다른 버전의 Windows에 대해 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-140">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="ac769-141">`Get-NetFirewallRule`규칙 목록을 보려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-141">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="ac769-142">방화벽 규칙을 사용 하도록 설정 하기 전에 규칙의 보안 설정을 확인 하 여 구성이 환경에 적합 한지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-142">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

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

<span data-ttu-id="ac769-143">기본적으로에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에서 원격 액세스를 허용 하는 네트워크 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-143">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="ac769-144">이 명령은 **SkipNetworkProfileCheck** 매개 변수를 사용하여 동일한 로컬 서브넷에 있는 공용 네트워크에서의 원격 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-144">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="ac769-145">명령은 **Force** 매개 변수를 지정 하 여 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-145">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="ac769-146">**SkipNetworkProfileCheck** 매개 변수는 기본적으로 동일한 로컬 서브넷에 있는 공용 네트워크에서의 원격 액세스를 허용 하는 Windows 운영 체제의 서버 버전에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-146">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="ac769-147">`Set-NetFirewallRule` **Netsecurity** 모듈의 cmdlet은 원격 위치의 공용 네트워크에서 원격 액세스를 허용 하는 방화벽 규칙을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-147">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="ac769-148">여기에는 다른 서브넷의 위치가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-148">This includes locations in different subnets.</span></span>

> [!NOTE]
> <span data-ttu-id="ac769-149">방화벽 규칙의 이름은 Windows 버전에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-149">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="ac769-150">Cmdlet을 사용 `Get-NetFirewallRule` 하 여 시스템에 있는 규칙의 이름을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-150">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="ac769-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ac769-151">PARAMETERS</span></span>

### <span data-ttu-id="ac769-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ac769-152">-Confirm</span></span>

<span data-ttu-id="ac769-153">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ac769-154">-Force</span><span class="sxs-lookup"><span data-stu-id="ac769-154">-Force</span></span>

<span data-ttu-id="ac769-155">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-155">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ac769-156">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="ac769-156">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="ac769-157">이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 Windows 운영 체제의 클라이언트 버전에서 원격 기능을 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-157">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="ac769-158">이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-158">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="ac769-159">이 매개 변수는 기본적으로 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있는 Windows 운영 체제의 서버 버전에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-159">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="ac769-160">서버 버전에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우 `Enable-PSRemoting` 이 매개 변수 값에 관계 없이을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-160">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="ac769-161">로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` **netsecurity** 모듈에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-161">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="ac769-162">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-162">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ac769-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ac769-163">-WhatIf</span></span>

<span data-ttu-id="ac769-164">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ac769-165">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ac769-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac769-166">CommonParameters</span></span>

<span data-ttu-id="ac769-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ac769-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ac769-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac769-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ac769-169">입력</span><span class="sxs-lookup"><span data-stu-id="ac769-169">INPUTS</span></span>

### <span data-ttu-id="ac769-170">없음</span><span class="sxs-lookup"><span data-stu-id="ac769-170">None</span></span>

<span data-ttu-id="ac769-171">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-171">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ac769-172">출력</span><span class="sxs-lookup"><span data-stu-id="ac769-172">OUTPUTS</span></span>

### <span data-ttu-id="ac769-173">System.String</span><span class="sxs-lookup"><span data-stu-id="ac769-173">System.String</span></span>

<span data-ttu-id="ac769-174">이 cmdlet은 결과를 설명 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-174">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="ac769-175">참고</span><span class="sxs-lookup"><span data-stu-id="ac769-175">NOTES</span></span>

<span data-ttu-id="ac769-176">PowerShell 3.0에서는 `Enable-PSRemoting` WS-Management 통신에 대해 다음과 같은 방화벽 예외를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-176">In PowerShell 3.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="ac769-177">서버 버전의 Windows 운영 체제에서는 `Enable-PSRemoting` 원격 액세스를 허용 하는 개인 및 도메인 네트워크에 대 한 방화벽 규칙을 만들고, 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-177">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="ac769-178">클라이언트 버전의 Windows 운영 체제에서 `Enable-PSRemoting` PowerShell 3.0은 무제한 원격 액세스를 허용 하는 개인 및 도메인 네트워크에 대 한 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-178">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 3.0 creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="ac769-179">공용 네트워크에 대해 동일한 로컬 서브넷에서의 원격 액세스를 허용하는 방화벽 규칙을 만들려면 **SkipNetworkProfileCheck** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-179">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="ac769-180">클라이언트 또는 서버 버전의 Windows 운영 체제에서 로컬 서브넷 제한을 제거 하 고 원격 액세스를 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만들려면 `Set-NetFirewallRule` NetSecurity 모듈에서 cmdlet을 사용 하 여 다음 명령을 실행 합니다. `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="ac769-180">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="ac769-181">PowerShell 2.0에서는 `Enable-PSRemoting` WS-Management 통신에 대해 다음과 같은 방화벽 예외를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-181">In PowerShell 2.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="ac769-182">서버 버전의 Windows 운영 체제에서는 원격 액세스를 허용 하는 모든 네트워크에 대 한 방화벽 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-182">On server versions of the Windows operating system, it creates firewall rules for all networks that allow remote access.</span></span>

<span data-ttu-id="ac769-183">Windows 운영 체제의 클라이언트 버전에서 `Enable-PSRemoting` PowerShell 2.0은 도메인 및 개인 네트워크 위치에 대해서만 방화벽 예외를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-183">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 2.0 creates a firewall exception only for domain and private network locations.</span></span> <span data-ttu-id="ac769-184">보안 위험을 최소화 하기 위해에서는 `Enable-PSRemoting` Windows 클라이언트 버전에서 공용 네트워크에 대 한 방화벽 규칙을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-184">To minimize security risks, `Enable-PSRemoting` does not create a firewall rule for public networks on client versions of Windows.</span></span> <span data-ttu-id="ac769-185">현재 네트워크 위치가 public 이면에서 `Enable-PSRemoting` 방화벽의 상태를 확인할 수 없습니다. 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-185">When the current network location is public, `Enable-PSRemoting` returns the following message: Unable to check the status of the firewall.</span></span>

<span data-ttu-id="ac769-186">PowerShell 3.0부터 `Enable-PSRemoting` 모든 세션 구성의 **Enabled** 속성 값을로 설정 하 여 모든 세션 구성을 사용 하도록 설정 `$True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-186">Starting in PowerShell 3.0, `Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="ac769-187">PowerShell 2.0에서는 `Enable-PSRemoting` 세션 구성의 보안 설명자에서 **Deny_All** 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-187">In PowerShell 2.0, `Enable-PSRemoting` removes the **Deny_All** setting from the security descriptor of session configurations.</span></span> <span data-ttu-id="ac769-188">PowerShell 3.0에서는 `Enable-PSRemoting` **Deny_All** 및 **Network_Deny_All** 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-188">In PowerShell 3.0, `Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="ac769-189">로컬에서 사용 하도록 예약 된 세션 구성에 대 한 원격 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac769-189">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="ac769-190">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ac769-190">RELATED LINKS</span></span>

[<span data-ttu-id="ac769-191">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac769-191">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ac769-192">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac769-192">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="ac769-193">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac769-193">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ac769-194">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac769-194">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ac769-195">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac769-195">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ac769-196">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ac769-196">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="ac769-197">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="ac769-197">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="ac769-198">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ac769-198">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="ac769-199">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ac769-199">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
