---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 37925cb1dfa7d588c38df46ec00ad2bfdc7cf9a2
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210993"
---
# <span data-ttu-id="23aea-103">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aea-103">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="23aea-104">개요</span><span class="sxs-lookup"><span data-stu-id="23aea-104">SYNOPSIS</span></span>
<span data-ttu-id="23aea-105">로컬 컴퓨터의 세션 구성을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-105">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="23aea-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23aea-106">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="23aea-107">설명</span><span class="sxs-lookup"><span data-stu-id="23aea-107">DESCRIPTION</span></span>

<span data-ttu-id="23aea-108">`Disable-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에서 세션 구성을 사용 하지 않도록 설정 하므로 모든 사용자가 세션 구성을 사용 하 여 로컬 컴퓨터에 사용자 관리 세션 ( **PSSessions** pssession)을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-108">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions ( **PSSessions** ) on the local computer.</span></span> <span data-ttu-id="23aea-109">이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="23aea-110">PowerShell 3.0부터 `Disable-PSSessionConfiguration` cmdlet은 세션 구성의 설정 **Enabled** 된 설정 ()을 `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` False로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-110">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="23aea-111">PowerShell 2.0에서 cmdlet은 `Disable-PSSessionConfiguration` 하나 이상의 등록 된 세션 구성의 보안 설명자에 **Deny_All** 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-111">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="23aea-112">매개 변수가 없으면 `Disable-PSSessionConfiguration` 세션에 사용 되는 기본 구성 인 **Microsoft. PowerShell** 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-112">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="23aea-113">사용자가 다른 구성을 지정하지 않으면 로컬 및 원격 사용자 모두 컴퓨터에 연결되는 세션을 효과적으로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-113">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="23aea-114">컴퓨터의 모든 세션 구성을 사용 하지 않도록 설정 하려면를 사용 `Disable-PSRemoting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-114">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="23aea-115">예제</span><span class="sxs-lookup"><span data-stu-id="23aea-115">EXAMPLES</span></span>

### <span data-ttu-id="23aea-116">예 1: 기본 구성을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="23aea-116">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="23aea-117">이 예제에서는 Microsoft. PowerShell 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-117">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="23aea-118">예 2: 등록 된 모든 세션 구성을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="23aea-118">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="23aea-119">이 예에서는 컴퓨터에 등록 된 모든 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-119">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="23aea-120">예제 3: 이름으로 세션 구성 비활성화</span><span class="sxs-lookup"><span data-stu-id="23aea-120">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="23aea-121">이 예에서는 이름이 Microsoft로 시작 하는 모든 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-121">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="23aea-122">**Force** 매개 변수는 cmdlet에서 모든 사용자 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-122">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="23aea-123">예제 4: 파이프라인을 사용 하 여 세션 구성 비활성화</span><span class="sxs-lookup"><span data-stu-id="23aea-123">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="23aea-124">이 예에서는 **MaintenanceShell** 및 **adminshell** 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-124">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="23aea-125">파이프라인 연산자 (|)가의 결과를로 보냅니다 `Get-PSSessionConfiguration` `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="23aea-125">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="23aea-126">예 5: 세션 구성을 사용 하지 않도록 설정 하는 효과</span><span class="sxs-lookup"><span data-stu-id="23aea-126">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="23aea-127">이 예에서는 실행 전후 사용 권한과 `Disable-PSSessionConfiguration` 세션 구성을 사용 하지 않도록 설정 하는 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-127">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> <span data-ttu-id="23aea-128">구성을 사용 하지 않도록 설정 해도 cmdlet을 사용 하 여 구성을 변경할 수 있습니다 `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="23aea-128">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="23aea-129">구성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-129">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="23aea-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23aea-130">PARAMETERS</span></span>

### <span data-ttu-id="23aea-131">-Force</span><span class="sxs-lookup"><span data-stu-id="23aea-131">-Force</span></span>

<span data-ttu-id="23aea-132">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-132">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="23aea-133">-Name</span><span class="sxs-lookup"><span data-stu-id="23aea-133">-Name</span></span>

<span data-ttu-id="23aea-134">사용 하지 않도록 설정할 세션 구성의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-134">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="23aea-135">구성 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-135">Enter one or more configuration names.</span></span> <span data-ttu-id="23aea-136">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-136">Wildcard characters are permitted.</span></span> <span data-ttu-id="23aea-137">구성 이름이 나 세션 구성 개체를 포함 하는 문자열을로 파이프 할 수도 있습니다 `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="23aea-137">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="23aea-138">이 매개 변수를 생략 하면에서 `Disable-PSSessionConfiguration` Microsoft. PowerShell 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-138">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

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

### <span data-ttu-id="23aea-139">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="23aea-139">-NoServiceRestart</span></span>

<span data-ttu-id="23aea-140">WSMan 서비스의 다시 시작을 방지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-140">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="23aea-141">구성을 사용 하지 않도록 설정 하기 위해 서비스를 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-141">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="23aea-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="23aea-142">-Confirm</span></span>

<span data-ttu-id="23aea-143">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="23aea-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="23aea-144">-WhatIf</span></span>

<span data-ttu-id="23aea-145">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="23aea-146">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="23aea-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23aea-147">CommonParameters</span></span>

<span data-ttu-id="23aea-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23aea-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23aea-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23aea-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23aea-150">입력</span><span class="sxs-lookup"><span data-stu-id="23aea-150">INPUTS</span></span>

### <span data-ttu-id="23aea-151">Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration, System.string</span><span class="sxs-lookup"><span data-stu-id="23aea-151">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="23aea-152">세션 구성 개체 또는 세션 구성의 이름을 포함 하는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-152">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="23aea-153">출력</span><span class="sxs-lookup"><span data-stu-id="23aea-153">OUTPUTS</span></span>

### <span data-ttu-id="23aea-154">없음</span><span class="sxs-lookup"><span data-stu-id="23aea-154">None</span></span>

<span data-ttu-id="23aea-155">이 cmdlet은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-155">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="23aea-156">참고</span><span class="sxs-lookup"><span data-stu-id="23aea-156">NOTES</span></span>

<span data-ttu-id="23aea-157">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23aea-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="23aea-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="23aea-158">RELATED LINKS</span></span>

[<span data-ttu-id="23aea-159">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aea-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="23aea-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aea-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="23aea-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="23aea-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="23aea-162">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aea-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="23aea-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aea-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="23aea-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="23aea-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="23aea-165">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aea-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="23aea-166">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="23aea-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="23aea-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="23aea-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="23aea-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="23aea-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
