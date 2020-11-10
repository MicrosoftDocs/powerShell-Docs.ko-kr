---
description: Windows PowerShell에서 WS-Management cmdlet을 사용 하기 위한 배경으로 WS-MANAGEMENT (Web Services for Management)에 대 한 개요를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: d11b8ca72951409a1b9a508623b3f39cae46e318
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390476"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="16382-104">WS-Management Cmdlet 정보</span><span class="sxs-lookup"><span data-stu-id="16382-104">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="16382-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="16382-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="16382-106">Windows PowerShell에서 WS-Management cmdlet을 사용 하기 위한 배경으로 WS-MANAGEMENT (Web Services for Management)에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-106">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="16382-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="16382-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="16382-108">이 항목에서는 Windows PowerShell에서 WS-Management cmdlet을 사용 하기 위한 배경으로 WS-MANAGEMENT (Web Services for Management)에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-108">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="16382-109">또한이 항목에서는 WS-MANAGEMENT에 대 한 자세한 정보를 제공 하는 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-109">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="16382-110">WS-Management의 Microsoft 구현은 WinRM (Windows 원격 관리)이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-110">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="16382-111">WS-Management 정보</span><span class="sxs-lookup"><span data-stu-id="16382-111">About WS-Management</span></span>

<span data-ttu-id="16382-112">Windows 원격 관리는 서로 다른 공급 업체의 하드웨어 및 운영 체제를 상호 운용할 수 있도록 하는 표준 SOAP 기반 방화벽 친화적인 프로토콜인 WS-Management 프로토콜의 Microsoft 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="16382-112">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="16382-113">WS-Management 프로토콜 사양은 시스템에서 IT (정보 기술) 인프라를 통해 관리 정보에 액세스 하 고 교환할 수 있는 일반적인 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-113">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="16382-114">WS-Management 및 IPMI (Intelligent Platform Management Interface)는 이벤트 수집기와 함께 Windows 하드웨어 관리 기능의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="16382-114">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="16382-115">WS-Management 프로토콜은 다음 표준 웹 서비스 사양을 기반으로 합니다. HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-ADDRESSING, WS-TRUST, WS-FEDERATION 및 WS 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="16382-115">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="16382-116">WS-Management 및 WMI</span><span class="sxs-lookup"><span data-stu-id="16382-116">WS-Management and WMI</span></span>

<span data-ttu-id="16382-117">WS-Management은 WMI (WMI(Windows Management Instrumentation))에서 제공 하는 데이터를 검색 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-117">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="16382-118">WS-Management 스크립팅 API 또는 WinRM 명령줄 도구를 사용 하는 스크립트나 응용 프로그램을 사용 하 여 WMI 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-118">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="16382-119">WS-Management는 포함 된 개체를 비롯 한 대부분의 익숙한 WMI 클래스와 작업을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-119">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="16382-120">WMI를 활용 하 여 리소스에 대 한 데이터를 수집 하거나 Windows 기반 컴퓨터에서 리소스를 관리할 수 WS-Management.</span><span class="sxs-lookup"><span data-stu-id="16382-120">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="16382-121">즉, 기존 WMI 클래스 집합을 통해 엔터프라이즈의 디스크, 네트워크 어댑터, 서비스 또는 프로세스와 같은 개체에 대 한 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-121">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="16382-122">표준 WMI IPMI 공급자에서 사용할 수 있는 하드웨어 데이터에도 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-122">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="16382-123">WS-Management Windows PowerShell 공급자 (WSMan)</span><span class="sxs-lookup"><span data-stu-id="16382-123">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="16382-124">WSMan 공급자는 사용 가능한 WS-Management 구성 설정에 대 한 계층 구조 보기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-124">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="16382-125">공급자를 사용 하 여 다양 한 WS-Management 구성 옵션을 탐색 하 고 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-125">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="16382-126">WS-Management 구성</span><span class="sxs-lookup"><span data-stu-id="16382-126">WS-Management Configuration</span></span>

<span data-ttu-id="16382-127">WS-Management 설치 및 구성 되지 않은 경우 Windows PowerShell 원격을 사용할 수 없으며, WS-Management cmdlet이 실행 되지 않으며, WS-Management 스크립트가 실행 되지 않으며, WSMan 공급자가 데이터 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-127">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="16382-128">WS-Management 명령줄 도구, WinRM 및 이벤트 전달은 WS-Management 구성에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="16382-128">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="16382-129">WS-Management Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16382-129">WS-Management Cmdlets</span></span>

<span data-ttu-id="16382-130">WS-Management 기능은 cmdlet 및 WSMan 공급자 집합을 포함 하는 모듈을 통해 Windows PowerShell에서 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16382-130">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="16382-131">이러한 cmdlet을 사용 하 여 로컬 및 원격 컴퓨터에서 WS-Management 설정을 관리 하는 데 필요한 종단 간 작업을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-131">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="16382-132">다음 WS-Management cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-132">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="16382-133">연결 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16382-133">Connection Cmdlets</span></span>

- <span data-ttu-id="16382-134">연결-WSMan: 원격 컴퓨터의 WS-Management (WinRM) 서비스에 로컬 컴퓨터를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-134">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="16382-135">Disconnect-WSMan: 원격 컴퓨터의 WS-Management (WinRM) 서비스에서 로컬 컴퓨터의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-135">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="16382-136">Management-Data Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16382-136">Management-Data Cmdlets</span></span>

- <span data-ttu-id="16382-137">Get WSManInstance: 리소스 URI로 지정 된 리소스 인스턴스에 대 한 관리 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-137">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="16382-138">-WSManAction 호출: 리소스 URI 및 선택기에 의해 지정 된 대상 개체에서 작업을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-138">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="16382-139">새-WSManInstance: 새 관리 리소스 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="16382-139">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="16382-140">-WSManInstance 제거: 관리 리소스 인스턴스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-140">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="16382-141">Set-WSManInstance: 리소스와 관련 된 관리 정보를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-141">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="16382-142">설정 및 구성 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16382-142">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="16382-143">Set-wsmanquickconfig: 원격 관리를 위해 로컬 컴퓨터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-143">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="16382-144">Set-WSManQuickConfig cmdlet을 사용 하 여 WS-Management (WinRM) 서비스에 대 한 원격 연결을 허용 하도록 WS-Management을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16382-144">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="16382-145">Set-WSManQuickConfig cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-145">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="16382-146">WS-Management (WinRM) 서비스가 실행 중인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-146">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="16382-147">WinRM 서비스가 실행 되 고 있지 않으면 Set-WSManQuickConfig cmdlet에서 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-147">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="16382-148">WS-Management (WinRM) 서비스 시작 유형을 자동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-148">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="16382-149">모든 IP 주소의 요청을 수락 하는 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="16382-149">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="16382-150">기본 전송 프로토콜은 HTTP입니다.</span><span class="sxs-lookup"><span data-stu-id="16382-150">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="16382-151">WS-Management 트래픽에 대 한 방화벽 예외를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-151">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="16382-152">참고: Windows Vista, Windows Server 2008 및 이후 버전의 Windows에서이 cmdlet을 실행 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-152">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="16382-153">테스트-WSMan: WS-Management 설치 및 구성 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-153">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="16382-154">Test-WSMan cmdlet은 WS-Management (WinRM) 서비스가 실행 중이 고 로컬 컴퓨터 또는 원격 컴퓨터에서 구성 되었는지 여부를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-154">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="16382-155">Enable-wsmancredssp: 클라이언트 컴퓨터에서 CredSSP 인증을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-155">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="16382-156">Enable-wsmancredssp: 클라이언트 컴퓨터에서 CredSSP 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16382-156">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="16382-157">Enable-wsmancredssp: 클라이언트 컴퓨터에 대 한 CredSSP 관련 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="16382-157">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="16382-158">WS-MANAGEMENT 관련 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16382-158">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="16382-159">새-WSManSessionOption: WS-Management cmdlet의 하나 이상의 매개 변수에 대 한 입력으로 사용할 WSManSessionOption 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="16382-159">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="16382-160">추가 WS-Management 정보</span><span class="sxs-lookup"><span data-stu-id="16382-160">Additional WS-Management Information</span></span>

<span data-ttu-id="16382-161">WS 관리에 대 한 자세한 내용은 Windows 설명서에서 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="16382-161">For more information about WS-Management, see the following topics in the Windows documentation.</span></span>

[<span data-ttu-id="16382-162">Windows 원격 관리</span><span class="sxs-lookup"><span data-stu-id="16382-162">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="16382-163">Windows 원격 관리 정보</span><span class="sxs-lookup"><span data-stu-id="16382-163">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="16382-164">Windows 원격 관리 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="16382-164">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="16382-165">Windows 원격 관리 아키텍처</span><span class="sxs-lookup"><span data-stu-id="16382-165">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="16382-166">WS-Management 프로토콜</span><span class="sxs-lookup"><span data-stu-id="16382-166">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="16382-167">Windows 원격 관리 및 WMI</span><span class="sxs-lookup"><span data-stu-id="16382-167">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="16382-168">리소스 URI</span><span class="sxs-lookup"><span data-stu-id="16382-168">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="16382-169">원격 하드웨어 관리</span><span class="sxs-lookup"><span data-stu-id="16382-169">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="16382-170">이벤트</span><span class="sxs-lookup"><span data-stu-id="16382-170">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="16382-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="16382-171">SEE ALSO</span></span>

[<span data-ttu-id="16382-172">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="16382-172">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="16382-173">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="16382-173">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="16382-174">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="16382-174">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="16382-175">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="16382-175">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="16382-176">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="16382-176">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="16382-177">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="16382-177">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="16382-178">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="16382-178">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="16382-179">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="16382-179">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="16382-180">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="16382-180">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="16382-181">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="16382-181">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="16382-182">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="16382-182">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="16382-183">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="16382-183">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
