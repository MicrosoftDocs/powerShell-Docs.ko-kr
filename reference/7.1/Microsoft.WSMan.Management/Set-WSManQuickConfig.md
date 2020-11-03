---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: 07f984b43ee783f25e9ede4a5888cd9dbbdea417
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93219825"
---
# <span data-ttu-id="74ac9-103">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="74ac9-103">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="74ac9-104">개요</span><span class="sxs-lookup"><span data-stu-id="74ac9-104">SYNOPSIS</span></span>
<span data-ttu-id="74ac9-105">원격 관리를 위해 로컬 컴퓨터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-105">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="74ac9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74ac9-106">SYNTAX</span></span>

### <span data-ttu-id="74ac9-107">모두</span><span class="sxs-lookup"><span data-stu-id="74ac9-107">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="74ac9-108">설명</span><span class="sxs-lookup"><span data-stu-id="74ac9-108">DESCRIPTION</span></span>

<span data-ttu-id="74ac9-109">`Set-WSManQuickConfig`Cmdlet은 ws-management (Web Services For management) 기술을 사용 하 여 전송 된 PowerShell 원격 명령을 받도록 컴퓨터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-109">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="74ac9-110">`Set-WSManQuickConfig` 는 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-110">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="74ac9-111">WinRM 서비스가 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-111">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="74ac9-112">WinRM 서비스가 실행 되 고 있지 않은 경우 서비스가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-112">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="74ac9-113">WinRM 서비스 시작 유형을 자동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-113">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="74ac9-114">모든 IP 주소에서 요청을 수락 하는 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-114">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="74ac9-115">기본 전송은 **HTTP** 입니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-115">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="74ac9-116">WinRM 트래픽에 대해 방화벽 예외를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-116">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="74ac9-117">를 실행 하려면 `Set-WSManQuickConfig` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-117">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="74ac9-118">예제</span><span class="sxs-lookup"><span data-stu-id="74ac9-118">EXAMPLES</span></span>

### <span data-ttu-id="74ac9-119">예제 1: HTTP를 통해 로컬 컴퓨터의 원격 관리 사용</span><span class="sxs-lookup"><span data-stu-id="74ac9-119">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="74ac9-120">이 예에서는 로컬 컴퓨터의 원격 관리를 사용 하도록 설정 하는 데 필요한 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-120">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="74ac9-121">기본적으로이 명령은 **HTTP** 에 WS-Management 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-121">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="74ac9-122">예 2: HTTPS를 통해 로컬 컴퓨터의 원격 관리 사용</span><span class="sxs-lookup"><span data-stu-id="74ac9-122">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="74ac9-123">이 예에서는 로컬 컴퓨터의 원격 관리를 사용 하도록 설정 하는 데 필요한 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-123">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="74ac9-124">**UseSSL** 매개 변수는 **HTTPS** 가 컴퓨터와 통신 하는 데 사용 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-124">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="74ac9-125">**HTTPS** 를 사용 하려면 수동 구성이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-125">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="74ac9-126">자세한 내용은 **UseSSL** 매개 변수의 설명을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="74ac9-126">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="74ac9-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74ac9-127">PARAMETERS</span></span>

### <span data-ttu-id="74ac9-128">-Force</span><span class="sxs-lookup"><span data-stu-id="74ac9-128">-Force</span></span>

<span data-ttu-id="74ac9-129">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-129">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="74ac9-130">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="74ac9-130">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="74ac9-131">컴퓨터가 공용 네트워크에 있을 때 원격 기능을 사용할 수 있도록 Windows 클라이언트 버전을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-131">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="74ac9-132">이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-132">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="74ac9-133">이 매개 변수는 기본적으로 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있는 Windows 서버 버전에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-133">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="74ac9-134">서버 버전의 Windows에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우 `Enable-PSRemoting` 이 매개 변수의 값에 관계 없이에서 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-134">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="74ac9-135">로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` **netsecurity** 모듈에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-135">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="74ac9-136">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-136">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="74ac9-137">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="74ac9-137">-UseSSL</span></span>

<span data-ttu-id="74ac9-138">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-138">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="74ac9-139">기본적으로 SSL은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-139">By default, SSL isn't used.</span></span>

<span data-ttu-id="74ac9-140">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-140">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="74ac9-141">**UseSSL** 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-141">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="74ac9-142">이 매개 변수를 사용 하 고 연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-142">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="74ac9-143">**HTTPS** 는 WinRM 및 방화벽 규칙을 수동으로 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-143">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="74ac9-144">자세한 내용은 [방법: HTTPS에 대해 WINRM 구성](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="74ac9-144">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

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

### <span data-ttu-id="74ac9-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74ac9-145">CommonParameters</span></span>

<span data-ttu-id="74ac9-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74ac9-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74ac9-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74ac9-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74ac9-148">입력</span><span class="sxs-lookup"><span data-stu-id="74ac9-148">INPUTS</span></span>

### <span data-ttu-id="74ac9-149">없음</span><span class="sxs-lookup"><span data-stu-id="74ac9-149">None</span></span>

<span data-ttu-id="74ac9-150">이 cmdlet은 어떠한 입력도 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-150">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="74ac9-151">출력</span><span class="sxs-lookup"><span data-stu-id="74ac9-151">OUTPUTS</span></span>

### <span data-ttu-id="74ac9-152">없음</span><span class="sxs-lookup"><span data-stu-id="74ac9-152">None</span></span>

<span data-ttu-id="74ac9-153">이 cmdlet은 어떠한 출력도 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74ac9-153">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="74ac9-154">참고</span><span class="sxs-lookup"><span data-stu-id="74ac9-154">NOTES</span></span>

## <span data-ttu-id="74ac9-155">관련 링크</span><span class="sxs-lookup"><span data-stu-id="74ac9-155">RELATED LINKS</span></span>

[<span data-ttu-id="74ac9-156">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="74ac9-156">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="74ac9-157">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="74ac9-157">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="74ac9-158">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="74ac9-158">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="74ac9-159">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="74ac9-159">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="74ac9-160">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="74ac9-160">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="74ac9-161">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="74ac9-161">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="74ac9-162">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="74ac9-162">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="74ac9-163">방법: HTTPS에 대해 WINRM 구성</span><span class="sxs-lookup"><span data-stu-id="74ac9-163">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="74ac9-164">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="74ac9-164">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="74ac9-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="74ac9-165">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="74ac9-166">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="74ac9-166">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="74ac9-167">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="74ac9-167">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="74ac9-168">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="74ac9-168">Test-WSMan</span></span>](Test-WSMan.md)

