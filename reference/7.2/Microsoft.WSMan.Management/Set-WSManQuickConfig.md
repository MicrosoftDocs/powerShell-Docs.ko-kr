---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600416"
---
# <span data-ttu-id="9dbd5-102">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="9dbd5-102">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="9dbd5-103">개요</span><span class="sxs-lookup"><span data-stu-id="9dbd5-103">SYNOPSIS</span></span>
<span data-ttu-id="9dbd5-104">원격 관리를 위해 로컬 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-104">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="9dbd5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9dbd5-105">SYNTAX</span></span>

### <span data-ttu-id="9dbd5-106">모두</span><span class="sxs-lookup"><span data-stu-id="9dbd5-106">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="9dbd5-107">설명</span><span class="sxs-lookup"><span data-stu-id="9dbd5-107">DESCRIPTION</span></span>

<span data-ttu-id="9dbd5-108">`Set-WSManQuickConfig`Cmdlet은 ws-management (Web Services For management) 기술을 사용 하 여 전송 된 PowerShell 원격 명령을 받도록 컴퓨터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-108">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="9dbd5-109">`Set-WSManQuickConfig` 는 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-109">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="9dbd5-110">WinRM 서비스가 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-110">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="9dbd5-111">WinRM 서비스가 실행 되 고 있지 않은 경우 서비스가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-111">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="9dbd5-112">WinRM 서비스 시작 유형을 자동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-112">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="9dbd5-113">모든 IP 주소에서 요청을 수락 하는 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-113">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="9dbd5-114">기본 전송은 **HTTP** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-114">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="9dbd5-115">WinRM 트래픽에 대해 방화벽 예외를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-115">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="9dbd5-116">를 실행 하려면 `Set-WSManQuickConfig` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-116">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="9dbd5-117">예제</span><span class="sxs-lookup"><span data-stu-id="9dbd5-117">EXAMPLES</span></span>

### <span data-ttu-id="9dbd5-118">예제 1: HTTP를 통해 로컬 컴퓨터의 원격 관리 사용</span><span class="sxs-lookup"><span data-stu-id="9dbd5-118">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="9dbd5-119">이 예에서는 로컬 컴퓨터의 원격 관리를 사용 하도록 설정 하는 데 필요한 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-119">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="9dbd5-120">기본적으로이 명령은 **HTTP** 에 WS-Management 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-120">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="9dbd5-121">예 2: HTTPS를 통해 로컬 컴퓨터의 원격 관리 사용</span><span class="sxs-lookup"><span data-stu-id="9dbd5-121">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="9dbd5-122">이 예에서는 로컬 컴퓨터의 원격 관리를 사용 하도록 설정 하는 데 필요한 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-122">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="9dbd5-123">**UseSSL** 매개 변수는 **HTTPS** 가 컴퓨터와 통신 하는 데 사용 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-123">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="9dbd5-124">**HTTPS** 를 사용 하려면 수동 구성이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-124">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="9dbd5-125">자세한 내용은 **UseSSL** 매개 변수의 설명을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-125">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="9dbd5-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9dbd5-126">PARAMETERS</span></span>

### <span data-ttu-id="9dbd5-127">-Force</span><span class="sxs-lookup"><span data-stu-id="9dbd5-127">-Force</span></span>

<span data-ttu-id="9dbd5-128">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-128">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9dbd5-129">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="9dbd5-129">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="9dbd5-130">컴퓨터가 공용 네트워크에 있을 때 원격 기능을 사용할 수 있도록 Windows 클라이언트 버전을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-130">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="9dbd5-131">이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-131">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="9dbd5-132">이 매개 변수는 기본적으로 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있는 Windows 서버 버전에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-132">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="9dbd5-133">서버 버전의 Windows에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우 `Enable-PSRemoting` 이 매개 변수의 값에 관계 없이에서 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-133">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="9dbd5-134">로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` **netsecurity** 모듈에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-134">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="9dbd5-135">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-135">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9dbd5-136">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="9dbd5-136">-UseSSL</span></span>

<span data-ttu-id="9dbd5-137">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-137">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="9dbd5-138">기본적으로 SSL은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-138">By default, SSL isn't used.</span></span>

<span data-ttu-id="9dbd5-139">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-139">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="9dbd5-140">**UseSSL** 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-140">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="9dbd5-141">이 매개 변수를 사용 하 고 연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-141">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="9dbd5-142">**HTTPS** 는 WinRM 및 방화벽 규칙을 수동으로 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-142">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="9dbd5-143">자세한 내용은 [방법: HTTPS에 대해 WINRM 구성](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-143">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9dbd5-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9dbd5-144">CommonParameters</span></span>

<span data-ttu-id="9dbd5-145">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9dbd5-146">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9dbd5-147">입력</span><span class="sxs-lookup"><span data-stu-id="9dbd5-147">INPUTS</span></span>

### <span data-ttu-id="9dbd5-148">없음</span><span class="sxs-lookup"><span data-stu-id="9dbd5-148">None</span></span>

<span data-ttu-id="9dbd5-149">이 cmdlet은 어떠한 입력도 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-149">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="9dbd5-150">출력</span><span class="sxs-lookup"><span data-stu-id="9dbd5-150">OUTPUTS</span></span>

### <span data-ttu-id="9dbd5-151">없음</span><span class="sxs-lookup"><span data-stu-id="9dbd5-151">None</span></span>

<span data-ttu-id="9dbd5-152">이 cmdlet은 어떠한 출력도 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9dbd5-152">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="9dbd5-153">참고</span><span class="sxs-lookup"><span data-stu-id="9dbd5-153">NOTES</span></span>

## <span data-ttu-id="9dbd5-154">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9dbd5-154">RELATED LINKS</span></span>

[<span data-ttu-id="9dbd5-155">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="9dbd5-155">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="9dbd5-156">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9dbd5-156">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="9dbd5-157">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="9dbd5-157">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="9dbd5-158">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="9dbd5-158">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="9dbd5-159">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9dbd5-159">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="9dbd5-160">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9dbd5-160">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="9dbd5-161">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9dbd5-161">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="9dbd5-162">방법: HTTPS에 대해 WINRM 구성</span><span class="sxs-lookup"><span data-stu-id="9dbd5-162">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="9dbd5-163">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="9dbd5-163">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="9dbd5-164">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9dbd5-164">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="9dbd5-165">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9dbd5-165">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="9dbd5-166">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="9dbd5-166">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="9dbd5-167">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="9dbd5-167">Test-WSMan</span></span>](Test-WSMan.md)

