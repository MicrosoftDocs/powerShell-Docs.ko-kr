---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: a5aa70521841b3b05d34623ff92ebbf9e3471fd1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600858"
---
# <span data-ttu-id="846d5-102">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-102">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="846d5-103">개요</span><span class="sxs-lookup"><span data-stu-id="846d5-103">SYNOPSIS</span></span>
<span data-ttu-id="846d5-104">컴퓨터에 등록된 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-104">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="846d5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="846d5-105">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="846d5-106">설명</span><span class="sxs-lookup"><span data-stu-id="846d5-106">DESCRIPTION</span></span>

<span data-ttu-id="846d5-107">`Get-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에 등록 된 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-107">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="846d5-108">이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="846d5-109">PowerShell 3.0부터 세션 구성 (pssc) 파일을 사용 하 여 세션 구성의 속성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-109">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="846d5-110">이 기능을 사용하면 컴퓨터 프로그램은 작성하지 않고도 사용자 지정 및 제한된 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-110">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="846d5-111">세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="846d5-111">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="846d5-112">또한 PowerShell 3.0 부터는에서 반환 하는 세션 구성 개체에 새로운 메모 속성이 추가 되었습니다 `Get-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="846d5-112">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="846d5-113">이러한 속성 덕분에 사용자 및 세션 구성 작성자가 세션 구성을 쉽게 확인하고 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-113">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="846d5-114">세션 구성을 만들고 등록 하려면 cmdlet을 사용 `Register-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-114">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="846d5-115">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="846d5-115">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="846d5-116">예제</span><span class="sxs-lookup"><span data-stu-id="846d5-116">EXAMPLES</span></span>

### <span data-ttu-id="846d5-117">예 1-로컬 컴퓨터에서 세션 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="846d5-117">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="846d5-118">예 2-두 개의 기본 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-118">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="846d5-119">이 명령은의 **Name** 매개 변수를 사용 하 여 `Get-PSSessionConfiguration` 이름이 "Microsoft"로 시작 하는 세션 구성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-119">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="846d5-120">예 3-세션 구성의 속성 및 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="846d5-120">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="846d5-121">이 예제에서는 세션 구성 파일을 사용하여 만든 세션 구성의 속성 및 속성 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-121">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

<span data-ttu-id="846d5-122">이 예에서는 cmdlet을 사용 하 여 `Get-PSSessionConfiguration` 전체 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-122">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="846d5-123">파이프라인 연산자는 전체 세션 구성을 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="846d5-123">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="846d5-124">값이 (모두) 인 **Property** 매개 변수는 `*` `Format-List` 목록에 개체의 모든 속성 및 값을 표시 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-124">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="846d5-125">출력은 세션 구성의 작성자, 세션 유형, 언어 모드,이 세션 구성으로 만든 세션의 실행 정책, 세션 할당량, 세션 구성 파일에 대 한 전체 경로를 포함 하 여 유용한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-125">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="846d5-126">이 세션 구성의 보기는 세션 구성 파일을 포함하는 세션에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-126">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="846d5-127">세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="846d5-127">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="846d5-128">예 4-세션 구성을 확인 하는 다른 방법</span><span class="sxs-lookup"><span data-stu-id="846d5-128">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="846d5-129">이 예에서는 `Get-ChildItem` `dir` WSMan: 공급자 드라이브의 cmdlet (별칭)을 사용 하 여 플러그 인 노드의 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-129">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="846d5-130">이 방법으로 컴퓨터의 세션 구성을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-130">This is another way to look at the session configurations on the computer.</span></span>

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="846d5-131">**플러그 인** 노드에는 ws-management 용 다른 플러그 인과 함께 등록 된 PowerShell 세션 구성을 나타내는 **ContainerElement** 개체 (에서 wsmanconfigcontainerelement가)가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-131">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="846d5-132">예 6-원격 컴퓨터에서 세션 구성 보기</span><span class="sxs-lookup"><span data-stu-id="846d5-132">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="846d5-133">이 예제에서는 WSMan 공급자를 사용하여 원격 컴퓨터에서 세션 구성을 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-133">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="846d5-134">이 메서드는 명령으로 많은 정보를 제공 하지 `Get-PSSessionConfiguration` 않지만이 cmdlet을 실행 하기 위해 사용자가 Administrators 그룹의 멤버가 될 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-134">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="846d5-135">`Connect-WSMan`Cmdlet은 Server01 원격 컴퓨터의 WinRM 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-135">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="846d5-136">`Get-ChildItem` `dir` WSMan: 드라이브의 cmdlet (별칭)은 **Server01\Plugin** 경로에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-136">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="846d5-137">출력에는 Server01 컴퓨터의 Plugin 디렉터리에 있는 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-137">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="846d5-138">이 항목에는 컴퓨터의 다른 플러그 인 유형과 함께 WSMan 플러그 인 유형인 세션 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-138">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="846d5-139">예 7-원격 컴퓨터에서 자세한 세션 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="846d5-139">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="846d5-140">이 예제에서는 `Get-PSSessionConfiguration` 원격 컴퓨터에서 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-140">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="846d5-141">이 명령을 실행하려면 로컬 컴퓨터의 클라이언트 설정과 원격 컴퓨터의 서비스 설정에서 CredSSP 위임을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-141">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="846d5-142">이 예제의 명령을 실행 하려면 로컬 및 원격 컴퓨터에서 Administrators 그룹의 구성원 이어야 하며 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-142">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

<span data-ttu-id="846d5-143">`Enable-WSManCredSSP`Cmdlet은 로컬 컴퓨터인 Server01에서 **CredSSP** 위임을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-143">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="846d5-144">`Connect-WSMan`Cmdlet는 Server02 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-144">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="846d5-145">이 작업은 로컬 컴퓨터의 WSMan: 드라이브에 Server02에 대 한 노드를 추가 하 여 Server02 컴퓨터의 WS-Management 설정을 보고 변경할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-145">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="846d5-146">`Set-Item`Cmdlet은 Server02 컴퓨터의 Service 노드에 있는 **CredSSP** 항목의 값을 **True** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-146">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True**.</span></span> <span data-ttu-id="846d5-147">이렇게 하면 원격 컴퓨터의 서비스 설정이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-147">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="846d5-148">`Invoke-Command`Cmdlet은 `Get-PSSessionConfiguration` Server02 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-148">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="846d5-149">이 명령은 **Credential** 매개 변수를 사용하고 **CredSSP** 값과 함께 **Authentication** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-149">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP**.</span></span> <span data-ttu-id="846d5-150">출력은 Server02 원격 컴퓨터의 세션 구성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-150">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="846d5-151">예 8-세션 구성의 리소스 URI 가져오기</span><span class="sxs-lookup"><span data-stu-id="846d5-151">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="846d5-152">이 예제는 `$PSSessionConfigurationName` 리소스 URI를 사용 하는 기본 설정 변수의 값을 설정 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-152">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="846d5-153">`$PSSessionConfigurationName`변수는 세션을 만들 때 사용 되는 기본 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-153">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="846d5-154">이 변수는 로컬 컴퓨터에 설정되지만 원격 컴퓨터의 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-154">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="846d5-155">변수에 대 한 자세한 내용은 `$PSSessionConfiguration` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="846d5-155">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="846d5-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="846d5-156">PARAMETERS</span></span>

### <span data-ttu-id="846d5-157">-Force</span><span class="sxs-lookup"><span data-stu-id="846d5-157">-Force</span></span>

<span data-ttu-id="846d5-158">서비스가 아직 실행되고 있지 않으면 WinRM 서비스를 다시 시작할 것인지 묻는 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-158">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="846d5-159">-Name</span><span class="sxs-lookup"><span data-stu-id="846d5-159">-Name</span></span>

<span data-ttu-id="846d5-160">지정된 이름이나 이름 패턴의 세션 구성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-160">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="846d5-161">하나 이상의 세션 구성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-161">Enter one or more session configuration names.</span></span> <span data-ttu-id="846d5-162">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-162">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="846d5-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="846d5-163">CommonParameters</span></span>

<span data-ttu-id="846d5-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="846d5-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="846d5-165">자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="846d5-165">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="846d5-166">입력</span><span class="sxs-lookup"><span data-stu-id="846d5-166">INPUTS</span></span>

### <span data-ttu-id="846d5-167">없음</span><span class="sxs-lookup"><span data-stu-id="846d5-167">None</span></span>

<span data-ttu-id="846d5-168">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="846d5-169">출력</span><span class="sxs-lookup"><span data-stu-id="846d5-169">OUTPUTS</span></span>

### <span data-ttu-id="846d5-170">Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-170">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="846d5-171">참고</span><span class="sxs-lookup"><span data-stu-id="846d5-171">NOTES</span></span>

- <span data-ttu-id="846d5-172">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-172">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="846d5-173">컴퓨터의 세션 구성을 보려면 컴퓨터에서 Administrators 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-173">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="846d5-174">`Get-PSSessionConfiguration`원격 컴퓨터에서 명령을 실행 하려면 CredSSP (자격 증명 보안 서비스 공급자) 인증을 로컬 컴퓨터의 클라이언트 설정에서 사용 하도록 설정 해야 합니다 ( `Enable-WSManCredSSP` cmdlet 사용) 및 원격 컴퓨터의 서비스 설정에서 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-174">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="846d5-175">또한 원격 세션을 설정할 때 **인증** 매개 변수의 **CredSSP** 값을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-175">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="846d5-176">그러지 않으면 액세스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-176">Otherwise, access is denied.</span></span>

- <span data-ttu-id="846d5-177">가 반환 하는 개체의 메모 속성은 `Get-PSSessionConfiguration` 값이 있는 경우에만 개체에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-177">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="846d5-178">세션 구성 파일을 사용 하 여 만든 세션 구성에만 정의 된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-178">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="846d5-179">세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-179">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="846d5-180">또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-180">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="846d5-181">WSMan: 드라이브에서 명령을 사용하여 세션 구성의 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-181">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="846d5-182">그러나 powershell 2.0의 WSMan: 드라이브를 사용 하 여 **OutputBufferingMode** 와 같은 powershell 3.0에 도입 된 세션 구성 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-182">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="846d5-183">PowerShell 2.0 명령은 오류를 생성 하지 않지만이는 의미가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-183">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="846d5-184">PowerShell 3.0에 도입 된 속성을 변경 하려면 PowerShell 3.0에서 WSMan: 드라이브를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="846d5-184">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="846d5-185">관련 링크</span><span class="sxs-lookup"><span data-stu-id="846d5-185">RELATED LINKS</span></span>

[<span data-ttu-id="846d5-186">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-186">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="846d5-187">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-187">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="846d5-188">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-188">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="846d5-189">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="846d5-189">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="846d5-190">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="846d5-190">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="846d5-191">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-191">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="846d5-192">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-192">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="846d5-193">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="846d5-193">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="846d5-194">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="846d5-194">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="846d5-195">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="846d5-195">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="846d5-196">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="846d5-196">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="846d5-197">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="846d5-197">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
