---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: c2f88431c0a09a2d4093c6523467a812812c10bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602456"
---
# <span data-ttu-id="1dd9b-102">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dd9b-102">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="1dd9b-103">개요</span><span class="sxs-lookup"><span data-stu-id="1dd9b-103">SYNOPSIS</span></span>
<span data-ttu-id="1dd9b-104">로컬 컴퓨터의 세션 구성을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-104">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="1dd9b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1dd9b-105">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="1dd9b-106">설명</span><span class="sxs-lookup"><span data-stu-id="1dd9b-106">DESCRIPTION</span></span>

<span data-ttu-id="1dd9b-107">`Disable-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에서 세션 구성을 사용 하지 않도록 설정 하므로 모든 사용자가 세션 구성을 사용 하 여 로컬 컴퓨터에 사용자 관리 세션 (pssession)을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-107">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions (**PSSessions**) on the local computer.</span></span> <span data-ttu-id="1dd9b-108">이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="1dd9b-109">PowerShell 3.0부터 `Disable-PSSessionConfiguration` cmdlet은 세션 구성의 설정  된 설정 ()을 `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` False로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-109">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="1dd9b-110">PowerShell 2.0에서 cmdlet은 `Disable-PSSessionConfiguration` 하나 이상의 등록 된 세션 구성의 보안 설명자에 **Deny_All** 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-110">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="1dd9b-111">매개 변수가 없으면 `Disable-PSSessionConfiguration` 세션에 사용 되는 기본 구성 인 **Microsoft. PowerShell** 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-111">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="1dd9b-112">사용자가 다른 구성을 지정하지 않으면 로컬 및 원격 사용자 모두 컴퓨터에 연결되는 세션을 효과적으로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-112">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="1dd9b-113">컴퓨터의 모든 세션 구성을 사용 하지 않도록 설정 하려면를 사용 `Disable-PSRemoting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-113">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="1dd9b-114">예제</span><span class="sxs-lookup"><span data-stu-id="1dd9b-114">EXAMPLES</span></span>

### <span data-ttu-id="1dd9b-115">예 1: 기본 구성을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="1dd9b-115">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="1dd9b-116">이 예제에서는 Microsoft. PowerShell 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-116">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="1dd9b-117">예 2: 등록 된 모든 세션 구성을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="1dd9b-117">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="1dd9b-118">이 예에서는 컴퓨터에 등록 된 모든 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-118">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="1dd9b-119">예제 3: 이름으로 세션 구성 비활성화</span><span class="sxs-lookup"><span data-stu-id="1dd9b-119">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="1dd9b-120">이 예에서는 이름이 Microsoft로 시작 하는 모든 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-120">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="1dd9b-121">**Force** 매개 변수는 cmdlet에서 모든 사용자 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-121">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="1dd9b-122">예제 4: 파이프라인을 사용 하 여 세션 구성 비활성화</span><span class="sxs-lookup"><span data-stu-id="1dd9b-122">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="1dd9b-123">이 예에서는 **MaintenanceShell** 및 **adminshell** 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-123">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="1dd9b-124">파이프라인 연산자 (|)가의 결과를로 보냅니다 `Get-PSSessionConfiguration` `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1dd9b-124">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="1dd9b-125">예 5: 세션 구성을 사용 하지 않도록 설정 하는 효과</span><span class="sxs-lookup"><span data-stu-id="1dd9b-125">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="1dd9b-126">이 예에서는 실행 전후 사용 권한과 `Disable-PSSessionConfiguration` 세션 구성을 사용 하지 않도록 설정 하는 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-126">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

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
> <span data-ttu-id="1dd9b-127">구성을 사용 하지 않도록 설정 해도 cmdlet을 사용 하 여 구성을 변경할 수 있습니다 `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1dd9b-127">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="1dd9b-128">구성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-128">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="1dd9b-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1dd9b-129">PARAMETERS</span></span>

### <span data-ttu-id="1dd9b-130">-Force</span><span class="sxs-lookup"><span data-stu-id="1dd9b-130">-Force</span></span>

<span data-ttu-id="1dd9b-131">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-131">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1dd9b-132">-Name</span><span class="sxs-lookup"><span data-stu-id="1dd9b-132">-Name</span></span>

<span data-ttu-id="1dd9b-133">사용 하지 않도록 설정할 세션 구성의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-133">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="1dd9b-134">구성 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-134">Enter one or more configuration names.</span></span> <span data-ttu-id="1dd9b-135">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="1dd9b-136">구성 이름이 나 세션 구성 개체를 포함 하는 문자열을로 파이프 할 수도 있습니다 `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1dd9b-136">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="1dd9b-137">이 매개 변수를 생략 하면에서 `Disable-PSSessionConfiguration` Microsoft. PowerShell 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-137">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

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

### <span data-ttu-id="1dd9b-138">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="1dd9b-138">-NoServiceRestart</span></span>

<span data-ttu-id="1dd9b-139">WSMan 서비스의 다시 시작을 방지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-139">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="1dd9b-140">구성을 사용 하지 않도록 설정 하기 위해 서비스를 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-140">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="1dd9b-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1dd9b-141">-Confirm</span></span>

<span data-ttu-id="1dd9b-142">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1dd9b-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1dd9b-143">-WhatIf</span></span>

<span data-ttu-id="1dd9b-144">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1dd9b-145">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1dd9b-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1dd9b-146">CommonParameters</span></span>

<span data-ttu-id="1dd9b-147">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1dd9b-148">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1dd9b-149">입력</span><span class="sxs-lookup"><span data-stu-id="1dd9b-149">INPUTS</span></span>

### <span data-ttu-id="1dd9b-150">Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration, System.string</span><span class="sxs-lookup"><span data-stu-id="1dd9b-150">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="1dd9b-151">세션 구성 개체 또는 세션 구성의 이름을 포함 하는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-151">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="1dd9b-152">출력</span><span class="sxs-lookup"><span data-stu-id="1dd9b-152">OUTPUTS</span></span>

### <span data-ttu-id="1dd9b-153">없음</span><span class="sxs-lookup"><span data-stu-id="1dd9b-153">None</span></span>

<span data-ttu-id="1dd9b-154">이 cmdlet은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-154">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="1dd9b-155">참고</span><span class="sxs-lookup"><span data-stu-id="1dd9b-155">NOTES</span></span>

<span data-ttu-id="1dd9b-156">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-156">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="1dd9b-157">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dd9b-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="1dd9b-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1dd9b-158">RELATED LINKS</span></span>

[<span data-ttu-id="1dd9b-159">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dd9b-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="1dd9b-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dd9b-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="1dd9b-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1dd9b-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="1dd9b-162">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dd9b-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="1dd9b-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dd9b-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="1dd9b-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1dd9b-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="1dd9b-165">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dd9b-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="1dd9b-166">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="1dd9b-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="1dd9b-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="1dd9b-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="1dd9b-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="1dd9b-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
