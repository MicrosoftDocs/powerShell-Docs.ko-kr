---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 4ac7605ada0fdb682e9df31c2422d368d6e64f57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602440"
---
# <span data-ttu-id="49fae-102">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-102">Unregister-PSSessionConfiguration</span></span>

## <span data-ttu-id="49fae-103">개요</span><span class="sxs-lookup"><span data-stu-id="49fae-103">SYNOPSIS</span></span>
<span data-ttu-id="49fae-104">컴퓨터에서 등록된 세션 구성을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-104">Deletes registered session configurations from the computer.</span></span>

## <span data-ttu-id="49fae-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49fae-105">SYNTAX</span></span>

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="49fae-106">설명</span><span class="sxs-lookup"><span data-stu-id="49fae-106">DESCRIPTION</span></span>

<span data-ttu-id="49fae-107">`Unregister-PSSessionConfiguration`Cmdlet은 컴퓨터에서 등록 된 세션 구성을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-107">The `Unregister-PSSessionConfiguration` cmdlet deletes registered session configurations from the computer.</span></span> <span data-ttu-id="49fae-108">이 cmdlet은 시스템 관리자가 사용자에 대 한 사용자 지정 세션 구성을 관리 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-108">This cmdlet is designed for system administrators to manage customized session configurations for users.</span></span>

<span data-ttu-id="49fae-109">변경 내용을 적용 하려면에서 `Unregister-PSSessionConfiguration` **WinRM** 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-109">To make the change effective, `Unregister-PSSessionConfiguration` restarts the **WinRM** service.</span></span> <span data-ttu-id="49fae-110">다시 시작을 방지 하려면 **NoServiceRestart** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-110">To prevent the restart, specify the **NoServiceRestart** parameter.</span></span>

<span data-ttu-id="49fae-111">기본 **microsoft.powershell32** 세션 구성을 실수로 삭제  한 경우 cmdlet을 사용 `Enable-PSRemoting` 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-111">If you accidentally delete the default **Microsoft.PowerShell** or **Microsoft.PowerShell32** session configurations, use the `Enable-PSRemoting` cmdlet to restore them.</span></span> <span data-ttu-id="49fae-112">자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="49fae-112">For more information, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="49fae-113">예제</span><span class="sxs-lookup"><span data-stu-id="49fae-113">EXAMPLES</span></span>

### <span data-ttu-id="49fae-114">예 1: 세션 구성 삭제</span><span class="sxs-lookup"><span data-stu-id="49fae-114">Example 1: Delete a session configuration</span></span>

<span data-ttu-id="49fae-115">이 예에서는 컴퓨터에서 **MaintenanceShell** 세션 구성을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-115">This example deletes the **MaintenanceShell** session configuration from the computer.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### <span data-ttu-id="49fae-116">예 2: 세션 구성을 삭제 하 고 WinRM 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-116">Example 2: Delete a session configuration and restart the WinRM service</span></span>

<span data-ttu-id="49fae-117">이 예제에서는 **MaintenanceShell** 구성을 삭제 하 고 WinRM 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-117">In this example, we delete the **MaintenanceShell** configuration and restart the WinRM service.</span></span> <span data-ttu-id="49fae-118">**Force** 매개 변수는 메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하는 모든 사용자 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-118">The **Force** parameter suppresses all user messages to restart the **WinRM** service without prompting.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### <span data-ttu-id="49fae-119">예 3: 모든 세션 구성 삭제</span><span class="sxs-lookup"><span data-stu-id="49fae-119">Example 3: Delete all session configurations</span></span>

<span data-ttu-id="49fae-120">이 예에서는 컴퓨터의 모든 세션 구성을 삭제 하는 두 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-120">This examples show two ways to delete all the session configurations on the computer.</span></span> <span data-ttu-id="49fae-121">두 명령 모두 동일한 효과를 가지 며 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-121">Both commands have the same effect and can be used interchangeably.</span></span>

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### <span data-ttu-id="49fae-122">예제 4: 다시 시작 하지 않고 등록 취소</span><span class="sxs-lookup"><span data-stu-id="49fae-122">Example 4: Unregister without a restart</span></span>

<span data-ttu-id="49fae-123">이 예제에서는 **NoServiceRestart** 매개 변수를 사용 하 여 컴퓨터의 모든 세션이 중단 되는 서비스 다시 시작을 방지 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-123">This example shows the effect of using the **NoServiceRestart** parameter to prevent a service restart that would disrupt any sessions on the computer.</span></span>

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="49fae-124">는 `Unregister-PSSessionConfiguration` **MaintenanceShell** 세션 구성을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-124">The `Unregister-PSSessionConfiguration` deletes the **MaintenanceShell** session configuration.</span></span>
<span data-ttu-id="49fae-125">그러나이 명령은 **NoServiceRestart** 매개 변수를 사용 하므로 **WinRM** 서비스가 다시 시작 되지 않고 변경 내용이 아직 완전히 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-125">However, because the command uses the **NoServiceRestart** parameter, the **WinRM** service is not restarted and the change is not yet completely effective.</span></span>

<span data-ttu-id="49fae-126">다음으로는 `Get-PSSessionConfiguration` **MaintenanceShell** 세션을 가져오려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-126">Next, the `Get-PSSessionConfiguration` tries to get the **MaintenanceShell** session.</span></span> <span data-ttu-id="49fae-127">WS-Management 리소스 테이블에서 세션이 제거 되었으므로에서 해당 세션을 `Get-PSSessionConfiguration` 반환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-127">Because the session has been removed from the WS-Management resource table, `Get-PSSessionConfiguration` cannot return it.</span></span>

<span data-ttu-id="49fae-128">`New-PSSession`Cmdlet은 **MaintenanceShell** 구성을 사용 하 여 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-128">The `New-PSSession` cmdlet creates a session using the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="49fae-129">명령이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-129">The command succeeds.</span></span> <span data-ttu-id="49fae-130">다음으로, **WinRM** 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-130">Next, we restart the **WinRM** service.</span></span>

<span data-ttu-id="49fae-131">마지막으로 `New-PSSession` cmdlet은 **MaintenanceShell** 구성을 사용 하는 세션을 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-131">Finally, the `New-PSSession` cmdlet tries to create a session that uses the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="49fae-132">이번에는 WinRM 서비스가 다시 시작 될 때 **MaintenanceShell** 구성이 삭제 되었으므로 세션이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-132">This time, the session fails because the **MaintenanceShell** configuration was deleted when the WinRM service restarted.</span></span>

## <span data-ttu-id="49fae-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49fae-133">PARAMETERS</span></span>

### <span data-ttu-id="49fae-134">-Force</span><span class="sxs-lookup"><span data-stu-id="49fae-134">-Force</span></span>

<span data-ttu-id="49fae-135">Cmdlet에서 확인 메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-135">Indicates that the cmdlet does not prompt you for confirmation, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="49fae-136">서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-136">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="49fae-137">다시 시작하지 않고 다시 시작 프롬프트를 표시하지 않으려면 **NoServiceRestart** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-137">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="49fae-138">-Name</span><span class="sxs-lookup"><span data-stu-id="49fae-138">-Name</span></span>

<span data-ttu-id="49fae-139">삭제할 세션 구성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-139">Specifies the names of the session configurations to delete.</span></span> <span data-ttu-id="49fae-140">세션 구성 이름 또는 구성 이름 패턴을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-140">Enter one session configuration name or a configuration name pattern.</span></span> <span data-ttu-id="49fae-141">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-141">Wildcard characters are permitted.</span></span> <span data-ttu-id="49fae-142">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-142">This parameter is required.</span></span>

<span data-ttu-id="49fae-143">세션 구성을로 파이프 할 수도 있습니다 `Unregister-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="49fae-143">You can also pipe a session configurations to `Unregister-PSSessionConfiguration`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="49fae-144">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="49fae-144">-NoServiceRestart</span></span>

<span data-ttu-id="49fae-145">이 cmdlet은 **WinRM** 서비스를 다시 시작 하지 않고 서비스를 다시 시작 하 라는 메시지를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-145">Indicates that this cmdlet does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="49fae-146">기본적으로 명령을 실행 하면 `Unregister-PSSessionConfiguration` **WinRM** 서비스를 다시 시작 하 여 변경 내용을 적용 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-146">By default, when you run an `Unregister-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the change effective.</span></span> <span data-ttu-id="49fae-147">**WinRM** 서비스가 다시 시작 될 때까지 사용자는 아직 등록 되지 않은 세션 구성을 사용할 수 있습니다. 단,이를 찾지 못하는 경우에도 마찬가지 `Get-PSSessionConfiguration` 입니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-147">Until the **WinRM** service is restarted, users can still use the unregistered session configuration, even though `Get-PSSessionConfiguration` does not find it.</span></span>

<span data-ttu-id="49fae-148">메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하려면 **Force** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-148">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="49fae-149">**WinRM** 서비스를 수동으로 다시 시작 하려면 cmdlet을 사용 합니다 `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="49fae-149">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="49fae-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="49fae-150">-Confirm</span></span>

<span data-ttu-id="49fae-151">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="49fae-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="49fae-152">-WhatIf</span></span>

<span data-ttu-id="49fae-153">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="49fae-154">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="49fae-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49fae-155">CommonParameters</span></span>

<span data-ttu-id="49fae-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49fae-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49fae-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49fae-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49fae-158">입력</span><span class="sxs-lookup"><span data-stu-id="49fae-158">INPUTS</span></span>

### <span data-ttu-id="49fae-159">Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-159">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

<span data-ttu-id="49fae-160">세션 구성 개체를에서이 cmdlet으로 파이프 할 수 있습니다 `Get-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="49fae-160">You can pipe a session configuration object from `Get-PSSessionConfiguration` to this cmdlet.</span></span>

## <span data-ttu-id="49fae-161">출력</span><span class="sxs-lookup"><span data-stu-id="49fae-161">OUTPUTS</span></span>

### <span data-ttu-id="49fae-162">없음</span><span class="sxs-lookup"><span data-stu-id="49fae-162">None</span></span>

<span data-ttu-id="49fae-163">이 cmdlet은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-163">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="49fae-164">참고</span><span class="sxs-lookup"><span data-stu-id="49fae-164">NOTES</span></span>

<span data-ttu-id="49fae-165">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-165">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="49fae-166">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49fae-166">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="49fae-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="49fae-167">RELATED LINKS</span></span>

[<span data-ttu-id="49fae-168">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-168">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="49fae-169">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-169">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="49fae-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="49fae-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="49fae-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="49fae-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="49fae-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="49fae-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="49fae-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="49fae-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="49fae-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="49fae-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="49fae-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="49fae-177">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="49fae-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="49fae-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="49fae-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="49fae-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="49fae-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
