---
description: WSMan
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 공급자
ms.openlocfilehash: 011383112d453a4fa88745c69b52e432709aa9d3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221026"
---
# <a name="wsman-provider"></a><span data-ttu-id="35616-104">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="35616-104">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="35616-105">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="35616-105">Provider name</span></span>

<span data-ttu-id="35616-106">WSMan</span><span class="sxs-lookup"><span data-stu-id="35616-106">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="35616-107">드라이브</span><span class="sxs-lookup"><span data-stu-id="35616-107">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="35616-108">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="35616-108">Short description</span></span>

<span data-ttu-id="35616-109">WS-Management(Web Services for Management) 구성 정보에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-109">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="35616-110">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="35616-110">Detailed description</span></span>

<span data-ttu-id="35616-111">PowerShell 용 **WSMan** 공급자를 사용 하 여 로컬 또는 원격 컴퓨터에서 WS-Management 구성 데이터를 추가, 변경, 지우기 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-111">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="35616-112">**WSMan** 공급자는 WS-Management 구성 설정의 논리적 그룹에 해당 하는 디렉터리 구조를 사용 하 여 PowerShell 드라이브를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-112">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="35616-113">이러한 그룹을 컨테이너라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-113">These groupings are known as containers.</span></span>

<span data-ttu-id="35616-114">Windows PowerShell 3.0부터 **WSMan** 공급자가 **OutputBufferingMode** 와 같은 세션 구성에 대 한 새 속성을 지원 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-114">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="35616-115">세션 구성은 드라이브의 플러그 인 디렉터리에 항목으로 표시 되 `WSMan:` 고 속성은 각 세션 구성에서 항목으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-115">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="35616-116">**WSMan** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-116">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="35616-117">Get-Location</span><span class="sxs-lookup"><span data-stu-id="35616-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="35616-118">Set-Location</span><span class="sxs-lookup"><span data-stu-id="35616-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="35616-119">Get-Item</span><span class="sxs-lookup"><span data-stu-id="35616-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="35616-120">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="35616-120">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="35616-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="35616-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="35616-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="35616-123">드라이브의 명령을 사용 하 여 `WSMan:` 새 속성의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-123">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="35616-124">그러나 `WSMan:` powershell 2.0에서 드라이브를 사용 하 여 Windows powershell 3.0에 도입 된 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-124">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="35616-125">오류가 생성 되지 않지만 이러한 설정을 변경 하는 데는 명령을 사용할 수 없습니다. Windows PowerShell 3.0에서 **WSMan** 드라이브를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-125">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="35616-126">WSMan: 드라이브 구성</span><span class="sxs-lookup"><span data-stu-id="35616-126">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="35616-127">**클라이언트** : WS-Management 클라이언트의 다양 한 측면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-127">**Client** : You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="35616-128">구성 정보는 레지스트리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-128">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="35616-129">**서비스** : WS-Management 서비스의 다양 한 측면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-129">**Service** : You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="35616-130">구성 정보는 레지스트리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-130">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-131">경우에 따라 서비스 구성을 서버 구성이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-131">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="35616-132">**Shell** : 원격 셸 액세스 허용 설정 ( **AllowRemoteShellAccess** ) 및 허용 되는 최대 동시 사용자 수 ( **MaxConcurrentUsers** )와 같은 WS-Management 셸의 다양 한 측면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-132">**Shell** : You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access ( **AllowRemoteShellAccess** ) and the maximum number of concurrent users allowed ( **MaxConcurrentUsers** ).</span></span>

- <span data-ttu-id="35616-133">**수신기** : 수신기를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-133">**Listener** : You can create and configure a listener.</span></span> <span data-ttu-id="35616-134">수신기는 메시지를 보내고 받을 WS-Management 프로토콜을 구현하는 관리 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-134">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="35616-135">**플러그 인** : 플러그 인은 다양 한 기능을 제공 하기 위해 WS-Management 서비스에서 로드 되 고 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-135">**Plugin** : Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="35616-136">기본적으로 PowerShell은 세 가지 플러그 인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-136">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="35616-137">이벤트 전달 플러그 인입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-137">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="35616-138">Microsoft PowerShell 플러그 인입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-138">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="35616-139">WMI(Windows Management Instrumentation) (WMI) 공급자 플러그 인입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-139">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="35616-140">이 세 가지 플러그 인은 이벤트 전달, 구성 및 WMI 액세스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-140">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="35616-141">**ClientCertificate** : 클라이언트 인증서를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-141">**ClientCertificate** : You can create and configure a client certificate.</span></span>
  <span data-ttu-id="35616-142">클라이언트 인증서는 WS-Management 클라이언트가 인증서 인증을 사용하도록 구성된 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-142">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="35616-143">WSMan 공급자의 디렉터리 계층 구조</span><span class="sxs-lookup"><span data-stu-id="35616-143">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="35616-144">로컬 컴퓨터용 WSMan 공급자의 디렉터리 계층 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-144">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

<span data-ttu-id="35616-145">로컬 컴퓨터와 원격 컴퓨터의 WSMan 공급자 디렉터리 계층 구조는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-145">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="35616-146">그러나 원격 컴퓨터의 구성 설정에 액세스하려면 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)을 사용하여 원격 컴퓨터에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-146">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="35616-147">원격 컴퓨터에 연결되면 원격 컴퓨터의 이름이 공급자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-147">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="35616-148">WSMan: 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="35616-148">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="35616-149">이 명령은 cmdlet을 사용 하 여 `Set-Location` 현재 위치를 드라이브로 변경 `WSMan:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-149">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="35616-150">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-150">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="35616-151">예를 들어을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-151">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="35616-152">원격 시스템 저장소 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="35616-152">Navigating to a remote system store location</span></span>

<span data-ttu-id="35616-153">이 명령은 명령을 사용 하 여 `Set-Location` 현재 위치를 원격 시스템 저장소 위치의 루트 위치로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-153">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="35616-154">백슬래시 `\` 또는 슬래시를 사용 `/` 하 여 드라이브의 수준을 표시 `WSMan:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-154">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="35616-155">위의 명령은 원격 시스템에 대한 연결이 이미 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-155">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="35616-156">WSMan: 드라이브의 콘텐츠 표시</span><span class="sxs-lookup"><span data-stu-id="35616-156">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="35616-157">이 명령은 cmdlet을 사용 하 여 `Get-Childitem` Localhost 저장소 위치의 WS-Management 저장소를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-157">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="35616-158">드라이브에 있는 경우 `WSMan:` 드라이브 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-158">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="35616-159">이 명령은 cmdlet을 사용 하 여 `Get-Childitem` 원격 컴퓨터 "SERVER01" 저장소 위치에 WS-Management 저장소를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-159">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="35616-160">위의 명령은 원격 시스템에 대한 연결이 이미 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-160">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="35616-161">WSMAN: 드라이브의 항목 값 설정</span><span class="sxs-lookup"><span data-stu-id="35616-161">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="35616-162">Cmdlet을 사용 `Set-Item` 하 여 드라이브의 구성 설정을 변경할 수 있습니다 `WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="35616-162">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="35616-163">다음 예에서는 "contoso.com" 접미사를 사용 하 여 모든 호스트를 허용 하도록 **TrustedHosts** 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-163">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="35616-164">`Set-Item`Cmdlet은 `-Concatenate` 값을 변경 하는 대신 추가 하는 추가 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-164">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="35616-165">다음 예에서는에 저장 된 이전 값에 새 값 "\*. domain2.com"를 추가 합니다. `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="35616-165">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="35616-166">WSMAN: 드라이브에 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-166">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="35616-167">새 수신기 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-167">Creating a new listener</span></span>

<span data-ttu-id="35616-168">`New-Item`Cmdlet은 공급자 드라이브에 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35616-168">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="35616-169">각 공급자에는 만들 수 있는 다양 한 항목 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-169">Each provider has different item types that you can create.</span></span> <span data-ttu-id="35616-170">드라이브에서 `WSMAN:` 원격 요청을 수신 하 고 응답 하도록 구성 하는 *수신기* 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-170">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="35616-171">다음 명령은 cmdlet을 사용 하 여 새 HTTP 수신기를 만듭니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="35616-171">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="35616-172">새 플러그 인 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-172">Creating a new plug-in</span></span>

<span data-ttu-id="35616-173">이 명령은 WS-Management 서비스용 플러그 인을 만듭니다(등록).</span><span class="sxs-lookup"><span data-stu-id="35616-173">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="35616-174">새 리소스 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-174">Creating a new resource entry</span></span>

<span data-ttu-id="35616-175">이 명령은 TestPlugin의 Resources 디렉터리에 리소스 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35616-175">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="35616-176">이 명령은 TestPlugin이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-176">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="35616-177">리소스에 대 한 새 보안 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-177">Creating a new security entry for a resource</span></span>

<span data-ttu-id="35616-178">이 명령은 Resource_5967683(특정 리소스)의 Security 디렉터리에 보안 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35616-178">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="35616-179">이 명령은 리소스 항목이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-179">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="35616-180">새 클라이언트 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-180">Creating a new Client Certificate</span></span>

<span data-ttu-id="35616-181">이 명령은 WS-Management 클라이언트에서 사용할 수 있는 **ClientCertificate** 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35616-181">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="35616-182">새 **ClientCertificate** 가 **ClientCertificate** 디렉터리 아래에 "ClientCertificate_1234567890"로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-182">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="35616-183">모든 매개 변수는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-183">All of the parameters are mandatory.</span></span> <span data-ttu-id="35616-184">**발급자** 는 발급자 인증서의 손 도장 (thumbprint) 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-184">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="35616-185">새 초기화 매개 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="35616-185">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="35616-186">이 명령은 "InitializationParameters" 디렉터리에 "testparametername" 이라는 초기화 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35616-186">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="35616-187">이 명령은 "TestPlugin"이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-187">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="35616-188">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="35616-188">Dynamic parameters</span></span>

<span data-ttu-id="35616-189">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-189">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="35616-190">Address \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-190">Address \<String\></span></span>

<span data-ttu-id="35616-191">이 수신기가 만들어진 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-191">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="35616-192">값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-192">The value can be one of the following:</span></span>

- <span data-ttu-id="35616-193">리터럴 문자열 "\*"입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-193">The literal string "\*".</span></span> <span data-ttu-id="35616-194">와일드 카드 문자 ( `*` )를 사용 하면 명령이 모든 네트워크 어댑터에서 모든 IP 주소를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-194">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="35616-195">리터럴 문자열 "IP:"와 IPv4 점으로 구분 된 IPv4 형식의 유효한 IP 주소, 즉 IPv6 복제 된 16 진수 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-195">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="35616-196">리터럴 문자열 "MAC:" 뒤에 어댑터의 MAC 주소가 옵니다.</span><span class="sxs-lookup"><span data-stu-id="35616-196">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="35616-197">예: MAC: 32-a3-58 -90-cc.</span><span class="sxs-lookup"><span data-stu-id="35616-197">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="35616-198">Address 값은 수신기를 만들 때 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-198">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-199">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="35616-199">Cmdlets supported</span></span>

- [<span data-ttu-id="35616-200">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-200">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="35616-201">Capability \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="35616-201">Capability \<Enumeration\></span></span>

<span data-ttu-id="35616-202">*플러그* 인을 사용 하는 경우이 매개 변수는이 URI (Uniform resource Identifier)에서 지원 되는 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-202">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="35616-203">URI가 지원하는 각 작업 유형에 대해 하나의 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-203">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="35616-204">작업에서 지 원하는 경우 지정 된 작업에 유효한 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-204">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="35616-205">이러한 특성에는 **Supportsfiltering** And **supportsfiltering** 가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-205">These attributes include **SupportsFiltering** and **SupportsFragment**.</span></span>

- <span data-ttu-id="35616-206">**만들기** : URI에서 만들기 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-206">**Create** : Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-207">**Supportfragment** 특성은 만들기 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-207">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="35616-208">**Supportfiltering** 특성은 만들기 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-208">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-209">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-209">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-210">**삭제** : URI에서 삭제 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-210">**Delete** : Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-211">**Supportfragment** 특성은 Delete 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-211">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="35616-212">**Supportfiltering** 특성은 삭제 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-212">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-213">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-213">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-214">**열거** : URI에 대해 열거 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-214">**Enumerate** : Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-215">**Supportfragment** 특성은 열거 작업에 지원 되지 않으므로 False로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-215">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="35616-216">**Supportfiltering** 특성이 유효 하 고 플러그 인에서 필터링을 지 원하는 경우이 특성을 "True"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-216">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-217">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-217">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-218">**Get** : get 작업은 URI에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-218">**Get** : Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-219">**Supportfragment** 특성은 Get 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-219">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="35616-220">**Supportfiltering** 특성은 Get 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-220">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-221">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-221">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-222">**Invoke** : 호출 작업은 URI에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-222">**Invoke** : Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-223">**Supportfragment** 특성은 호출 작업에 지원 되지 않으므로 False로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-223">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="35616-224">**Supportfiltering** 특성이 잘못 되었으며 "False"로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-224">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-225">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-225">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-226">**Put** : URI에서 put 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-226">**Put** : Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-227">**Supportfragment** 특성은 Put 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-227">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="35616-228">**Supportfiltering** 특성은 Put 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-228">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-229">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-229">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-230">**구독** : URI에서 구독 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-230">**Subscribe** : Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-231">**Supportfragment** 특성은 구독 작업에 대해 지원 되지 않으므로 False로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-231">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="35616-232">**Supportfiltering** 특성은 구독 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-232">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-233">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-233">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="35616-234">**셸** : URI에서 셸 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-234">**Shell** : Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="35616-235">**Supportfragment** 특성은 셸 작업에 대해 지원 되지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-235">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="35616-236">**Supportfiltering** 특성은 셸 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-236">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-237">다른 작업도 지원 되는 경우이 작업은 URI에 대해 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-237">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="35616-238">URI에 대해 Shell 작업이 구성된 경우 Get, Put, Create, Delete, Invoke 및 Enumerate 작업은 셸을 관리하기 위해 WS-Management(WinRM) 서비스에서 내부적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-238">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="35616-239">따라서 플러그 인에서 작업을 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-239">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-240">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="35616-240">Cmdlets supported</span></span>

- [<span data-ttu-id="35616-241">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-241">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="35616-242">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-242">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="35616-243">서비스 인증서의 지문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-243">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="35616-244">이 값은 인증서의 Thumbprint 필드에 있는 2자리 16진수 값의 문자열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="35616-244">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="35616-245">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-245">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="35616-246">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-246">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="35616-247">인증서는 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-247">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="35616-248">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-248">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-249">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="35616-249">Cmdlets supported</span></span>

- [<span data-ttu-id="35616-250">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-250">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="35616-251">Enabled \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="35616-251">Enabled \<Boolean\></span></span>

<span data-ttu-id="35616-252">수신기를 사용하도록 설정할지 또는 사용하지 않도록 설정할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-252">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="35616-253">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-253">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-254">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-254">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-255">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-255">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="35616-256">FileName (Plugin) \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-256">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="35616-257">작업 플러그 인의 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-257">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="35616-258">이 항목에 포함 된 모든 환경 변수는 요청이 수신 될 때 사용자의 컨텍스트에서 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-258">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="35616-259">각 사용자는 동일한 환경 변수의 서로 다른 버전을 가질 수 있기 때문에 각 사용자는 다른 플러그 인을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-259">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="35616-260">이 항목은 비워 둘 수 없으며 올바른 플러그 인을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-260">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-261">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-261">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-262">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-262">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="35616-263">HostName \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-263">HostName \<String\></span></span>

<span data-ttu-id="35616-264">WS-Management(WinRM) 서비스가 실행되는 컴퓨터의 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-264">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="35616-265">값은 정규화된 도메인 이름, IPv4 또는 IPv6 리터럴 문자열 또는 와일드카드 문자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-265">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-266">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-266">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-267">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-267">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="35616-268">Issuer \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-268">Issuer \<String\></span></span>

<span data-ttu-id="35616-269">인증서를 발급한 인증 기관의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-269">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-270">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-270">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-271">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-271">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="35616-272">플러그 인 \<\> WS-Management 플러그 인은 네이티브 dll (동적 연결 라이브러리)입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-272">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="35616-273">WS-Management의 기능을 연결 하 고 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-273">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="35616-274">WSW-Management 플러그 인 API는 지원 되는 리소스 Uri 및 작업에 대 한 특정 Api를 구현 하 여 사용자가 플러그 인을 작성할 수 있도록 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-274">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="35616-275">플러그 인이 WS-Management(WinRM) 서비스 또는 IIS(인터넷 정보 서비스)에 대해 구성된 경우 각각 WS-Management 호스트 또는 IIS 호스트에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-275">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="35616-276">원격 요청은 작업을 수행하기 위해 이러한 플러그 인 진입점에 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-276">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-277">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-277">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-278">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-278">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="35616-279">Port \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="35616-279">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="35616-280">이 수신기가 만들어지는 TCP 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-280">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="35616-281">1에서 65535 사이의 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-281">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-282">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-282">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-283">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-283">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="35616-284">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-284">Resource \<String\></span></span>

<span data-ttu-id="35616-285">고유한 유형의 관리 작업 또는 값을 나타내는 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-285">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="35616-286">서비스는 하나 이상의 리소스를 표시하고, 일부 리소스는 둘 이상의 인스턴스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-286">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="35616-287">관리 리소스는 WMI 클래스 또는 데이터베이스 테이블과 유사하며, 인스턴스는 클래스 인스턴스나 테이블의 행과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-287">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="35616-288">예를 들어 **Win32_LogicalDisk** 클래스는 리소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="35616-288">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="35616-289">`Win32_LogicalDisk="C:\\"` 는 리소스의 특정 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-289">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="35616-290">URI(Uniform Resource Identifier)에는 접두사와 리소스 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-290">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="35616-291">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="35616-291">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-292">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-292">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-293">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-293">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="35616-294">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-294">Resource \<String\></span></span>

<span data-ttu-id="35616-295">디스크 또는 프로세스와 같은 컴퓨터의 특정 리소스 유형을 식별하는 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-295">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="35616-296">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-296">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="35616-297">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="35616-297">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-298">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-298">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-299">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-299">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="35616-300">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-300">SDKVersion \<String\></span></span>

<span data-ttu-id="35616-301">WS-Management 플러그 인 SDK의 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-301">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="35616-302">유일 하 게 유효한 값은</span><span class="sxs-lookup"><span data-stu-id="35616-302">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-303">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-303">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-304">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-304">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="35616-305">Subject \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-305">Subject \<String\></span></span>

<span data-ttu-id="35616-306">인증서로 식별되는 엔티티를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-306">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-307">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-307">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-308">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-308">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="35616-309">Transport \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-309">Transport \<String\></span></span>

<span data-ttu-id="35616-310">WS-Management 프로토콜 요청 및 응답을 보내고 받는 데 사용할 전송을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-310">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="35616-311">값은 HTTP 또는 HTTPS여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-311">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="35616-312">참고: 전송 값은 수신기를 만들 때 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-312">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-313">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-313">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-314">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-314">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="35616-315">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-315">URI \<String\></span></span>

<span data-ttu-id="35616-316">Sddl 매개 변수의 값을 기준으로 액세스 권한이 부여되는 URI를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-316">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-317">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-317">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-318">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-318">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="35616-319">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-319">URLPrefix \<String\></span></span>

<span data-ttu-id="35616-320">HTTP 또는 HTTPS 요청을 수락할 URL 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-320">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="35616-321">이는 문자 `[a-z]` , `[A-Z]` , `[9-0]` , 밑줄 ( `_` ) 및 백슬래시 ( `/` )만 포함 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-321">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="35616-322">문자열은 백슬래시 ()로 시작 하거나 끝나지 않아야 합니다 `/` .</span><span class="sxs-lookup"><span data-stu-id="35616-322">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="35616-323">예를 들어 컴퓨터 이름이 "SampleComputer" 인 경우 WS-Management 클라이언트는 `http://SampleMachine/URLPrefix` 대상 주소에를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-323">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-324">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-324">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-325">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-325">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="35616-326">Value \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-326">Value \<String\></span></span>

<span data-ttu-id="35616-327">구성 옵션을 지정하는 데 사용되는 플러그 인 관련 값인 초기화 매개 변수 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-327">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-328">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-328">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-329">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-329">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="35616-330">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="35616-330">XMLRenderingType \<String\></span></span>

<span data-ttu-id="35616-331">**WSMAN_DATA** 개체를 통해 XML이 플러그 인에 전달 되는 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-331">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="35616-332">다음은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="35616-332">The following are valid values:</span></span>

- <span data-ttu-id="35616-333">Text: 들어오는 XML 데이터는 XML을 **Pcwstr** 메모리 버퍼로 나타내는 **WSMAN_DATA_TYPE_TEXT** 구조에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35616-333">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="35616-334">XMLReader: 들어오는 XML 데이터는 XML을 "WebServices" 헤더 파일에 정의 된 **XmlReader** 개체로 나타내는 **WSMAN_DATA_TYPE_WS_XML_READER** 구조에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-334">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="35616-335">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35616-335">Cmdlets Supported</span></span>

- [<span data-ttu-id="35616-336">New-Item</span><span class="sxs-lookup"><span data-stu-id="35616-336">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="35616-337">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="35616-337">Using the pipeline</span></span>

<span data-ttu-id="35616-338">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-338">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="35616-339">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-339">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="35616-340">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35616-340">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="35616-341">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="35616-341">Getting help</span></span>

<span data-ttu-id="35616-342">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35616-342">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="35616-343">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35616-343">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="35616-344">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35616-344">See also</span></span>

[<span data-ttu-id="35616-345">about_Providers</span><span class="sxs-lookup"><span data-stu-id="35616-345">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)
