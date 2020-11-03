---
description: 컴퓨터에 원격으로 연결할 수 있는 사용자와 실행할 수 있는 명령을 결정하는 세션 구성에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5b59d8fb05ee118f5b2d7b5b859efad9be75814a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220594"
---
# <a name="about-session-configurations"></a><span data-ttu-id="d2223-104">세션 구성 정보</span><span class="sxs-lookup"><span data-stu-id="d2223-104">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="d2223-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="d2223-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d2223-106">컴퓨터에 원격으로 연결할 수 있는 사용자와 실행할 수 있는 명령을 결정하는 세션 구성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-106">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="d2223-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="d2223-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d2223-108">"끝점"이 라고도 하는 세션 구성은 원격 사용자 또는 로컬 사용자가 로컬 컴퓨터의 PowerShell에 연결할 때 생성 되는 PowerShell 세션의 환경을 정의 하는 로컬 컴퓨터의 설정 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-108">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="d2223-109">컴퓨터 관리자는 세션 구성을 사용 하 여 컴퓨터를 보호 하 고 컴퓨터에 연결 하는 사용자에 대 한 사용자 지정 환경을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-109">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="d2223-110">또한 관리자는 세션 구성을 사용 하 여 컴퓨터에 원격으로 연결 하는 데 필요한 권한을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-110">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="d2223-111">기본적으로 Administrators 그룹의 구성원만 세션 구성을 사용 하 여 원격으로 연결 하는 권한을 가지 지만, 모든 사용자 또는 선택한 사용자가 컴퓨터에 원격으로 연결할 수 있도록 기본 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-111">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="d2223-112">PowerShell 3.0부터 세션 구성 파일을 사용 하 여 세션 구성의 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-112">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="d2223-113">이 기능을 사용 하면 코드를 작성 하지 않고 세션을 쉽게 사용자 지정 하 고 세션 구성의 속성을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-113">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="d2223-114">세션 구성 파일을 만들려면 New-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-114">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="d2223-115">세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](about_Session_Configuration_Files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2223-115">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="d2223-116">세션 구성은 WS-MANAGEMENT (Web Services for Management) 기반 PowerShell 원격 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-116">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="d2223-117">이는 새 PSSession, 호출 명령 또는 Enter-PSSession cmdlet을 사용 하 여 원격 컴퓨터에 연결 하는 경우에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-117">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="d2223-118">참고: 세션 구성을 관리 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-118">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="d2223-119">세션 구성 정보</span><span class="sxs-lookup"><span data-stu-id="d2223-119">About Session Configurations</span></span>

<span data-ttu-id="d2223-120">모든 PowerShell 세션은 세션 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-120">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="d2223-121">여기에는 New-PSSession 또는 Enter-PSSession cmdlet을 사용 하 여 만드는 영구 세션과 PowerShell에서 사용 하는 임시 세션 (예: Invoke 명령과 같은 WS-MANAGEMENT 기반 원격 기술을 사용 하는 cmdlet의 ComputerName 매개 변수를 사용 하는 경우)이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-121">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="d2223-122">관리자는 세션 구성을 사용 하 여 컴퓨터의 리소스를 보호 하 고 컴퓨터에 연결 하는 사용자에 대 한 사용자 지정 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-122">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="d2223-123">예를 들어 세션 구성을 사용 하 여 컴퓨터에서 세션에 수신 하는 개체의 크기를 제한 하 고, 세션의 언어 모드를 정의 하 고, 세션에서 사용할 수 있는 cmdlet, 공급자 및 함수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-123">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="d2223-124">세션 구성의 보안 설명자를 구성 하 여 세션 구성을 사용 하 여 컴퓨터에 연결할 수 있는 사용자를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-124">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="d2223-125">세션에서 사용 하려면 사용자에 게 세션 구성에 대 한 Execute 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-125">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="d2223-126">사용자에 게 컴퓨터의 세션 구성을 사용 하는 데 필요한 권한이 없는 경우에는 사용자가 원격으로 컴퓨터에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-126">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="d2223-127">기본적으로 컴퓨터의 관리자 에게만 기본 세션 구성을 사용할 수 있는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-127">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="d2223-128">그러나 보안 설명자를 변경 하 여 모든 사용자가 없거나 선택한 사용자만 컴퓨터에서 세션 구성을 사용할 수 있도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-128">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="d2223-129">기본 제공 세션 구성</span><span class="sxs-lookup"><span data-stu-id="d2223-129">Built-in Session Configurations</span></span>

<span data-ttu-id="d2223-130">PowerShell 3.0에는 Microsoft. PowerShell 및 Microsoft. Workflow 라는 기본 제공 세션 구성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-130">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="d2223-131">64 비트 버전의 Windows를 실행 하는 컴퓨터에서 PowerShell은 Microsoft.powershell32 (32 비트 세션 구성)도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-131">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="d2223-132">Microsoft. PowerShell 세션 구성은 기본적으로 세션에 사용 됩니다. 즉, 세션을 만드는 명령에 새 PSSession, Enter-PSSession 또는 Invoke-Command cmdlet의 ConfigurationName 매개 변수가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-132">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="d2223-133">기본 세션 구성에 대 한 보안 설명자를 사용 하 여 로컬 컴퓨터의 Administrators 그룹 구성원만이를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-133">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="d2223-134">따라서 기본 설정을 변경 하지 않는 한 관리자 그룹의 구성원만 원격으로 컴퓨터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-134">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="d2223-135">$PSSessionConfigurationName 기본 설정 변수를 사용 하 여 기본 세션 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-135">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="d2223-136">자세한 내용은 about_preference_variables를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2223-136">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="d2223-137">로컬 컴퓨터에서 세션 구성 보기</span><span class="sxs-lookup"><span data-stu-id="d2223-137">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="d2223-138">로컬 컴퓨터의 세션 구성을 가져오려면 Get-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-138">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="d2223-139">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-139">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="d2223-140">세션 구성 파일을 사용 하 여 구성 된 세션 구성의 속성을 표시 하기 위해 PowerShell 3.0에서 세션 구성 개체가 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-140">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="d2223-141">예를 들어 세션 구성 개체의 모든 속성을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-141">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="d2223-142">PowerShell에서 WSMan 공급자를 사용 하 여 세션 구성을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-142">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="d2223-143">WSMan 공급자는 세션에 WSMAN: 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-143">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="d2223-144">WSMAN: 드라이브에서 세션 구성은 플러그 인 노드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-144">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="d2223-145">모든 세션 구성은 플러그 인 노드에 있지만 세션 구성이 아닌 플러그 인 노드에 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-145">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="d2223-146">예를 들어 로컬 컴퓨터의 세션 구성을 보려면 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-146">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="d2223-147">원격 컴퓨터에서 세션 구성 보기</span><span class="sxs-lookup"><span data-stu-id="d2223-147">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="d2223-148">원격 컴퓨터의 세션 구성을 보려면 Connect-WSMan cmdlet을 사용 하 여 원격 컴퓨터의 정보를 로컬 컴퓨터의 WSMAN: 드라이브에 추가한 다음 WSMAN: 드라이브를 사용 하 여 세션 구성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-148">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="d2223-149">예를 들어 다음 명령은 로컬 컴퓨터의 WSMAN: 드라이브에 Server01 원격 컴퓨터에 대 한 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-149">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="d2223-150">명령이 완료 되 면 Server01 컴퓨터의 노드로 이동 하 여 세션 구성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-150">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="d2223-151">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="d2223-151">For example:</span></span>

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="d2223-152">세션 구성의 보안 설명자 변경</span><span class="sxs-lookup"><span data-stu-id="d2223-152">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="d2223-153">Windows server 2012 이상 버전의 Windows Server에서는 기본적으로 원격 사용자에 대해 기본 제공 세션 구성이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-153">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="d2223-154">지원 되는 다른 버전의 Windows에서는 원격 액세스를 허용 하도록 세션 구성의 보안 설명자를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-154">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="d2223-155">컴퓨터의 세션 구성에 대 한 원격 액세스를 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-155">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="d2223-156">이 cmdlet은 두 개의 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-156">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="d2223-157">이름이 "PowerShell"로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-157">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="d2223-158">+ "현재 PowerShell 버전"</span><span class="sxs-lookup"><span data-stu-id="d2223-158">+ "current PowerShell version"</span></span>
- <span data-ttu-id="d2223-159">이름이 "PowerShell. 6" 인 경우 특정 PowerShell 버전에 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-159">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="d2223-160">또한 기본적으로 컴퓨터의 Administrators 그룹 구성원만 기본 세션 구성에 대 한 실행 권한을 가지 지만 기본 세션 구성 및 사용자가 만든 모든 세션 구성에 대 한 보안 설명자를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-160">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="d2223-161">다른 사용자에 게 원격으로 컴퓨터에 연결할 수 있는 권한을 부여 하려면 Set-PSSessionConfiguration cmdlet을 사용 하 여 해당 사용자에 대 한 "실행" 권한을 Microsoft.powershell32 세션 구성의 보안 설명자에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-161">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="d2223-162">예를 들어 다음 명령은 Microsoft PowerShell 기본 세션 구성에 대 한 보안 설명자를 변경할 수 있는 속성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-162">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="d2223-163">컴퓨터의 모든 세션 구성에 대 한 모든 권한을 거부 하려면 Disable-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-163">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="d2223-164">예를 들어 다음 명령은 컴퓨터에서 기본 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-164">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="d2223-165">원격 사용자가 컴퓨터에 연결 하는 것을 방지 하기 위해 로컬 사용자가 연결할 수 있도록 하려면 Disable-PSRemoting cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-165">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="d2223-166">Disable-PSRemoting 컴퓨터의 모든 세션 구성에 "Network_Deny_All" 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-166">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="d2223-167">원격 사용자가 컴퓨터에서 모든 세션 구성을 사용할 수 있도록 하려면 Enable-PSRemoting 또는 Enable-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-167">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="d2223-168">예를 들어 다음 명령은 기본 제공 세션 구성에 대 한 원격 액세스를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-168">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="d2223-169">세션 구성의 보안 설명자에 대 한 다른 변경 작업을 수행 하려면 Set-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-169">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="d2223-170">SecurityDescriptorSDDL 매개 변수를 사용 하 여 SDDL 문자열 값을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-170">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="d2223-171">ShowSecurityDescriptorUI 매개 변수를 사용 하 여 새 SDDL을 만드는 데 도움이 되는 사용자 인터페이스 속성 시트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-171">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="d2223-172">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="d2223-172">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="d2223-173">새 세션 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="d2223-173">Creating a New Session Configuration</span></span>

<span data-ttu-id="d2223-174">로컬 컴퓨터에서 새 세션 구성을 만들려면 Register-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-174">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="d2223-175">새 세션 구성을 정의 하기 위해 c # 어셈블리, PowerShell 스크립트 및 Register-PSSessionConfiguration cmdlet의 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-175">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="d2223-176">예를 들어 다음 명령은 원격 명령에서 받은 데이터를 20mb로 제한 한다는 점을 제외 하 고는 Microsoft. PowerShell 세션 구성과 동일한 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-176">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="d2223-177">기본값은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-177">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="d2223-178">세션 구성을 만들 때 다른 세션 구성 cmdlet을 사용 하 여 관리할 수 있으며,이는 WSMAN: 드라이브에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-178">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="d2223-179">자세한 내용은 Register-pssessionconfiguration를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2223-179">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="d2223-180">세션 구성 제거</span><span class="sxs-lookup"><span data-stu-id="d2223-180">Removing a Session Configuration</span></span>

<span data-ttu-id="d2223-181">로컬 컴퓨터에서 세션 구성을 제거 하려면 Unregister-PSSessionConfiguration cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-181">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="d2223-182">예를 들어 다음 명령은 컴퓨터에서 NewConfig 세션 구성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-182">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="d2223-183">자세한 내용은 Register-pssessionconfiguration을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2223-183">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="d2223-184">세션 구성 복원</span><span class="sxs-lookup"><span data-stu-id="d2223-184">Restoring a Session Configuration</span></span>

<span data-ttu-id="d2223-185">실수로 삭제 (등록 취소) 된 기본 세션 구성을 복원 하려면 Enable-PSRemoting cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-185">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="d2223-186">Enable-PSRemoting cmdlet은 컴퓨터에 존재 하지 않는 모든 기본 세션 구성을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-186">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="d2223-187">기존 세션 구성의 속성 값을 덮어쓰거나 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-187">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="d2223-188">기본 세션 구성의 원래 속성 값을 복원 하려면 Unregister-PSSessionConfiguration을 사용 하 여 세션 구성을 삭제 한 다음 Enable-PSRemoting cmdlet을 사용 하 여 다시 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="d2223-188">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="d2223-189">세션 구성 선택</span><span class="sxs-lookup"><span data-stu-id="d2223-189">Selecting a Session Configuration</span></span>

<span data-ttu-id="d2223-190">세션에 대 한 특정 세션 구성을 선택 하려면 New-PSSession, Enter-PSSession 또는 Invoke 명령의 ConfigurationName 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-190">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="d2223-191">예를 들어이 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에서 PSSession을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-191">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="d2223-192">이 명령은 ConfigurationName 매개 변수를 사용 하 여 Server01 컴퓨터에서 WithProfile 구성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-192">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="d2223-193">이 명령은 현재 사용자가 WithProfile 세션 구성을 사용할 수 있는 권한이 있거나 필요한 권한이 있는 사용자의 자격 증명을 제공할 수 있는 경우에만 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-193">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="d2223-194">$PSSessionConfigurationName 기본 설정 변수를 사용 하 여 컴퓨터의 기본 세션 구성을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2223-194">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="d2223-195">$PSSessionConfigurationName 기본 설정 변수에 대 한 자세한 내용은 about_Preference_Variables을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2223-195">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="d2223-196">어</span><span class="sxs-lookup"><span data-stu-id="d2223-196">KEYWORDS</span></span>

<span data-ttu-id="d2223-197">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="d2223-197">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="d2223-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2223-198">SEE ALSO</span></span>

[<span data-ttu-id="d2223-199">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="d2223-199">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="d2223-200">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="d2223-200">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="d2223-201">about_Remote</span><span class="sxs-lookup"><span data-stu-id="d2223-201">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="d2223-202">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="d2223-202">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="d2223-203">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d2223-203">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="d2223-204">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2223-204">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="d2223-205">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2223-205">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="d2223-206">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2223-206">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="d2223-207">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d2223-207">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="d2223-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2223-208">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="d2223-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2223-209">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="d2223-210">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d2223-210">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="d2223-211">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2223-211">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
