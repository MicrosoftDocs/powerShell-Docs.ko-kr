---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 72ee8c7eebf7d74920fd0d39e3a508841e57b7c5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347502"
---
# <span data-ttu-id="04f95-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04f95-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="04f95-104">개요</span><span class="sxs-lookup"><span data-stu-id="04f95-104">SYNOPSIS</span></span>
<span data-ttu-id="04f95-105">등록된 세션 구성의 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="04f95-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="04f95-106">SYNTAX</span></span>

### <span data-ttu-id="04f95-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="04f95-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04f95-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="04f95-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04f95-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="04f95-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="04f95-110">설명</span><span class="sxs-lookup"><span data-stu-id="04f95-110">DESCRIPTION</span></span>

<span data-ttu-id="04f95-111">`Set-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에서 세션 구성의 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="04f95-112">**Name** 매개 변수를 사용하여 변경할 세션 구성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="04f95-113">다른 매개 변수를 사용하여 세션 구성의 속성에 대해 새 값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="04f95-114">구성에서 속성 값을 삭제 하 고 기본값을 사용 하려면 해당 매개 변수에 대해 빈 문자열 ("") 또는 값을 입력 `$Null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="04f95-115">PowerShell 3.0부터 세션 구성 파일을 사용 하 여 세션 구성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="04f95-116">이 기능은 세션 구성을 사용하는 세션의 속성을 설정 및 변경하는 간단하고 검색 가능한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="04f95-117">세션 구성 파일을 지정 하려면의 **Path** 매개 변수를 사용 `Set-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="04f95-118">세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04f95-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="04f95-119">세션 구성 파일을 만들고 수정 하는 방법에 대 한 자세한 내용은 cmdlet을 참조 하십시오 `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="04f95-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="04f95-120">세션 구성은 로컬 컴퓨터에 연결 되는 원격 세션 ( **pssessions** ) 환경을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="04f95-121">모든 **PSSession** 은 세션 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="04f95-122">세션 구성은 세션에서 사용 가능한 모듈, 실행할 수 있는 cmdlet, 언어 모드, 할당량 및 시간 제한과 같은 **PSSession** 의 기능을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="04f95-123">세션 구성의 보안 설명자는 세션 구성을 사용 하 여 로컬 컴퓨터에 연결할 수 있는 사용자를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="04f95-124">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04f95-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="04f95-125">세션 구성의 속성을 보려면 `Get-PSSessionConfiguration` cmdlet 또는 WSMan 공급자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="04f95-126">WSMan 공급자에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="04f95-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="04f95-127">예제</span><span class="sxs-lookup"><span data-stu-id="04f95-127">EXAMPLES</span></span>

### <span data-ttu-id="04f95-128">예제 1: 세션 구성 만들기 및 변경</span><span class="sxs-lookup"><span data-stu-id="04f95-128">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="04f95-129">이 예제에서는 구성에서 시작 스크립트를 추가 하 고 제거 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-129">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="04f95-130">첫 번째 명령은 **Adminshell** 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-130">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="04f95-131">두 번째 명령은 `AdminConfig.ps1` 구성에 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-131">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="04f95-132">**WinRM** 을 다시 시작할 때 변경 내용이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-132">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="04f95-133">세 번째 명령은 `AdminConfig.ps1` 구성에서 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-133">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="04f95-134">예제 2: 결과 표시</span><span class="sxs-lookup"><span data-stu-id="04f95-134">Example 2: Display results</span></span>

<span data-ttu-id="04f95-135">이 예에서는 **MaximumReceivedObjectSizeMB** 속성의 값을 20으로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-135">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="04f95-136">이 명령은 또한 **WinRM** 서비스를 다시 시작 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-136">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="04f95-137">**WinRM** 서비스를 다시 시작할 때까지 변경 내용이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-137">The change is not effective until the **WinRM** service is restarted.</span></span>

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### <span data-ttu-id="04f95-138">예제 3: 다양 한 방법으로 결과 표시</span><span class="sxs-lookup"><span data-stu-id="04f95-138">Example 3: Display results in different ways</span></span>

<span data-ttu-id="04f95-139">이 예에서는 `Set-PSSessionConfiguration` **MaintenanceShell** 세션 구성의 시작 스크립트를로 변경 합니다 `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="04f95-139">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="04f95-140">출력은 변경 내용을 표시 하 고 **WinRM** 서비스를 다시 시작 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-140">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="04f95-141">"y"(예)로 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-141">The response is "y" (yes).</span></span>

<span data-ttu-id="04f95-142">`Get-PSSessionConfiguration`**MaintenanceShell** 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-142">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="04f95-143">파이프라인 연산자 (|)는 명령 결과를으로 보냅니다. 그러면 `Format-List` 이 목록에 있는 구성 개체의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-143">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="04f95-144">그런 다음 WSMan 공급자를 사용 하 여 **MaintenanceShell** 구성에 대 한 초기화 매개 변수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-144">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="04f95-145">`Get-ChildItem`(별칭 `dir` ) **MaintenanceShell** 플러그 인에 대 한 **InitializationParameters** 노드의 자식 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-145">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="04f95-146">WSMan 공급자에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="04f95-146">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## <span data-ttu-id="04f95-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="04f95-147">PARAMETERS</span></span>

### <span data-ttu-id="04f95-148">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="04f95-148">-AccessMode</span></span>

<span data-ttu-id="04f95-149">세션 구성을 사용하거나 사용하지 않도록 설정하고 컴퓨터에서 원격 또는 로컬 세션에 사용할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-149">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="04f95-150">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="04f95-151">사용 안 함.</span><span class="sxs-lookup"><span data-stu-id="04f95-151">Disabled.</span></span> <span data-ttu-id="04f95-152">세션 구성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-152">Disables the session configuration.</span></span> <span data-ttu-id="04f95-153">컴퓨터에 대한 원격 또는 로컬 액세스에 세션 구성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-153">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="04f95-154">이 값은 세션 구성의 **Enabled** 속성 ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` )을 **False** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-154">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="04f95-155">로컬.</span><span class="sxs-lookup"><span data-stu-id="04f95-155">Local.</span></span> <span data-ttu-id="04f95-156">세션 구성의 보안 설명자에 **Network_Deny_All** 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-156">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="04f95-157">로컬 컴퓨터의 사용자는 세션 구성을 사용 하 여 동일한 컴퓨터에 로컬 루프백 세션을 만들 수 있지만 원격 사용자는 액세스가 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-157">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="04f95-158">리모콘.</span><span class="sxs-lookup"><span data-stu-id="04f95-158">Remote.</span></span> <span data-ttu-id="04f95-159">세션 구성의 보안 설명자에서 **Deny_All** 및 **Network_Deny_All** 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-159">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="04f95-160">로컬 및 원격 컴퓨터의 사용자가 세션 구성을 사용하여 이 컴퓨터에서 세션을 만들고 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-160">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="04f95-161">기본값은 **Remote** 입니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-161">The default value is **Remote**.</span></span>

<span data-ttu-id="04f95-162">다른 cmdlet은 나중에이 매개 변수의 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-162">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="04f95-163">예를 들어 `Enable-PSRemoting` cmdlet은 컴퓨터의 모든 세션 구성을 사용 하도록 설정 하 고 원격 액세스를 허용 하며, `Disable-PSRemoting` cmdlet은 컴퓨터의 모든 세션 구성에 대 한 로컬 액세스만 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-163">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="04f95-164">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-164">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-165">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="04f95-165">-ApplicationBase</span></span>

<span data-ttu-id="04f95-166">\* **AssemblyName** 매개 변수 값에 지정 된 어셈블리 파일 (.dll)의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-166">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-167">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="04f95-167">-AssemblyName</span></span>

<span data-ttu-id="04f95-168">어셈블리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-168">Specifies the assembly name.</span></span> <span data-ttu-id="04f95-169">이 cmdlet은 어셈블리에 정의 된 클래스를 기반으로 하 여 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-169">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="04f95-170">세션 구성을 정의 하는 어셈블리 .dll 파일의 파일 이름 또는 전체 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-170">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="04f95-171">파일 이름만 입력 하는 경우 **ApplicationBase** 매개 변수 값에 경로를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-171">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-172">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="04f95-172">-ConfigurationTypeName</span></span>

<span data-ttu-id="04f95-173">**AssemblyName** 매개 변수의 어셈블리에 정의된 세션 구성의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-173">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="04f95-174">지정한 유형은 **System.Management.Automation.Remoting.PSSessionConfiguration** 클래스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-174">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="04f95-175">이 매개 변수는 어셈블리 이름을 지정할 때 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-175">This parameter is required when you specify an assembly name.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-176">-Force</span><span class="sxs-lookup"><span data-stu-id="04f95-176">-Force</span></span>

<span data-ttu-id="04f95-177">모든 사용자 프롬프트를 표시 하지 않고 **WinRM** 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-177">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="04f95-178">서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-178">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="04f95-179">다시 시작하지 않고 다시 시작 프롬프트를 표시하지 않으려면 **NoServiceRestart** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-179">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="04f95-180">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="04f95-180">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="04f95-181">단일 원격 명령으로이 컴퓨터에 보낼 수 있는 데이터 양에 대 한 제한을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-181">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="04f95-182">데이터 크기를 MB 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="04f95-182">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="04f95-183">기본값은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-183">The default is 50 MB.</span></span>

<span data-ttu-id="04f95-184">**Configurationtypename** 매개 변수에 지정 된 구성 유형에 데이터 크기 제한이 정의 되어 있으면 구성 유형의 제한이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-184">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="04f95-185">이 매개 변수 값은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-185">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-186">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="04f95-186">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="04f95-187">단일 개체에서이 컴퓨터에 보낼 수 있는 데이터 양에 대 한 제한을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-187">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="04f95-188">데이터 크기 (mb)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-188">Enter the data size in megabytes.</span></span> <span data-ttu-id="04f95-189">기본값은 10MB입니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-189">The default is 10 MB.</span></span>

<span data-ttu-id="04f95-190">**Configurationtypename** 매개 변수에 지정 된 구성 유형에 개체 크기 제한이 정의 되어 있으면 구성 유형의 제한이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-190">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="04f95-191">이 매개 변수 값은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-191">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-192">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="04f95-192">-ModulesToImport</span></span>

<span data-ttu-id="04f95-193">세션 구성을 사용하는 세션에 자동으로 가져오는 모듈 및 스냅인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-193">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="04f95-194">모듈 및 스냅인 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-194">Enter the module and snap-in names.</span></span>

<span data-ttu-id="04f95-195">기본적으로 **Microsoft. PowerShell. 코어** 스냅인만 세션으로 가져오지만, cmdlet을 제외 하지 않으면 `Import-Module` 및 Add-PSSnapin cmdlet을 사용 하 여 모듈 및 스냅인을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-195">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="04f95-196">이 매개 변수 값에 지정 된 모듈은 세션 구성 파일 ()에 지정 된 모듈에 추가 하 여 가져옵니다 `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="04f95-196">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="04f95-197">그러나 세션 구성 파일의 설정은 모듈에서 내보낸 명령을 숨기거나 사용자가 명령을 사용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-197">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="04f95-198">이 매개 변수 값에 지정 된 모듈은 cmdlet의 **ModulesToImport** 매개 변수를 사용 하 여 지정 된 모듈 목록을 바꿉니다 `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="04f95-198">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="04f95-199">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-199">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-200">-Name</span><span class="sxs-lookup"><span data-stu-id="04f95-200">-Name</span></span>

<span data-ttu-id="04f95-201">변경할 세션 구성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-201">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="04f95-202">이 매개 변수를 사용하여 세션 구성의 이름을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-202">You cannot use this parameter to change the name of the session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-203">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="04f95-203">-NoServiceRestart</span></span>

<span data-ttu-id="04f95-204">**WinRM** 서비스를 다시 시작 하지 않고 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-204">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="04f95-205">기본적으로를 실행할 때 `Set-PSSessionConfiguration` 새 세션 구성을 적용 하려면 **WinRM** 서비스를 다시 시작 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-205">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="04f95-206">**WinRM** 서비스를 다시 시작할 때까지 새 세션 구성이 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-206">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="04f95-207">메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-207">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="04f95-208">**WinRM** 서비스를 수동으로 다시 시작 하려면 cmdlet을 사용 합니다 `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="04f95-208">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="04f95-209">-Path</span><span class="sxs-lookup"><span data-stu-id="04f95-209">-Path</span></span>

<span data-ttu-id="04f95-210">Cmdlet에서 만든 것과 같은 세션 구성 파일 (.psc)의 경로를 지정 합니다. `New-PSSessionConfigurationFile`</span><span class="sxs-lookup"><span data-stu-id="04f95-210">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="04f95-211">경로를 생략할 경우 기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-211">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="04f95-212">세션 구성 파일을 수정 하는 방법에 대 한 자세한 내용은 cmdlet에 대 한 도움말 항목을 참조 하십시오 `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="04f95-212">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="04f95-213">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-213">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-214">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="04f95-214">-PSVersion</span></span>

<span data-ttu-id="04f95-215">이 세션 구성을 사용 하는 세션의 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-215">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="04f95-216">이 매개 변수 값은 세션 구성 파일에 있는 **PowerShellVersion** 키의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-216">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="04f95-217">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-217">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-218">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="04f95-218">-RunAsCredential</span></span>

<span data-ttu-id="04f95-219">세션의 명령에 대 한 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-219">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="04f95-220">기본적으로 명령은 현재 사용자의 사용 권한으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-220">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="04f95-221">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-221">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-222">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="04f95-222">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="04f95-223">구성에 대해 다른 SDDL(Security Descriptor Definition Language) 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-223">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="04f95-224">이 문자열은 새 세션 구성을 사용하는 데 필요한 권한을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-224">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="04f95-225">세션에서 세션 구성을 사용 하려면 사용자에 게 구성에 대 한 Execute (Invoke) 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-225">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="04f95-226">구성에 대 한 기본 보안 설명자를 사용 하려면 빈 문자열 ("") 또는 값을 입력 `$Null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-226">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="04f95-227">기본값은 WSMan: 드라이브의 루트 SDDL입니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-227">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="04f95-228">보안 설명자가 복잡 한 경우이 매개 변수 대신 **ShowSecurityDescriptorUI** 매개 변수를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-228">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="04f95-229">동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-229">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="04f95-230">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="04f95-230">-SessionTypeOption</span></span>

<span data-ttu-id="04f95-231">세션 구성에 대 한 유형별 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-231">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="04f95-232">Cmdlet에서 반환 하는 **Psworkflowexecutionoption** 개체와 같은 세션 유형 옵션 개체를 입력 `New-PSWorkflowExecutionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-232">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="04f95-233">세션 구성을 사용하는 세션의 옵션은 세션 옵션 값과 세션 구성 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-233">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="04f95-234">지정 하지 않은 경우에는 cmdlet을 사용 하는 등의 방법으로 세션에 설정 된 옵션이 `New-PSSessionOption` 세션 구성에 설정 된 옵션 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-234">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="04f95-235">그러나 세션 옵션 값은 세션 구성에서 설정된 최대값을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-235">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="04f95-236">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-236">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-237">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="04f95-237">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="04f95-238">이 cmdlet이 세션 구성에 대 한 새 SDDL을 만드는 데 도움이 되는 속성 시트 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-238">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="04f95-239">속성 시트는 명령을 실행 한 `Set-PSSessionConfiguration` 다음 **WinRM** 서비스를 다시 시작 하면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-239">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="04f95-240">구성에 대 한 사용 권한을 설정 하는 경우 세션에서 세션 구성을 사용 하려면 사용자에 게 적어도 실행 (호출) 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-240">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="04f95-241">동일한 명령에 **SecurityDescriptorSDDL** 매개 변수와 이 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-241">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="04f95-242">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="04f95-242">-StartupScript</span></span>

<span data-ttu-id="04f95-243">구성에 대 한 시작 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-243">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="04f95-244">PowerShell 스크립트의 정규화 된 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-244">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="04f95-245">지정한 스크립트는 세션 구성을 사용하는 새 세션에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-245">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="04f95-246">세션 구성에서 시작 스크립트를 삭제 하려면 빈 문자열 ("") 또는 값을 입력 `$Null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-246">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="04f95-247">시작 스크립트를 사용 하 여 사용자 세션을 추가로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-247">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="04f95-248">종료 되지 않은 오류를 포함 하 여 스크립트에서 오류를 생성 하는 경우 세션은 만들어지지 않으며 `New-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-248">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="04f95-249">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="04f95-249">-ThreadOptions</span></span>

<span data-ttu-id="04f95-250">구성의 스레드 옵션 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-250">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="04f95-251">이 설정은 세션에서 명령을 실행할 때 스레드가 만들어져 사용되는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-251">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="04f95-252">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="04f95-253">기본값</span><span class="sxs-lookup"><span data-stu-id="04f95-253">Default</span></span>
- <span data-ttu-id="04f95-254">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="04f95-254">ReuseThread</span></span>
- <span data-ttu-id="04f95-255">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="04f95-255">UseCurrentThread</span></span>
- <span data-ttu-id="04f95-256">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="04f95-256">UseNewThread</span></span>

<span data-ttu-id="04f95-257">기본값은 **UseCurrentThread** 입니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-257">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="04f95-258">자세한 내용은 [Psthreadoptions 열거](/dotnet/api/system.management.automation.runspaces.psthreadoptions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04f95-258">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-259">-로 옵션</span><span class="sxs-lookup"><span data-stu-id="04f95-259">-TransportOption</span></span>

<span data-ttu-id="04f95-260">세션 구성에 대 한 전송 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-260">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="04f95-261">Cmdlet이 반환 하는 **Wsmanconfigurationoption** 개체와 같은 전송 옵션 개체를 입력 `New-PSTransportOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-261">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="04f95-262">세션 구성을 사용하는 세션의 옵션은 세션 옵션 값과 세션 구성 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-262">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="04f95-263">지정 하지 않은 경우에는 cmdlet을 사용 하는 등의 방법으로 세션에 설정 된 옵션이 `New-PSSessionOption` 세션 구성에 설정 된 옵션 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-263">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="04f95-264">그러나 세션 옵션 값은 세션 구성에서 설정된 최대값을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-264">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="04f95-265">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-265">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-266">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="04f95-266">-UseSharedProcess</span></span>

<span data-ttu-id="04f95-267">한 프로세스만 사용 하 여 동일한 사용자에 의해 시작 되 고 동일한 세션 구성을 사용 하는 모든 세션을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-267">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="04f95-268">기본적으로 각 세션은 해당 프로세스에 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-268">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="04f95-269">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-269">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="04f95-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="04f95-270">-Confirm</span></span>

<span data-ttu-id="04f95-271">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-271">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="04f95-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="04f95-272">-WhatIf</span></span>

<span data-ttu-id="04f95-273">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-273">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="04f95-274">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-274">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="04f95-275">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="04f95-275">-ThreadApartmentState</span></span>

<span data-ttu-id="04f95-276">사용할 스레딩 모듈의 아파트 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-276">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="04f95-277">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="04f95-277">Acceptable values are:</span></span>

- <span data-ttu-id="04f95-278">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="04f95-278">Unknown</span></span>
- <span data-ttu-id="04f95-279">MTA</span><span class="sxs-lookup"><span data-stu-id="04f95-279">MTA</span></span>
- <span data-ttu-id="04f95-280">STA</span><span class="sxs-lookup"><span data-stu-id="04f95-280">STA</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04f95-281">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="04f95-281">CommonParameters</span></span>

<span data-ttu-id="04f95-282">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="04f95-282">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="04f95-283">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04f95-283">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="04f95-284">입력</span><span class="sxs-lookup"><span data-stu-id="04f95-284">INPUTS</span></span>

### <span data-ttu-id="04f95-285">없음</span><span class="sxs-lookup"><span data-stu-id="04f95-285">None</span></span>

<span data-ttu-id="04f95-286">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-286">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="04f95-287">출력</span><span class="sxs-lookup"><span data-stu-id="04f95-287">OUTPUTS</span></span>

### <span data-ttu-id="04f95-288">WSManConfigLeafElement.</span><span class="sxs-lookup"><span data-stu-id="04f95-288">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="04f95-289">참고</span><span class="sxs-lookup"><span data-stu-id="04f95-289">NOTES</span></span>

<span data-ttu-id="04f95-290">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-290">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="04f95-291">이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-291">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="04f95-292">`Set-PSSessionConfiguration`Cmdlet는 구성 이름을 변경 하지 않으며 **WSMan** 공급자는이 cmdlet을 지원 하지 않습니다 `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="04f95-292">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="04f95-293">세션 구성의 이름을 변경 하려면 cmdlet을 사용 하 여 `Unregister-PSSessionConfiguration` 구성을 삭제 한 다음 cmdlet을 사용 하 여 `Register-PSSessionConfiguration` 새 세션 구성을 만들고 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-293">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="04f95-294">Cmdlet을 사용 하 여 `Set-PSSessionConfiguration` 기본 microsoft.powershell32 세션 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-294">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="04f95-295">이 구성은 보호되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-295">They are not protected.</span></span> <span data-ttu-id="04f95-296">기본 세션 구성의 원래 버전으로 되돌리려면 cmdlet을 사용 하 여 `Unregister-PSSessionConfiguration` 기본 세션 구성을 삭제 한 다음 cmdlet을 사용 하 여 `Enable-PSRemoting` 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-296">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="04f95-297">세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="04f95-298">또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="04f95-299">WSMan: 드라이브에서 명령을 사용하여 세션 구성의 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-299">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="04f95-300">그러나 powershell 2.0의 WSMan: 드라이브를 사용 하 여 **OutputBufferingMode** 와 같은 powershell 3.0에 도입 된 세션 구성 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-300">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="04f95-301">Windows PowerShell 2.0 명령은 오류를 생성하지 않지만 이런 시도가 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-301">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="04f95-302">PowerShell 3.0에 도입 된 속성을 변경 하려면 PowerShell 3.0에서 WSMan: 드라이브를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f95-302">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="04f95-303">관련 링크</span><span class="sxs-lookup"><span data-stu-id="04f95-303">RELATED LINKS</span></span>

[<span data-ttu-id="04f95-304">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04f95-304">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="04f95-305">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04f95-305">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="04f95-306">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04f95-306">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="04f95-307">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="04f95-307">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="04f95-308">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="04f95-308">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="04f95-309">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="04f95-309">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="04f95-310">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04f95-310">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="04f95-311">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="04f95-311">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="04f95-312">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04f95-312">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="04f95-313">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="04f95-313">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="04f95-314">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="04f95-314">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="04f95-315">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="04f95-315">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
