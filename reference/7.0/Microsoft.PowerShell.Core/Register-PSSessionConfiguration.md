---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: c72641c73851521ceb3b696e8eda5ad02a4e46d2
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347519"
---
# <span data-ttu-id="53234-103">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53234-103">Register-PSSessionConfiguration</span></span>

## <span data-ttu-id="53234-104">개요</span><span class="sxs-lookup"><span data-stu-id="53234-104">SYNOPSIS</span></span>
<span data-ttu-id="53234-105">새 세션 구성을 만들어 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-105">Creates and registers a new session configuration.</span></span>

## <span data-ttu-id="53234-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="53234-106">SYNTAX</span></span>

### <span data-ttu-id="53234-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="53234-107">NameParameterSet (Default)</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="53234-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="53234-108">AssemblyNameParameterSet</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="53234-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="53234-109">SessionConfigurationFile</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="53234-110">설명</span><span class="sxs-lookup"><span data-stu-id="53234-110">DESCRIPTION</span></span>

<span data-ttu-id="53234-111">`Register-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에 새 세션 구성을 만들어 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-111">The `Register-PSSessionConfiguration` cmdlet creates and registers a new session configuration on the local computer.</span></span> <span data-ttu-id="53234-112">이 cmdlet은 원격 사용자에 대 한 사용자 지정 세션을 만드는 데 사용할 수 있는 고급 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-112">This is an advanced cmdlet that you can use to create custom sessions for remote users.</span></span>

<span data-ttu-id="53234-113">모든 PowerShell 세션 ( **PSSession** )은 끝점 이라고 하는 세션 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-113">Every PowerShell session ( **PSSession** ) uses a session configuration, also known as an endpoint.</span></span>
<span data-ttu-id="53234-114">사용자가 컴퓨터에 연결 하는 세션을 만드는 경우 세션 구성을 선택 하거나 PowerShell 원격을 사용 하도록 설정할 때 등록 된 기본 세션 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-114">When users create a session that connects to the computer, they can select a session configuration or use the default session configuration that is registered when you enable PowerShell remoting.</span></span>
<span data-ttu-id="53234-115">현재 세션에서 만들어진 원격 세션에 대한 기본 구성을 지정하는 $PSSessionConfigurationName 기본 설정 변수를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-115">Users can also set the $PSSessionConfigurationName preference variable, which specifies a default configuration for remote sessions created in the current session.</span></span>

<span data-ttu-id="53234-116">세션 구성은 원격 세션에 대한 환경을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-116">The session configuration defines the environment for the remote session.</span></span> <span data-ttu-id="53234-117">구성에 따라 세션에서 사용 가능한 명령 및 언어가 결정되며, 세션이 하나의 개체나 명령을 통해 원격으로 받을 수 있는 데이터양을 제한하는 설정과 같이 컴퓨터를 보호하는 설정이 구성에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-117">The configuration can determine which commands and language elements are available in the session, and it can include settings that protect the computer, such as those that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="53234-118">세션 구성의 보안 설명자는 세션 구성을 사용할 권한이 있는 사용자를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-118">The security descriptor of the session configuration determines which users have permission to use the session configuration.</span></span>

<span data-ttu-id="53234-119">새 구성 클래스를 구현하는 어셈블리와 세션에서 실행되는 스크립트를 사용하여 구성 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-119">You can define the elements of configuration by using an assembly that implements a new configuration class and by using a script that runs in the session.</span></span> <span data-ttu-id="53234-120">PowerShell 3.0부터 세션 구성 파일을 사용 하 여 세션 구성을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-120">Beginning in PowerShell 3.0, you can also use a session configuration file to define the session configuration.</span></span>

<span data-ttu-id="53234-121">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-121">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>
<span data-ttu-id="53234-122">세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-122">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

## <span data-ttu-id="53234-123">예제</span><span class="sxs-lookup"><span data-stu-id="53234-123">EXAMPLES</span></span>

### <span data-ttu-id="53234-124">예제 1: NewShell 세션 구성 등록</span><span class="sxs-lookup"><span data-stu-id="53234-124">Example 1: Register a NewShell session configuration</span></span>

<span data-ttu-id="53234-125">이 예제에서는 **Newshell** 세션 구성을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-125">In this example, we register the **NewShell** session configuration.</span></span> <span data-ttu-id="53234-126">**AssemblyName** 및 **ApplicationBase** 매개 변수는 세션 구성에서 cmdlet 및 공급자를 지정 하는 **MyShell.dll** 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-126">The **AssemblyName** and **ApplicationBase** parameters specify the location of the **MyShell.dll** file, which specifies the cmdlets and providers in the session configuration.</span></span> <span data-ttu-id="53234-127">**Configurationtypename** 매개 변수는 어셈블리에서 사용할 구성 클래스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-127">The **ConfigurationTypeName** parameter specifies the configuration class to use from the assembly.</span></span>

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

<span data-ttu-id="53234-128">이 구성을 사용 하려면을 입력 `New-PSSession -ConfigurationName newshell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-128">To use this configuration, type `New-PSSession -ConfigurationName newshell`.</span></span>

### <span data-ttu-id="53234-129">예제 2: MaintenanceShell 세션 구성 등록</span><span class="sxs-lookup"><span data-stu-id="53234-129">Example 2: Register a MaintenanceShell session configuration</span></span>

<span data-ttu-id="53234-130">이 예에서는 로컬 컴퓨터에 **MaintenanceShell** 세션 구성을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-130">This example registers the **MaintenanceShell** session configuration on the local computer.</span></span> <span data-ttu-id="53234-131">**Startupscript** 매개 변수는 스크립트를 지정 합니다 `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="53234-131">The **StartupScript** parameter specifies the `Maintenance.ps1` script.</span></span>

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

<span data-ttu-id="53234-132">사용자가 명령을 사용 하 `New-PSSession` 고 **MaintenanceShell** 구성을 선택 하면 `Maintenance.ps1` 스크립트는 새 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-132">When a user uses a `New-PSSession` command and selects the **MaintenanceShell** configuration, the `Maintenance.ps1` script runs in the new session.</span></span> <span data-ttu-id="53234-133">스크립트에서 세션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-133">The script can configure the session.</span></span> <span data-ttu-id="53234-134">여기에는 모듈 가져오기 및 세션에 대 한 실행 정책 설정이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-134">This includes importing modules and setting the execution policy for the session.</span></span> <span data-ttu-id="53234-135">종료 되지 않는 오류를 포함 하 여 스크립트에서 오류를 생성 하는 경우 `New-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-135">If the script generates any errors, including non-terminating errors, the `New-PSSession` command fails.</span></span>

### <span data-ttu-id="53234-136">예제 3: 세션 구성 등록</span><span class="sxs-lookup"><span data-stu-id="53234-136">Example 3: Register a session configuration</span></span>

<span data-ttu-id="53234-137">이 예제에서는 **Adminshell** 세션 구성을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-137">This example registers the **AdminShell** session configuration.</span></span>

<span data-ttu-id="53234-138">`$sessionParams`변수는 모든 매개 변수 값을 포함 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-138">The `$sessionParams` variable is a hashtable containing all the parameter values.</span></span> <span data-ttu-id="53234-139">이 해시 테이블은 PowerShell 스 플랫을 사용 하 여 cmdlet에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-139">This hashtable is passed to the cmdlet using PowerShell splatting.</span></span> <span data-ttu-id="53234-140">이 `Register-PSSessionConfiguration` 명령은 **SecurityDescritorSDDL** 매개 변수를 사용 하 여 변수 값에 SDDL을 지정 하 `$sddl` 고 **MaximumReceivedObjectSizeMB** 매개 변수를 사용 하 여 개체 크기 제한을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="53234-140">The `Register-PSSessionConfiguration` command uses the **SecurityDescritorSDDL** parameter to specify the SDDL in the value of the `$sddl` variable and the **MaximumReceivedObjectSizeMB** parameter to increase the object size limit.</span></span> <span data-ttu-id="53234-141">또한 **StartupScript** 매개 변수를 사용하여 세션을 구성하는 스크립트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-141">It also uses the **StartupScript** parameter to specify a script that configures the session.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### <span data-ttu-id="53234-142">예제 4: 구성 컨테이너 요소 반환</span><span class="sxs-lookup"><span data-stu-id="53234-142">Example 4: Return a configuration container element</span></span>

<span data-ttu-id="53234-143">이 예제에서는 **MaintenanceShell** 구성을 등록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53234-143">This example shows how to register the **MaintenanceShell** configuration.</span></span>
<span data-ttu-id="53234-144">`Register-PSSessionConfiguration` 변수에 저장 된 **에서 wsmanconfigcontainerelement가** 개체를 반환 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-144">`Register-PSSessionConfiguration` returns a **WSManConfigContainerElement** object stored in the `$s` variable.</span></span> <span data-ttu-id="53234-145">`Format-List` 반환 된 개체의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-145">`Format-List` displays all the properties of the returned object.</span></span> <span data-ttu-id="53234-146">**PSPath** 속성은 개체가 WSMan: 드라이브의 디렉터리에 저장됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53234-146">The **PSPath** property shows that the object is stored in a directory of the WSMan: drive.</span></span> <span data-ttu-id="53234-147">`Get-ChildItem` (별칭 `dir` ) 경로의 항목을 표시 합니다 `WSMan:\LocalHost\PlugIn` .</span><span class="sxs-lookup"><span data-stu-id="53234-147">`Get-ChildItem` (alias `dir`) displays the items in the `WSMan:\LocalHost\PlugIn` path.</span></span> <span data-ttu-id="53234-148">여기에는 새로운 **MaintenanceShell** 구성과 PowerShell과 함께 제공 되는 두 가지 기본 구성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-148">These include the new **MaintenanceShell** configuration and the two default configurations that come with PowerShell.</span></span>

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### <span data-ttu-id="53234-149">예 5: 시작 스크립트를 사용 하 여 세션 구성 등록</span><span class="sxs-lookup"><span data-stu-id="53234-149">Example 5: Register a session configuration with a startup script</span></span>

<span data-ttu-id="53234-150">이 예제에서는 **Withprofile** 세션 구성을 만들고 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-150">In this example we create and register the **WithProfile** session configuration.</span></span> <span data-ttu-id="53234-151">**Startupscript** 매개 변수는 세션 구성을 사용 하는 모든 세션에 대해 지정 된 스크립트를 실행 하도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-151">The **StartupScript** parameter directs PowerShell to run the specified script for any session that uses the session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

<span data-ttu-id="53234-152">스크립트에는 도트 소싱을 사용하여 현재 세션 범위에서 사용자의 **CurrentUserAllHosts** 프로필을 실행하는 하나의 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-152">The script contains a single command that uses dot sourcing to run the user's **CurrentUserAllHosts** profile in the current scope of the session.</span></span>

<span data-ttu-id="53234-153">프로필에 대한 자세한 내용은 [about_Profiles](./About/about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-153">For more information about profiles, see [about_Profiles](./About/about_Profiles.md).</span></span> <span data-ttu-id="53234-154">도트 소싱에 대한 자세한 내용은 [about_Scopes](./About/about_Scopes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-154">For more information about dot sourcing, see [about_Scopes](./About/about_Scopes.md).</span></span>

## <span data-ttu-id="53234-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53234-155">PARAMETERS</span></span>

### <span data-ttu-id="53234-156">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="53234-156">-AccessMode</span></span>

<span data-ttu-id="53234-157">세션 구성을 사용하거나 사용하지 않도록 설정하고 컴퓨터에서 원격 또는 로컬 세션에 사용할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-157">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="53234-158">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-158">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="53234-159">사용 안 함.</span><span class="sxs-lookup"><span data-stu-id="53234-159">Disabled.</span></span> <span data-ttu-id="53234-160">세션 구성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-160">Disables the session configuration.</span></span> <span data-ttu-id="53234-161">컴퓨터에 대한 원격 또는 로컬 액세스에 세션 구성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-161">It cannot be used for remote or local access to the computer.</span></span>
- <span data-ttu-id="53234-162">로컬.</span><span class="sxs-lookup"><span data-stu-id="53234-162">Local.</span></span> <span data-ttu-id="53234-163">로컬 컴퓨터의 사용자가 세션 구성을 사용 하 여 동일한 컴퓨터에 로컬 루프백 세션을 만들 수 있지만 원격 사용자에 대 한 액세스를 거부 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-163">Allows users of the local computer to use the session configuration to create a local loopback session on the same computer, but denies access to remote users.</span></span>
- <span data-ttu-id="53234-164">리모콘.</span><span class="sxs-lookup"><span data-stu-id="53234-164">Remote.</span></span> <span data-ttu-id="53234-165">로컬 및 원격 컴퓨터의 사용자가 세션 구성을 사용하여 이 컴퓨터에서 세션을 만들고 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-165">Allows local and remote users to use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="53234-166">기본값은 Remote입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-166">The default value is Remote.</span></span>

<span data-ttu-id="53234-167">다른 cmdlet은 나중에이 매개 변수의 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-167">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="53234-168">예를 들어 `Enable-PSRemoting` cmdlet은 모든 세션 구성에 대 한 원격 액세스를 허용 하 `Enable-PSSessionConfiguration` 고, cmdlet은 세션 구성을 사용 하도록 설정 하 고, `Disable-PSRemoting` cmdlet은 모든 세션 구성에 대 한 원격 액세스를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-168">For example, the `Enable-PSRemoting` cmdlet allows for remote access to all session configurations, the `Enable-PSSessionConfiguration` cmdlet enables session configurations, and the `Disable-PSRemoting` cmdlet prevents remote access to all session configurations.</span></span>

<span data-ttu-id="53234-169">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-169">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-170">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="53234-170">-ApplicationBase</span></span>

<span data-ttu-id="53234-171">\* **AssemblyName** 매개 변수 값에 지정 된 어셈블리 파일 (.dll)의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-171">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span> <span data-ttu-id="53234-172">**AssemblyName** 매개 변수 값에 경로가 포함되지 않은 경우 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-172">Use this parameter when the value of the **AssemblyName** parameter does not include a path.</span></span> <span data-ttu-id="53234-173">기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-173">The default is the current directory.</span></span>

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

### <span data-ttu-id="53234-174">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="53234-174">-AssemblyName</span></span>

<span data-ttu-id="53234-175">구성 형식이 정의 된 어셈블리 파일 (.dll)의 이름을 지정 합니다 \* .</span><span class="sxs-lookup"><span data-stu-id="53234-175">Specifies the name of an assembly file (\*.dll) in which the configuration type is defined.</span></span> <span data-ttu-id="53234-176">이 매개 변수 또는 **ApplicationBase** 매개 변수 값에서 .dll의 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-176">You can specify the path of the .dll in this parameter or in the value of the **ApplicationBase** parameter.</span></span>

<span data-ttu-id="53234-177">**Configurationtypename** 매개 변수를 지정 하는 경우이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-177">This parameter is required when you specify the **ConfigurationTypeName** parameter.</span></span>

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

### <span data-ttu-id="53234-178">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="53234-178">-ConfigurationTypeName</span></span>

<span data-ttu-id="53234-179">이 구성에 사용되는 Microsoft .NET Framework 유형의 정규화된 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-179">Specifies the fully qualified name of the Microsoft .NET Framework type that is used for this configuration.</span></span> <span data-ttu-id="53234-180">지정한 유형은 **System.Management.Automation.Remoting.PSSessionConfiguration** 클래스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-180">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="53234-181">\*구성 유형을 구현 하는 어셈블리 파일 (.dll)을 지정 하려면 **AssemblyName** 및 **ApplicationBase** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-181">To specify the assembly file (\*.dll) that implements the configuration type, specify the **AssemblyName** and **ApplicationBase** parameters.</span></span>

<span data-ttu-id="53234-182">유형을 만들면 cmdlet의 특정 매개 변수를 표시 또는 숨기 거 나 사용자가 재정의할 수 없는 데이터 크기 및 개체 크기 제한을 설정 하는 등 세션 구성의 여러 측면을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-182">Creating a type lets you control more aspects of the session configuration, such as exposing or hiding certain parameters of cmdlets, or setting data size and object size limits that users cannot override.</span></span>

<span data-ttu-id="53234-183">이 매개 변수를 생략하면 **DefaultRemotePowerShellConfiguration** 클래스가 세션 구성에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-183">If you omit this parameter, the **DefaultRemotePowerShellConfiguration** class is used for the session configuration.</span></span>

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

### <span data-ttu-id="53234-184">-Force</span><span class="sxs-lookup"><span data-stu-id="53234-184">-Force</span></span>

<span data-ttu-id="53234-185">모든 사용자 프롬프트를 표시 하지 않고 **WinRM** 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-185">Suppresses all user prompts and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="53234-186">서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-186">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="53234-187">다시 시작을 방지 하 고 다시 시작 메시지를 표시 하지 않으려면 **NoServiceRestart** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-187">To prevent a restart and suppress the restart prompt, specify the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="53234-188">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="53234-188">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="53234-189">단일 원격 명령으로이 컴퓨터에 보낼 수 있는 데이터 양에 대 한 제한을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-189">Specifies a limit for the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="53234-190">데이터 크기를 MB 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-190">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="53234-191">기본값은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-191">The default is 50 MB.</span></span>

<span data-ttu-id="53234-192">**ConfigurationTypeName** 매개 변수에 지정된 구성 유형에 데이터 크기 제한이 정의되어 있을 경우 구성 유형의 제한이 사용되고 이 매개 변수 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-192">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="53234-193">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="53234-193">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="53234-194">단일 개체에서이 컴퓨터에 보낼 수 있는 데이터 양에 대 한 제한을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-194">Specifies a limit for the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="53234-195">데이터 크기 (mb)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-195">Enter the data size in megabytes.</span></span> <span data-ttu-id="53234-196">기본값은 10MB입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-196">The default is 10 MB.</span></span>

<span data-ttu-id="53234-197">**ConfigurationTypeName** 매개 변수에 지정된 구성 유형에 개체 크기 제한이 정의되어 있을 경우 구성 유형의 제한이 사용되고 이 매개 변수 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-197">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53234-198">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="53234-198">-ModulesToImport</span></span>

<span data-ttu-id="53234-199">세션 구성을 사용 하는 세션에 자동으로 가져오는 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-199">Specifies the modules that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="53234-200">기본적으로 **Microsoft. PowerShell. Core** 만 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="53234-200">By default, only **Microsoft.PowerShell.Core** is imported into sessions.</span></span> <span data-ttu-id="53234-201">Cmdlet을 제외 하지 않으면를 사용 하 여 `Import-Module` 세션에 모듈을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-201">Unless the cmdlets are excluded, you can use `Import-Module` to add modules to the session.</span></span>

<span data-ttu-id="53234-202">이 매개 변수 값에 지정 된 모듈은 **SessionType** 매개 변수로 지정 된 모듈과 세션 구성 파일 ()의 **ModulesToImport** 키에 나열 된 모듈에 추가 하 여 가져옵니다 `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="53234-202">The modules specified in this parameter value are imported in additions to modules that are specified by the **SessionType** parameter and those listed in the **ModulesToImport** key in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="53234-203">그러나 세션 구성 파일의 설정은 모듈에서 내보낸 명령을 숨기거나 사용자가 명령을 사용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-203">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="53234-204">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-204">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-205">-Name</span><span class="sxs-lookup"><span data-stu-id="53234-205">-Name</span></span>

<span data-ttu-id="53234-206">세션 구성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-206">Specifies a name for the session configuration.</span></span> <span data-ttu-id="53234-207">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-207">This parameter is required.</span></span>

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

### <span data-ttu-id="53234-208">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="53234-208">-NoServiceRestart</span></span>

<span data-ttu-id="53234-209">**WinRM** 서비스를 다시 시작 하지 않고 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-209">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="53234-210">기본적으로 명령을 실행 하면 `Register-PSSessionConfiguration` **WinRM** 서비스를 다시 시작 하 라는 메시지가 표시 됩니다. 이렇게 하면 새 세션 구성을 효과적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-210">By default, when you run a `Register-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="53234-211">**WinRM** 서비스를 다시 시작할 때까지 새 세션 구성이 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-211">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="53234-212">메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하려면 **Force** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-212">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="53234-213">**WinRM** 서비스를 수동으로 다시 시작 하려면 cmdlet을 사용 합니다 `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="53234-213">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="53234-214">-Path</span><span class="sxs-lookup"><span data-stu-id="53234-214">-Path</span></span>

<span data-ttu-id="53234-215">에서 만든 것과 같은 세션 구성 파일 (.psc)의 경로와 파일 이름을 지정 합니다 `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="53234-215">Specifies the path and filename of a session configuration file (.pssc), such as one created by `New-PSSessionConfigurationFile`.</span></span> <span data-ttu-id="53234-216">경로를 생략할 경우 기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-216">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="53234-217">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-218">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="53234-218">-ProcessorArchitecture</span></span>

<span data-ttu-id="53234-219">이 세션 구성을 사용 하는 세션에서 32 비트 또는 64 비트 버전의 PowerShell 프로세스가 시작 되는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-219">Determines whether a 32-bit or 64-bit version of the PowerShell process is started in sessions that use this session configuration.</span></span> <span data-ttu-id="53234-220">이 매개 변수에 허용 되는 값은 x86 (32 비트) 및 AMD64 (64 비트)입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-220">The acceptable values for this parameter are: x86 (32-bit) and AMD64 (64-bit).</span></span> <span data-ttu-id="53234-221">기본값은 세션 구성을 호스트하는 컴퓨터의 프로세서 아키텍처에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-221">The default value is determined by the processor architecture of the computer that hosts the session configuration.</span></span>

<span data-ttu-id="53234-222">이 매개 변수를 사용하여 64비트 컴퓨터에 32비트 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-222">You can use this parameter to create a 32-bit session on a 64-bit computer.</span></span> <span data-ttu-id="53234-223">32비트 컴퓨터에 64비트 프로세스를 만들려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-223">Attempts to create a 64-bit process on a 32-bit computer fail.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53234-224">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="53234-224">-PSVersion</span></span>

<span data-ttu-id="53234-225">이 세션 구성을 사용 하는 세션의 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-225">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="53234-226">이 매개 변수 값은 세션 구성 파일에 있는 **PowerShellVersion** 키의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-226">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="53234-227">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-228">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="53234-228">-RunAsCredential</span></span>

<span data-ttu-id="53234-229">세션의 명령에 대 한 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-229">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="53234-230">기본적으로 명령은 현재 사용자의 사용 권한으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-230">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="53234-231">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-231">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-232">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="53234-232">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="53234-233">구성에 대한 SDDL(Security Descriptor Definition Language) 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-233">Specifies a Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="53234-234">이 문자열은 새 세션 구성을 사용하는 데 필요한 권한을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-234">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="53234-235">세션에서 세션 구성을 사용 하려면 사용자에 게 구성에 대 한 Execute (Invoke) 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-235">To use a session configuration in a session, users must have at least Execute (Invoke) permission for the configuration.</span></span>

<span data-ttu-id="53234-236">보안 설명자가 복잡한 경우 이 매개 변수 대신 **ShowSecurityDescriptorUI** 매개 변수를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-236">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this parameter.</span></span> <span data-ttu-id="53234-237">동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-237">You cannot use both parameters in the same command.</span></span>

<span data-ttu-id="53234-238">이 매개 변수를 생략 하면 **WinRM** 서비스에 대 한 루트 SDDL이이 구성에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-238">If you omit this parameter, the root SDDL for the **WinRM** service is used for this configuration.</span></span>
<span data-ttu-id="53234-239">루트 SDDL을 보거나 변경하려면 WSMan 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-239">To view or change the root SDDL, use the WSMan provider.</span></span> <span data-ttu-id="53234-240">예: `Get-Item wsman:\localhost\service\rootSDDL`.</span><span class="sxs-lookup"><span data-stu-id="53234-240">For example `Get-Item wsman:\localhost\service\rootSDDL`.</span></span> <span data-ttu-id="53234-241">WSMan 공급자에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="53234-241">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

### <span data-ttu-id="53234-242">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="53234-242">-SessionTypeOption</span></span>

<span data-ttu-id="53234-243">세션 구성에 대 한 유형별 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-243">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="53234-244">Cmdlet에서 반환 하는 **Psworkflowexecutionoption** 개체와 같은 세션 유형 옵션 개체를 입력 `New-PSWorkflowExecutionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-244">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="53234-245">세션 구성을 사용하는 세션의 옵션은 세션 옵션 값과 세션 구성 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-245">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="53234-246">지정 하지 않은 경우에는 cmdlet을 사용 하는 등의 방법으로 세션에 설정 된 옵션이 `New-PSSessionOption` 세션 구성에 설정 된 옵션 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-246">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="53234-247">그러나 세션 옵션 값은 세션 구성에서 설정된 최대값을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-247">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="53234-248">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-248">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-249">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="53234-249">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="53234-250">이 cmdlet이 세션 구성에 대 한 SDDL을 만드는 데 도움이 되는 속성 시트를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="53234-250">Indicates that this cmdlet displays a property sheet that helps you create the SDDL for the session configuration.</span></span> <span data-ttu-id="53234-251">속성 시트는 명령을 입력 한 `Register-PSSessionConfiguration` 다음 **WinRM** 서비스를 다시 시작 하면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53234-251">The property sheet appears after you enter the `Register-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="53234-252">구성에 대 한 사용 권한을 설정 하는 경우 세션에서 세션 구성을 사용 하려면 사용자에 게 적어도 실행 (호출) 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-252">When setting the permissions for the configuration, remember that users must have at least Execute (Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="53234-253">동일한 명령에 **SecurityDescriptorSDDL** 매개 변수와 이 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-253">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="53234-254">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="53234-254">-StartupScript</span></span>

<span data-ttu-id="53234-255">PowerShell 스크립트의 정규화 된 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-255">Specifies the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="53234-256">지정한 스크립트는 세션 구성을 사용하는 새 세션에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-256">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="53234-257">스크립트를 사용 하 여 세션을 추가로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-257">You can use the script to additionally configure the session.</span></span> <span data-ttu-id="53234-258">종료 되지 않은 오류를 포함 하 여 스크립트에서 오류를 생성 하는 경우 세션은 만들어지지 않으며 `New-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-258">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="53234-259">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="53234-259">-ThreadOptions</span></span>

<span data-ttu-id="53234-260">세션에서 명령을 실행할 때 스레드를 만들고 사용 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-260">Specifies how threads are created and used when a command runs in the session.</span></span> <span data-ttu-id="53234-261">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-261">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="53234-262">기본값</span><span class="sxs-lookup"><span data-stu-id="53234-262">Default</span></span>
- <span data-ttu-id="53234-263">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="53234-263">ReuseThread</span></span>
- <span data-ttu-id="53234-264">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="53234-264">UseCurrentThread</span></span>
- <span data-ttu-id="53234-265">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="53234-265">UseNewThread</span></span>

<span data-ttu-id="53234-266">기본값은 **UseCurrentThread** 입니다.</span><span class="sxs-lookup"><span data-stu-id="53234-266">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="53234-267">자세한 내용은 [Psthreadoptions 열거](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-267">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span></span>

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

### <span data-ttu-id="53234-268">-로 옵션</span><span class="sxs-lookup"><span data-stu-id="53234-268">-TransportOption</span></span>

<span data-ttu-id="53234-269">전송 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-269">Specifies the transport option.</span></span>

<span data-ttu-id="53234-270">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-270">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-271">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="53234-271">-UseSharedProcess</span></span>

<span data-ttu-id="53234-272">한 프로세스만 사용 하 여 동일한 사용자에 의해 시작 되 고 동일한 세션 구성을 사용 하는 모든 세션을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-272">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="53234-273">기본적으로 각 세션은 해당 프로세스에 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="53234-273">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="53234-274">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-274">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53234-275">-Confirm</span><span class="sxs-lookup"><span data-stu-id="53234-275">-Confirm</span></span>

<span data-ttu-id="53234-276">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-276">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="53234-277">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="53234-277">-WhatIf</span></span>

<span data-ttu-id="53234-278">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-278">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="53234-279">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-279">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="53234-280">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="53234-280">-ThreadApartmentState</span></span>

<span data-ttu-id="53234-281">사용할 스레딩 모듈의 아파트 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-281">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="53234-282">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="53234-282">Acceptable values are:</span></span>

- <span data-ttu-id="53234-283">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="53234-283">Unknown</span></span>
- <span data-ttu-id="53234-284">MTA</span><span class="sxs-lookup"><span data-stu-id="53234-284">MTA</span></span>
- <span data-ttu-id="53234-285">STA</span><span class="sxs-lookup"><span data-stu-id="53234-285">STA</span></span>

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

### <span data-ttu-id="53234-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53234-286">CommonParameters</span></span>

<span data-ttu-id="53234-287">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53234-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53234-288">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53234-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53234-289">입력</span><span class="sxs-lookup"><span data-stu-id="53234-289">INPUTS</span></span>

### <span data-ttu-id="53234-290">없음</span><span class="sxs-lookup"><span data-stu-id="53234-290">None</span></span>

<span data-ttu-id="53234-291">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-291">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="53234-292">출력</span><span class="sxs-lookup"><span data-stu-id="53234-292">OUTPUTS</span></span>

### <span data-ttu-id="53234-293">에서 wsmanconfigcontainerelement가.</span><span class="sxs-lookup"><span data-stu-id="53234-293">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>

## <span data-ttu-id="53234-294">참고</span><span class="sxs-lookup"><span data-stu-id="53234-294">NOTES</span></span>

<span data-ttu-id="53234-295">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-295">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="53234-296">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53234-296">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="53234-297">이 cmdlet은 WS-MANAGEMENT (Web Services for Management) 플러그 인 구성을 나타내는 XML을 생성 하 고 WS-MANAGEMENT로 XML을 보냅니다 .이는 로컬 컴퓨터 ()에 플러그 인을 등록 합니다 `New-Item wsman:\localhost\plugin` .</span><span class="sxs-lookup"><span data-stu-id="53234-297">This cmdlet generates XML that represents a Web Services for Management (WS-Management) plug-in configuration and sends the XML to WS-Management, which registers the plug-in on the local computer (`New-Item wsman:\localhost\plugin`).</span></span>

<span data-ttu-id="53234-298">세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="53234-298">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="53234-299">또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53234-299">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="53234-300">관련 링크</span><span class="sxs-lookup"><span data-stu-id="53234-300">RELATED LINKS</span></span>

[<span data-ttu-id="53234-301">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53234-301">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="53234-302">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53234-302">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="53234-303">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53234-303">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="53234-304">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="53234-304">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="53234-305">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53234-305">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="53234-306">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="53234-306">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="53234-307">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53234-307">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="53234-308">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="53234-308">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="53234-309">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="53234-309">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="53234-310">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="53234-310">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
