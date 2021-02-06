---
description: WSMan
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 공급자
ms.openlocfilehash: 32baaaec3589fc9d6f4c2319f47d56bca777f738
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601860"
---
# <a name="wsman-provider"></a><span data-ttu-id="88ad7-103">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="88ad7-103">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="88ad7-104">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="88ad7-104">Provider name</span></span>

<span data-ttu-id="88ad7-105">WSMan</span><span class="sxs-lookup"><span data-stu-id="88ad7-105">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="88ad7-106">드라이브</span><span class="sxs-lookup"><span data-stu-id="88ad7-106">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="88ad7-107">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="88ad7-107">Short description</span></span>

<span data-ttu-id="88ad7-108">WS-Management(Web Services for Management) 구성 정보에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-108">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="88ad7-109">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="88ad7-109">Detailed description</span></span>

<span data-ttu-id="88ad7-110">PowerShell 용 **WSMan** 공급자를 사용 하 여 로컬 또는 원격 컴퓨터에서 WS-Management 구성 데이터를 추가, 변경, 지우기 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-110">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="88ad7-111">**WSMan** 공급자는 WS-Management 구성 설정의 논리적 그룹에 해당 하는 디렉터리 구조를 사용 하 여 PowerShell 드라이브를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-111">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="88ad7-112">이러한 그룹을 컨테이너라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-112">These groupings are known as containers.</span></span>

<span data-ttu-id="88ad7-113">Windows PowerShell 3.0부터 **WSMan** 공급자가 **OutputBufferingMode** 와 같은 세션 구성에 대 한 새 속성을 지원 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-113">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="88ad7-114">세션 구성은 드라이브의 플러그 인 디렉터리에 항목으로 표시 되 `WSMan:` 고 속성은 각 세션 구성에서 항목으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-114">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="88ad7-115">**WSMan** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-115">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="88ad7-116">Get-Location</span><span class="sxs-lookup"><span data-stu-id="88ad7-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="88ad7-117">Set-Location</span><span class="sxs-lookup"><span data-stu-id="88ad7-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="88ad7-118">Get-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="88ad7-119">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="88ad7-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="88ad7-120">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-120">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="88ad7-121">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-121">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="88ad7-122">드라이브의 명령을 사용 하 여 `WSMan:` 새 속성의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-122">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="88ad7-123">그러나 `WSMan:` powershell 2.0에서 드라이브를 사용 하 여 Windows powershell 3.0에 도입 된 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-123">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="88ad7-124">오류가 생성 되지 않지만 이러한 설정을 변경 하는 데는 명령을 사용할 수 없습니다. Windows PowerShell 3.0에서 **WSMan** 드라이브를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-124">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="88ad7-125">WSMan: 드라이브 구성</span><span class="sxs-lookup"><span data-stu-id="88ad7-125">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="88ad7-126">**클라이언트**: WS-Management 클라이언트의 다양 한 측면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-126">**Client**: You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="88ad7-127">구성 정보는 레지스트리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-127">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="88ad7-128">**서비스**: WS-Management 서비스의 다양 한 측면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-128">**Service**: You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="88ad7-129">구성 정보는 레지스트리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-129">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-130">경우에 따라 서비스 구성을 서버 구성이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-130">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="88ad7-131">**Shell**: 원격 셸 액세스 허용 설정 (**AllowRemoteShellAccess**) 및 허용 되는 최대 동시 사용자 수 (**MaxConcurrentUsers**)와 같은 WS-Management 셸의 다양 한 측면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-131">**Shell**: You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access (**AllowRemoteShellAccess**) and the maximum number of concurrent users allowed (**MaxConcurrentUsers**).</span></span>

- <span data-ttu-id="88ad7-132">**수신기**: 수신기를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-132">**Listener**: You can create and configure a listener.</span></span> <span data-ttu-id="88ad7-133">수신기는 메시지를 보내고 받을 WS-Management 프로토콜을 구현하는 관리 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-133">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="88ad7-134">**플러그 인**: 플러그 인은 다양 한 기능을 제공 하기 위해 WS-Management 서비스에서 로드 되 고 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-134">**Plugin**: Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="88ad7-135">기본적으로 PowerShell은 세 가지 플러그 인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-135">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="88ad7-136">이벤트 전달 플러그 인입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-136">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="88ad7-137">Microsoft PowerShell 플러그 인입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-137">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="88ad7-138">WMI(Windows Management Instrumentation) (WMI) 공급자 플러그 인입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-138">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="88ad7-139">이 세 가지 플러그 인은 이벤트 전달, 구성 및 WMI 액세스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-139">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="88ad7-140">**ClientCertificate**: 클라이언트 인증서를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-140">**ClientCertificate**: You can create and configure a client certificate.</span></span>
  <span data-ttu-id="88ad7-141">클라이언트 인증서는 WS-Management 클라이언트가 인증서 인증을 사용하도록 구성된 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-141">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="88ad7-142">WSMan 공급자의 디렉터리 계층 구조</span><span class="sxs-lookup"><span data-stu-id="88ad7-142">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="88ad7-143">로컬 컴퓨터용 WSMan 공급자의 디렉터리 계층 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-143">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

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

<span data-ttu-id="88ad7-144">로컬 컴퓨터와 원격 컴퓨터의 WSMan 공급자 디렉터리 계층 구조는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-144">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="88ad7-145">그러나 원격 컴퓨터의 구성 설정에 액세스하려면 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)을 사용하여 원격 컴퓨터에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-145">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="88ad7-146">원격 컴퓨터에 연결되면 원격 컴퓨터의 이름이 공급자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-146">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="88ad7-147">WSMan: 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="88ad7-147">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="88ad7-148">이 명령은 cmdlet을 사용 하 여 `Set-Location` 현재 위치를 드라이브로 변경 `WSMan:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-148">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="88ad7-149">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-149">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="88ad7-150">예를 들어을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-150">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="88ad7-151">원격 시스템 저장소 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="88ad7-151">Navigating to a remote system store location</span></span>

<span data-ttu-id="88ad7-152">이 명령은 명령을 사용 하 여 `Set-Location` 현재 위치를 원격 시스템 저장소 위치의 루트 위치로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-152">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="88ad7-153">백슬래시 `\` 또는 슬래시를 사용 `/` 하 여 드라이브의 수준을 표시 `WSMan:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-153">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="88ad7-154">위의 명령은 원격 시스템에 대한 연결이 이미 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-154">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="88ad7-155">WSMan: 드라이브의 콘텐츠 표시</span><span class="sxs-lookup"><span data-stu-id="88ad7-155">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="88ad7-156">이 명령은 cmdlet을 사용 하 여 `Get-Childitem` Localhost 저장소 위치의 WS-Management 저장소를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-156">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="88ad7-157">드라이브에 있는 경우 `WSMan:` 드라이브 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-157">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="88ad7-158">이 명령은 cmdlet을 사용 하 여 `Get-Childitem` 원격 컴퓨터 "SERVER01" 저장소 위치에 WS-Management 저장소를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-158">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="88ad7-159">위의 명령은 원격 시스템에 대한 연결이 이미 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-159">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="88ad7-160">WSMAN: 드라이브의 항목 값 설정</span><span class="sxs-lookup"><span data-stu-id="88ad7-160">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="88ad7-161">Cmdlet을 사용 `Set-Item` 하 여 드라이브의 구성 설정을 변경할 수 있습니다 `WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="88ad7-161">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="88ad7-162">다음 예에서는 "contoso.com" 접미사를 사용 하 여 모든 호스트를 허용 하도록 **TrustedHosts** 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-162">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="88ad7-163">`Set-Item`Cmdlet은 `-Concatenate` 값을 변경 하는 대신 추가 하는 추가 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-163">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="88ad7-164">다음 예에서는에 저장 된 이전 값에 새 값 "\*. domain2.com"를 추가 합니다. `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="88ad7-164">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="88ad7-165">WSMAN: 드라이브에 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-165">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="88ad7-166">새 수신기 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-166">Creating a new listener</span></span>

<span data-ttu-id="88ad7-167">`New-Item`Cmdlet은 공급자 드라이브에 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-167">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="88ad7-168">각 공급자에는 만들 수 있는 다양 한 항목 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-168">Each provider has different item types that you can create.</span></span> <span data-ttu-id="88ad7-169">드라이브에서 `WSMAN:` 원격 요청을 수신 하 고 응답 하도록 구성 하는 *수신기* 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-169">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="88ad7-170">다음 명령은 cmdlet을 사용 하 여 새 HTTP 수신기를 만듭니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="88ad7-170">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="88ad7-171">새 플러그 인 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-171">Creating a new plug-in</span></span>

<span data-ttu-id="88ad7-172">이 명령은 WS-Management 서비스용 플러그 인을 만듭니다(등록).</span><span class="sxs-lookup"><span data-stu-id="88ad7-172">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="88ad7-173">새 리소스 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-173">Creating a new resource entry</span></span>

<span data-ttu-id="88ad7-174">이 명령은 TestPlugin의 Resources 디렉터리에 리소스 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-174">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="88ad7-175">이 명령은 TestPlugin이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-175">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="88ad7-176">리소스에 대 한 새 보안 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-176">Creating a new security entry for a resource</span></span>

<span data-ttu-id="88ad7-177">이 명령은 Resource_5967683(특정 리소스)의 Security 디렉터리에 보안 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-177">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="88ad7-178">이 명령은 리소스 항목이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-178">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="88ad7-179">새 클라이언트 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-179">Creating a new Client Certificate</span></span>

<span data-ttu-id="88ad7-180">이 명령은 WS-Management 클라이언트에서 사용할 수 있는 **ClientCertificate** 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-180">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="88ad7-181">새 **ClientCertificate** 가 **ClientCertificate** 디렉터리 아래에 "ClientCertificate_1234567890"로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-181">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="88ad7-182">모든 매개 변수는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-182">All of the parameters are mandatory.</span></span> <span data-ttu-id="88ad7-183">**발급자** 는 발급자 인증서의 손 도장 (thumbprint) 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-183">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="88ad7-184">새 초기화 매개 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="88ad7-184">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="88ad7-185">이 명령은 "InitializationParameters" 디렉터리에 "testparametername" 이라는 초기화 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-185">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="88ad7-186">이 명령은 "TestPlugin"이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-186">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="88ad7-187">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="88ad7-187">Dynamic parameters</span></span>

<span data-ttu-id="88ad7-188">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-188">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="88ad7-189">Address \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-189">Address \<String\></span></span>

<span data-ttu-id="88ad7-190">이 수신기가 만들어진 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-190">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="88ad7-191">값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-191">The value can be one of the following:</span></span>

- <span data-ttu-id="88ad7-192">리터럴 문자열 "\*"입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-192">The literal string "\*".</span></span> <span data-ttu-id="88ad7-193">와일드 카드 문자 ( `*` )를 사용 하면 명령이 모든 네트워크 어댑터에서 모든 IP 주소를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-193">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="88ad7-194">리터럴 문자열 "IP:"와 IPv4 점으로 구분 된 IPv4 형식의 유효한 IP 주소, 즉 IPv6 복제 된 16 진수 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-194">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="88ad7-195">리터럴 문자열 "MAC:" 뒤에 어댑터의 MAC 주소가 옵니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-195">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="88ad7-196">예: MAC: 32-a3-58 -90-cc.</span><span class="sxs-lookup"><span data-stu-id="88ad7-196">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="88ad7-197">Address 값은 수신기를 만들 때 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-197">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-198">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="88ad7-198">Cmdlets supported</span></span>

- [<span data-ttu-id="88ad7-199">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-199">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="88ad7-200">Capability \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="88ad7-200">Capability \<Enumeration\></span></span>

<span data-ttu-id="88ad7-201">*플러그* 인을 사용 하는 경우이 매개 변수는이 URI (Uniform resource Identifier)에서 지원 되는 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-201">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="88ad7-202">URI가 지원하는 각 작업 유형에 대해 하나의 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-202">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="88ad7-203">작업에서 지 원하는 경우 지정 된 작업에 유효한 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-203">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="88ad7-204">이러한 특성에는 **Supportsfiltering** And **supportsfiltering** 가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-204">These attributes include **SupportsFiltering** and **SupportsFragment**.</span></span>

- <span data-ttu-id="88ad7-205">**만들기**: URI에서 만들기 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-205">**Create**: Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-206">**Supportfragment** 특성은 만들기 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-206">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="88ad7-207">**Supportfiltering** 특성은 만들기 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-207">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-208">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-208">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-209">**삭제**: URI에서 삭제 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-209">**Delete**: Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-210">**Supportfragment** 특성은 Delete 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-210">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="88ad7-211">**Supportfiltering** 특성은 삭제 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-211">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-212">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-212">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-213">**열거**: URI에 대해 열거 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-213">**Enumerate**: Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-214">**Supportfragment** 특성은 열거 작업에 지원 되지 않으므로 False로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-214">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="88ad7-215">**Supportfiltering** 특성이 유효 하 고 플러그 인에서 필터링을 지 원하는 경우이 특성을 "True"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-215">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-216">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-216">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-217">**Get**: get 작업은 URI에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-217">**Get**: Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-218">**Supportfragment** 특성은 Get 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-218">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="88ad7-219">**Supportfiltering** 특성은 Get 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-219">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-220">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-220">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-221">**Invoke**: 호출 작업은 URI에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-221">**Invoke**: Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-222">**Supportfragment** 특성은 호출 작업에 지원 되지 않으므로 False로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-222">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="88ad7-223">**Supportfiltering** 특성이 잘못 되었으며 "False"로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-223">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-224">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-224">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-225">**Put**: URI에서 put 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-225">**Put**: Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-226">**Supportfragment** 특성은 Put 작업에서 개념을 지 원하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-226">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="88ad7-227">**Supportfiltering** 특성은 Put 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-227">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-228">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-228">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-229">**구독**: URI에서 구독 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-229">**Subscribe**: Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-230">**Supportfragment** 특성은 구독 작업에 대해 지원 되지 않으므로 False로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-230">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="88ad7-231">**Supportfiltering** 특성은 구독 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-231">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-232">Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-232">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="88ad7-233">**셸**: URI에서 셸 작업이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-233">**Shell**: Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="88ad7-234">**Supportfragment** 특성은 셸 작업에 대해 지원 되지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-234">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="88ad7-235">**Supportfiltering** 특성은 셸 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-235">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-236">다른 작업도 지원 되는 경우이 작업은 URI에 대해 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-236">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="88ad7-237">URI에 대해 Shell 작업이 구성된 경우 Get, Put, Create, Delete, Invoke 및 Enumerate 작업은 셸을 관리하기 위해 WS-Management(WinRM) 서비스에서 내부적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-237">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="88ad7-238">따라서 플러그 인에서 작업을 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-238">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-239">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="88ad7-239">Cmdlets supported</span></span>

- [<span data-ttu-id="88ad7-240">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-240">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="88ad7-241">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-241">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="88ad7-242">서비스 인증서의 지문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-242">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="88ad7-243">이 값은 인증서의 Thumbprint 필드에 있는 2자리 16진수 값의 문자열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-243">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="88ad7-244">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-244">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="88ad7-245">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-245">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="88ad7-246">인증서는 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-246">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="88ad7-247">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-247">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-248">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="88ad7-248">Cmdlets supported</span></span>

- [<span data-ttu-id="88ad7-249">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-249">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="88ad7-250">Enabled \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="88ad7-250">Enabled \<Boolean\></span></span>

<span data-ttu-id="88ad7-251">수신기를 사용하도록 설정할지 또는 사용하지 않도록 설정할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-251">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="88ad7-252">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-252">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-253">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-253">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-254">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-254">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="88ad7-255">FileName (Plugin) \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-255">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="88ad7-256">작업 플러그 인의 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-256">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="88ad7-257">이 항목에 포함 된 모든 환경 변수는 요청이 수신 될 때 사용자의 컨텍스트에서 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-257">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="88ad7-258">각 사용자는 동일한 환경 변수의 서로 다른 버전을 가질 수 있기 때문에 각 사용자는 다른 플러그 인을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-258">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="88ad7-259">이 항목은 비워 둘 수 없으며 올바른 플러그 인을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-259">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-260">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-260">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-261">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-261">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="88ad7-262">HostName \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-262">HostName \<String\></span></span>

<span data-ttu-id="88ad7-263">WS-Management(WinRM) 서비스가 실행되는 컴퓨터의 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-263">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="88ad7-264">값은 정규화된 도메인 이름, IPv4 또는 IPv6 리터럴 문자열 또는 와일드카드 문자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-264">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-265">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-265">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-266">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-266">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="88ad7-267">Issuer \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-267">Issuer \<String\></span></span>

<span data-ttu-id="88ad7-268">인증서를 발급한 인증 기관의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-268">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-269">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-269">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-270">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-270">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="88ad7-271">플러그 인 \<\> WS-Management 플러그 인은 네이티브 dll (동적 연결 라이브러리)입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-271">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="88ad7-272">WS-Management의 기능을 연결 하 고 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-272">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="88ad7-273">WSW-Management 플러그 인 API는 지원 되는 리소스 Uri 및 작업에 대 한 특정 Api를 구현 하 여 사용자가 플러그 인을 작성할 수 있도록 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-273">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="88ad7-274">플러그 인이 WS-Management(WinRM) 서비스 또는 IIS(인터넷 정보 서비스)에 대해 구성된 경우 각각 WS-Management 호스트 또는 IIS 호스트에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-274">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="88ad7-275">원격 요청은 작업을 수행하기 위해 이러한 플러그 인 진입점에 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-275">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-276">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-276">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-277">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-277">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="88ad7-278">Port \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="88ad7-278">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="88ad7-279">이 수신기가 만들어지는 TCP 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-279">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="88ad7-280">1에서 65535 사이의 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-280">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-281">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-281">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-282">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-282">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="88ad7-283">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-283">Resource \<String\></span></span>

<span data-ttu-id="88ad7-284">고유한 유형의 관리 작업 또는 값을 나타내는 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-284">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="88ad7-285">서비스는 하나 이상의 리소스를 표시하고, 일부 리소스는 둘 이상의 인스턴스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-285">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="88ad7-286">관리 리소스는 WMI 클래스 또는 데이터베이스 테이블과 유사하며, 인스턴스는 클래스 인스턴스나 테이블의 행과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-286">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="88ad7-287">예를 들어 **Win32_LogicalDisk** 클래스는 리소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-287">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="88ad7-288">`Win32_LogicalDisk="C:\\"` 는 리소스의 특정 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-288">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="88ad7-289">URI(Uniform Resource Identifier)에는 접두사와 리소스 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-289">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="88ad7-290">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="88ad7-290">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-291">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-291">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-292">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-292">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="88ad7-293">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-293">Resource \<String\></span></span>

<span data-ttu-id="88ad7-294">디스크 또는 프로세스와 같은 컴퓨터의 특정 리소스 유형을 식별하는 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-294">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="88ad7-295">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-295">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="88ad7-296">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="88ad7-296">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-297">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-297">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-298">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-298">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="88ad7-299">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-299">SDKVersion \<String\></span></span>

<span data-ttu-id="88ad7-300">WS-Management 플러그 인 SDK의 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-300">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="88ad7-301">유일 하 게 유효한 값은</span><span class="sxs-lookup"><span data-stu-id="88ad7-301">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-302">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-302">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-303">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-303">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="88ad7-304">Subject \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-304">Subject \<String\></span></span>

<span data-ttu-id="88ad7-305">인증서로 식별되는 엔티티를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-305">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-306">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-306">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-307">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-307">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="88ad7-308">Transport \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-308">Transport \<String\></span></span>

<span data-ttu-id="88ad7-309">WS-Management 프로토콜 요청 및 응답을 보내고 받는 데 사용할 전송을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-309">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="88ad7-310">값은 HTTP 또는 HTTPS여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-310">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="88ad7-311">참고: 전송 값은 수신기를 만들 때 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-311">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-312">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-312">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-313">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-313">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="88ad7-314">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-314">URI \<String\></span></span>

<span data-ttu-id="88ad7-315">Sddl 매개 변수의 값을 기준으로 액세스 권한이 부여되는 URI를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-315">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-316">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-316">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-317">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-317">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="88ad7-318">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-318">URLPrefix \<String\></span></span>

<span data-ttu-id="88ad7-319">HTTP 또는 HTTPS 요청을 수락할 URL 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-319">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="88ad7-320">이는 문자 `[a-z]` , `[A-Z]` , `[9-0]` , 밑줄 ( `_` ) 및 백슬래시 ( `/` )만 포함 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-320">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="88ad7-321">문자열은 백슬래시 ()로 시작 하거나 끝나지 않아야 합니다 `/` .</span><span class="sxs-lookup"><span data-stu-id="88ad7-321">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="88ad7-322">예를 들어 컴퓨터 이름이 "SampleComputer" 인 경우 WS-Management 클라이언트는 `http://SampleMachine/URLPrefix` 대상 주소에를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-322">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-323">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-323">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-324">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-324">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="88ad7-325">Value \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-325">Value \<String\></span></span>

<span data-ttu-id="88ad7-326">구성 옵션을 지정하는 데 사용되는 플러그 인 관련 값인 초기화 매개 변수 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-326">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-327">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-327">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-328">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-328">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="88ad7-329">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="88ad7-329">XMLRenderingType \<String\></span></span>

<span data-ttu-id="88ad7-330">**WSMAN_DATA** 개체를 통해 XML이 플러그 인에 전달 되는 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-330">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="88ad7-331">다음은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-331">The following are valid values:</span></span>

- <span data-ttu-id="88ad7-332">Text: 들어오는 XML 데이터는 XML을 **Pcwstr** 메모리 버퍼로 나타내는 **WSMAN_DATA_TYPE_TEXT** 구조에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-332">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="88ad7-333">XMLReader: 들어오는 XML 데이터는 XML을 "WebServices" 헤더 파일에 정의 된 **XmlReader** 개체로 나타내는 **WSMAN_DATA_TYPE_WS_XML_READER** 구조에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-333">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="88ad7-334">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88ad7-334">Cmdlets Supported</span></span>

- [<span data-ttu-id="88ad7-335">New-Item</span><span class="sxs-lookup"><span data-stu-id="88ad7-335">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="88ad7-336">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="88ad7-336">Using the pipeline</span></span>

<span data-ttu-id="88ad7-337">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-337">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="88ad7-338">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-338">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="88ad7-339">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88ad7-339">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="88ad7-340">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="88ad7-340">Getting help</span></span>

<span data-ttu-id="88ad7-341">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-341">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="88ad7-342">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ad7-342">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="88ad7-343">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88ad7-343">See also</span></span>

[<span data-ttu-id="88ad7-344">about_Providers</span><span class="sxs-lookup"><span data-stu-id="88ad7-344">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

