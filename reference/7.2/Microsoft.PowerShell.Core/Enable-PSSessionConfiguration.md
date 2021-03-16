---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 86650f33f376ccb7d1428836c9d0070e749cf0ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99604996"
---
# <span data-ttu-id="1090f-102">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1090f-102">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="1090f-103">개요</span><span class="sxs-lookup"><span data-stu-id="1090f-103">SYNOPSIS</span></span>
<span data-ttu-id="1090f-104">로컬 컴퓨터의 세션 구성을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-104">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="1090f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1090f-105">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1090f-106">설명</span><span class="sxs-lookup"><span data-stu-id="1090f-106">DESCRIPTION</span></span>

<span data-ttu-id="1090f-107">`Enable-PSSessionConfiguration`Cmdlet을 사용 하면 `Disable-PSSessionConfiguration` 또는 `Disable-PSRemoting` Cmdlet 또는의 **accessmode** 매개 변수를 사용 하는 등 사용 하지 않도록 설정 된 등록 된 세션 구성을 사용할 수 있습니다 `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1090f-107">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="1090f-108">이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="1090f-109">매개 변수가 없으면 `Enable-PSSessionConfiguration` 세션에 사용 되는 기본 구성 인 **Microsoft. PowerShell** 구성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-109">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="1090f-110">`Enable-PSSessionConfiguration` 영향을 받는 세션 구성의 보안 설명자에서 **Deny_All** 설정을 제거 하 고, 모든 IP 주소에서 요청을 수락 하는 수신기를 설정 하 고, WinRM 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-110">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="1090f-111">PowerShell 3.0 부터는에서 `Enable-PSSessionConfiguration` 세션 구성의 **Enabled** 속성 값 ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` )을 True로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-111">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="1090f-112">그러나는 `Enable-PSSessionConfiguration`  `AccessMode=Local` 로컬 컴퓨터의 사용자만 세션 구성에 사용할 수 있도록 하는 Network_Deny_All () 보안 설명자 설정을 제거 하거나 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-112">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="1090f-113">예제</span><span class="sxs-lookup"><span data-stu-id="1090f-113">EXAMPLES</span></span>

### <span data-ttu-id="1090f-114">예제 1: 기본 세션 다시 사용</span><span class="sxs-lookup"><span data-stu-id="1090f-114">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="1090f-115">이 예제에서는 컴퓨터에서 **Microsoft. PowerShell** 기본 세션 구성을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-115">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="1090f-116">예제 2: 지정 된 세션 다시 사용</span><span class="sxs-lookup"><span data-stu-id="1090f-116">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="1090f-117">이 예제에서는 컴퓨터에서 **MaintenanceShell** 및 **adminshell** 세션 구성을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-117">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="1090f-118">예제 3: 모든 세션 다시 사용</span><span class="sxs-lookup"><span data-stu-id="1090f-118">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="1090f-119">이 예에서는 컴퓨터의 모든 세션 구성을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-119">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="1090f-120">이러한 명령은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-120">These commands are equivalent.</span></span>
<span data-ttu-id="1090f-121">따라서 둘 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-121">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="1090f-122">`Enable-PSSessionConfiguration` 이미 사용 하도록 설정 된 세션 구성을 사용 하도록 설정 하면에서 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-122">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="1090f-123">예제 4: 세션을 다시 사용 하도록 설정 하 고 새 보안 설명자 지정</span><span class="sxs-lookup"><span data-stu-id="1090f-123">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="1090f-124">이 예에서는 **MaintenanceShell** 세션 구성을 다시 사용 하도록 설정 하 고 구성에 대 한 새 보안 설명자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-124">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="1090f-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1090f-125">PARAMETERS</span></span>

### <span data-ttu-id="1090f-126">-Force</span><span class="sxs-lookup"><span data-stu-id="1090f-126">-Force</span></span>

<span data-ttu-id="1090f-127">Cmdlet에서 확인 메시지를 표시 하지 않고 WinRM 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-127">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="1090f-128">서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-128">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="1090f-129">다시 시작하지 않고 다시 시작 프롬프트를 표시하지 않으려면 **NoServiceRestart** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-129">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="1090f-130">-Name</span><span class="sxs-lookup"><span data-stu-id="1090f-130">-Name</span></span>

<span data-ttu-id="1090f-131">사용하도록 설정할 세션 구성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-131">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="1090f-132">구성 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-132">Enter one or more configuration names.</span></span>
<span data-ttu-id="1090f-133">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-133">Wildcard characters are permitted.</span></span>

<span data-ttu-id="1090f-134">구성 이름이 나 세션 구성 개체를 포함 하는 문자열을로 파이프 할 수도 있습니다 `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1090f-134">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="1090f-135">이 매개 변수를 생략 하면에서 `Enable-PSSessionConfiguration` **Microsoft. PowerShell** 세션 구성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-135">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1090f-136">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="1090f-136">-NoServiceRestart</span></span>

<span data-ttu-id="1090f-137">Cmdlet에서 서비스를 다시 시작 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-137">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="1090f-138">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="1090f-138">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="1090f-139">이 cmdlet이 세션 구성에 대 한 보안 설명자를 대체 하는 보안 설명자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-139">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="1090f-140">이 매개 변수를 생략 하면는 `Enable-PSSessionConfiguration` 보안 설명자에서 모두 거부 항목만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-140">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1090f-141">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="1090f-141">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="1090f-142">이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 세션 구성을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-142">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="1090f-143">이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-143">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="1090f-144">기본적으로는 `Enable-PSSessionConfiguration` 공용 네트워크에서 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-144">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="1090f-145">이 매개 변수는 Windows 운영 체제의 클라이언트 버전용으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-145">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="1090f-146">서버 버전의 Windows 운영 체제에는 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-146">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="1090f-147">그러나 서버 버전의 Windows 운영 체제에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우이 매개 변수는 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-147">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="1090f-148">로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` NetSecurity 모듈에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-148">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="1090f-149">자세한 내용은 `Enable-PSRemoting`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1090f-149">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="1090f-150">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-150">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1090f-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1090f-151">-Confirm</span></span>

<span data-ttu-id="1090f-152">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1090f-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1090f-153">-WhatIf</span></span>

<span data-ttu-id="1090f-154">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1090f-155">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1090f-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1090f-156">CommonParameters</span></span>

<span data-ttu-id="1090f-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1090f-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1090f-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1090f-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1090f-159">입력</span><span class="sxs-lookup"><span data-stu-id="1090f-159">INPUTS</span></span>

### <span data-ttu-id="1090f-160">Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration, System.string</span><span class="sxs-lookup"><span data-stu-id="1090f-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="1090f-161">세션 구성 개체 또는 세션 구성의 이름을 포함 하는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-161">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="1090f-162">출력</span><span class="sxs-lookup"><span data-stu-id="1090f-162">OUTPUTS</span></span>

### <span data-ttu-id="1090f-163">없음</span><span class="sxs-lookup"><span data-stu-id="1090f-163">None</span></span>

<span data-ttu-id="1090f-164">이 cmdlet은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="1090f-165">참고</span><span class="sxs-lookup"><span data-stu-id="1090f-165">NOTES</span></span>

<span data-ttu-id="1090f-166">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="1090f-167">이 cmdlet을 사용 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1090f-167">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="1090f-168">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1090f-168">RELATED LINKS</span></span>

[<span data-ttu-id="1090f-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1090f-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="1090f-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1090f-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="1090f-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1090f-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="1090f-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="1090f-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="1090f-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1090f-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="1090f-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1090f-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="1090f-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1090f-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="1090f-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1090f-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="1090f-177">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="1090f-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="1090f-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="1090f-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="1090f-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="1090f-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)