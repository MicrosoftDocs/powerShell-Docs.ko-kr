---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 00680a466c9cc9dd719fbce3d66f4eb10ec47860
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605471"
---
# <span data-ttu-id="41cef-102">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="41cef-102">Get-WSManInstance</span></span>

## <span data-ttu-id="41cef-103">개요</span><span class="sxs-lookup"><span data-stu-id="41cef-103">SYNOPSIS</span></span>
<span data-ttu-id="41cef-104">리소스 URI로 지정된 리소스 인스턴스에 대한 관리 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-104">Displays management information for a resource instance specified by a Resource URI.</span></span>

## <span data-ttu-id="41cef-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41cef-105">SYNTAX</span></span>

### <span data-ttu-id="41cef-106">GetInstance (기본값)</span><span class="sxs-lookup"><span data-stu-id="41cef-106">GetInstance (Default)</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="41cef-107">열거</span><span class="sxs-lookup"><span data-stu-id="41cef-107">Enumerate</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="41cef-108">설명</span><span class="sxs-lookup"><span data-stu-id="41cef-108">DESCRIPTION</span></span>
<span data-ttu-id="41cef-109">**Get WSManInstance** cmdlet은 리소스 URI (Uniform resource identifier)로 지정 된 관리 리소스의 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-109">The **Get-WSManInstance** cmdlet retrieves an instance of a management resource that is specified by a resource Uniform Resource Identifier (URI).</span></span>
<span data-ttu-id="41cef-110">검색 되는 정보는 복합 XML 정보 집합 (개체 또는 단순 값)이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-110">The information that is retrieved can be a complex XML information set, which is an object, or a simple value.</span></span>
<span data-ttu-id="41cef-111">이 cmdlet은 WS-MANAGEMENT (standard Web Services for Management) **Get** 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-111">This cmdlet is the equivalent to the standard Web Services for Management (WS-Management) **Get** command.</span></span>

<span data-ttu-id="41cef-112">이 cmdlet은 WS-Management 연결/전송 계층을 사용하여 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-112">This cmdlet uses the WS-Management connection/transport layer to retrieve information.</span></span>

## <span data-ttu-id="41cef-113">예제</span><span class="sxs-lookup"><span data-stu-id="41cef-113">EXAMPLES</span></span>

### <span data-ttu-id="41cef-114">예제 1: WMI에서 모든 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-114">Example 1: Get all information from WMI</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="winrm"} -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : Windows Remote Management (WS-Management)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Windows Remote Management (WinRM) service implements the WS-Management protocol for remote
management. WS-Management is a standard web services protocol used for remote software and
hardware management. The WinRM service listens on the network for WS-Management requests
and processes them. The WinRM Service needs to be configured with a listener using the
winrm.cmd command line tool or through Group Policy in order for it to listen over the
network. The WinRM service provides access to WMI data and enables event collection. Event
collection and subscription to events require that the service is running. WinRM messages
use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is
preconfigured to share a port with IIS on the same computer.  The WinRM service reserves the
/wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any
websites hosted on IIS do not use the /wsman URL prefix.
DesktopInteract         : false
DisplayName             : Windows Remote Management (WS-Management)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : winrm
PathName                : C:\Windows\System32\svchost.exe -k NetworkService
ProcessId               : 948
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0
```

<span data-ttu-id="41cef-115">이 명령은 WMI(Windows Management Instrumentation) (WMI)가 원격 server01 컴퓨터에서 **WinRM** 서비스에 대해 노출 하는 모든 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-115">This command returns all of the information that Windows Management Instrumentation (WMI) exposes about the **WinRM** service on the remote server01 computer.</span></span>

### <span data-ttu-id="41cef-116">예 2: 스풀러 서비스의 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-116">Example 2: Get the status of the Spooler service</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

<span data-ttu-id="41cef-117">이 명령은 원격 server01 컴퓨터에서 **스풀러** 서비스의 상태만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-117">This command returns only the status of the **Spooler** service on the remote server01 computer.</span></span>

### <span data-ttu-id="41cef-118">예 3: 모든 서비스에 대 한 끝점 참조 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-118">Example 3: Get endpoint references for all services</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/win32_service -ReturnType EPR
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Visual Studio 2008 Remote Debugger
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Allows members of the Administrators group to remotely debug server applications using Visual
Studio 2008. Use the Visual Studio 2008 Remote Debugging Configuration Wizard to enable this
service.
DesktopInteract         : false
DisplayName             : Visual Studio 2008 Remote Debugger
ErrorControl            : Ignore
ExitCode                : 1077
InstallDate             : InstallDate
Name                    : msvsmon90
PathName                : "C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe" /service msvsmon90
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Own Process
Started                 : false
StartMode               : Disabled
StartName               : LocalSystem
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : COMPUTER01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="41cef-119">이 명령은 로컬 컴퓨터에서 모든 서비스에 해당하는 엔드포인트 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-119">This command returns endpoint references that correspond to all the services on the local computer.</span></span>

### <span data-ttu-id="41cef-120">예 4: 지정 된 조건을 충족 하는 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-120">Example 4: Get services that meet specified criteria</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/* -Filter "select * from win32_service where StartMode = 'Auto' and State = 'Stopped'" -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Windows Media Center Service Launcher
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Starts Windows Media Center Scheduler and Windows Media Center Receiver services
at startup if TV is enabled within Windows Media Center.
DesktopInteract         : false
DisplayName             : Windows Media Center Service Launcher
ErrorControl            : Ignore
ExitCode                : 0
InstallDate             : InstallDate
Name                    : ehstart
PathName                : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : false
StartMode               : Auto
StartName               : NT AUTHORITY\LocalService
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : Server01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="41cef-121">이 명령은 원격 Server01 컴퓨터에서 다음 조건을 충족 하는 모든 서비스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-121">This command lists all of the services that meet the following criteria on the remote Server01 computer:</span></span>

- <span data-ttu-id="41cef-122">서비스의 시작 유형은 자동입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-122">The startup type of the service is Automatic.</span></span>
- <span data-ttu-id="41cef-123">서비스가 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-123">The service is stopped.</span></span>

### <span data-ttu-id="41cef-124">예 5: 로컬 컴퓨터의 조건과 일치 하는 수신기 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-124">Example 5: Get listener configuration that matches criteria on the local computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"}
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.123, ::1, 2001:4898:0:fff:0:5efe:123.123.123.123...}
```

<span data-ttu-id="41cef-125">이 명령은 선택기 집합에서 조건과 일치하는 수신기에 대한 WS-Management 수신기 구성을 로컬 컴퓨터에 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-125">This command lists the WS-Management listener configuration on the local computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="41cef-126">예제 6: 원격 컴퓨터의 조건과 일치 하는 수신기 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-126">Example 6: Get listener configuration that matches criteria on a remote computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"} -ComputerName "Server01"
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.124, ::1, 2001:4898:0:fff:0:5efe:123.123.123.124...}
```

<span data-ttu-id="41cef-127">이 명령은 선택기 집합에서 조건과 일치하는 수신기에 대한 WS-Management 수신기 구성을 원격 server01 컴퓨터에 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-127">This command lists the WS-Management listener configuration on the remote server01 computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="41cef-128">예 7: 지정 된 인스턴스와 관련 된 연결 된 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-128">Example 7: Get associated instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
xsi                       : http://www.w3.org/2001/XMLSchema-instance
p                         : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_ComputerSystem
cim                       : http://schemas.dmtf.org/wbem/wscim/1/common
type                      : p:Win32_ComputerSystem_Type
lang                      : en-US
AdminPasswordStatus       : 1
AutomaticManagedPagefile  : true
AutomaticResetBootOption  : true
AutomaticResetCapability  : true
BootOptionOnLimit         : BootOptionOnLimit
BootOptionOnWatchDog      : BootOptionOnWatchDog
BootROMSupported          : true
BootupState               : Normal boot
Caption                   : SERVER01
ChassisBootupState        : 3
CreationClassName         : Win32_ComputerSystem
CurrentTimeZone           : -480
DaylightInEffect          : false
Description               : AT/AT COMPATIBLE
DNSHostName               : server01
Domain                    : site01.corp.fabrikam.com
DomainRole                : 1
EnableDaylightSavingsTime : true
FrontPanelResetStatus     : 2
InfraredSupported         : false
InstallDate               : InstallDate
KeyboardPasswordStatus    : 2
LastLoadInfo              : LastLoadInfo
Manufacturer              : Dell Inc.
Model                     : OptiPlex 745
Name                      : SERVER01
NameFormat                : NameFormat
NetworkServerModeEnabled  : true
NumberOfLogicalProcessors : 2
NumberOfProcessors        : 1
OEMStringArray            : www.dell.com
PartOfDomain              : true
PauseAfterReset           : -1
PCSystemType              : 5
PowerManagementSupported  : PowerManagementSupported
PowerOnPasswordStatus     : 1
PowerState                : 0
PowerSupplyState          : 3
PrimaryOwnerContact       : PrimaryOwnerContact
PrimaryOwnerName          : testuser01
ResetCapability           : 1
ResetCount                : -1
ResetLimit                : -1
Roles                     : {LM_Workstation, LM_Server, SQLServer, NT}
Status                    : OK
SystemStartupDelay        : SystemStartupDelay
SystemStartupSetting      : SystemStartupSetting
SystemType                : X86-based PC
ThermalState              : 3
TotalPhysicalMemory       : 3217760256
UserName                  : FABRIKAM\testuser01
WakeUpType                : 6
Workgroup                 : Workgroup
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Remote Procedure Call (RPC)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Serves as the endpoint mapper and COM Service Control Manager. If this service is stopped
or disabled, programs using COM or Remote Procedure Call (RPC) services will not function
properly.
DesktopInteract         : false
DisplayName             : Remote Procedure Call (RPC)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : RpcSs
PathName                : C:\Windows\system32\svchost.exe -k rpcss
ProcessId               : 1100
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0

xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_SystemDriver
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_SystemDriver_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : HTTP
CreationClassName       : Win32_SystemDriver
Description             : HTTP
DesktopInteract         : false
DisplayName             : HTTP
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : HTTP
PathName                : C:\Windows\system32\drivers\HTTP.sys
ServiceSpecificExitCode : 0
ServiceType             : Kernel Driver
Started                 : true
StartMode               : Manual
StartName               :
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
```

<span data-ttu-id="41cef-129">이 명령은 지정된 인스턴스(winrm)와 관련된 연결된 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-129">This command gets the associated instances that are related to the specified instance (winrm).</span></span>

<span data-ttu-id="41cef-130">예제에 표시된 것처럼 필터를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-130">You must enclose the filter in quotation marks, as shown in the example.</span></span>

### <span data-ttu-id="41cef-131">예 8: 지정 된 인스턴스와 관련 된 연결 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="41cef-131">Example 8: Get association instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

<span data-ttu-id="41cef-132">이 명령은 지정된 인스턴스(winrm)와 관련된 연결 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-132">This command gets association instances that are related to the specified instance (winrm).</span></span>
<span data-ttu-id="41cef-133">*언어* 값이 연결이 고 *association* 매개 변수가 사용 되므로이 명령은 연결 된 인스턴스가 아니라 연결 인스턴스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-133">Because the *Dialect* value is association and the *Associations* parameter is used, this command returns association instances, not associated instances.</span></span>

<span data-ttu-id="41cef-134">예제에 표시된 것처럼 필터를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-134">You must enclose the filter in quotation marks, as shown in the example.</span></span>

## <span data-ttu-id="41cef-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41cef-135">PARAMETERS</span></span>

### <span data-ttu-id="41cef-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="41cef-136">-ApplicationName</span></span>
<span data-ttu-id="41cef-137">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="41cef-138">*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="41cef-139">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="41cef-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="41cef-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="41cef-141">예: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="41cef-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="41cef-142">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="41cef-143">이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="41cef-144">이 매개 변수는 많은 컴퓨터에서 PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="41cef-145">이 경우 IIS는 효율성을 위해 WS-Management를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-145">In this case, IIS hosts WS-Management for efficiency.</span></span>

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

### <span data-ttu-id="41cef-146">-연결</span><span class="sxs-lookup"><span data-stu-id="41cef-146">-Associations</span></span>
<span data-ttu-id="41cef-147">이 cmdlet은 연결 된 인스턴스가 아니라 연결 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-147">Indicates that this cmdlet gets association instances, not associated instances.</span></span>
<span data-ttu-id="41cef-148">이 매개 변수는 *언어* 매개 변수의 값이 Association 인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-148">You can use this parameter only when the *Dialect* parameter has a value of Association.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-149">-인증</span><span class="sxs-lookup"><span data-stu-id="41cef-149">-Authentication</span></span>
<span data-ttu-id="41cef-150">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-150">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="41cef-151">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="41cef-152">기본.</span><span class="sxs-lookup"><span data-stu-id="41cef-152">Basic.</span></span>
<span data-ttu-id="41cef-153">Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-153">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="41cef-154">기본값</span><span class="sxs-lookup"><span data-stu-id="41cef-154">Default.</span></span>
<span data-ttu-id="41cef-155">WS-Management 프로토콜로 구현된 인증 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-155">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="41cef-156">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-156">This is the default.</span></span>
- <span data-ttu-id="41cef-157">다이제스트.</span><span class="sxs-lookup"><span data-stu-id="41cef-157">Digest.</span></span>
<span data-ttu-id="41cef-158">Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-158">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="41cef-159">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="41cef-159">Kerberos.</span></span>
<span data-ttu-id="41cef-160">클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용하여 상호 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-160">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="41cef-161">Negotiate</span><span class="sxs-lookup"><span data-stu-id="41cef-161">Negotiate.</span></span>
<span data-ttu-id="41cef-162">Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-162">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="41cef-163">예를 들어이 매개 변수 값은 협상을 통해 Kerberos 프로토콜 또는 NTLM이 사용 되는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-163">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="41cef-164">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="41cef-164">CredSSP.</span></span>
<span data-ttu-id="41cef-165">사용자가 자격 증명을 위임할 수 있도록 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-165">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="41cef-166">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-166">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="41cef-167">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-167">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="41cef-168">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-168">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="41cef-169">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-169">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-170">-Base속성만</span><span class="sxs-lookup"><span data-stu-id="41cef-170">-BasePropertiesOnly</span></span>
<span data-ttu-id="41cef-171">이 cmdlet은 *ResourceURI* 매개 변수로 지정 된 기본 클래스의 일부인 속성만 열거 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-171">Indicates that this cmdlet enumerates only the properties that are part of the base class that is specified by the *ResourceURI* parameter.</span></span>
<span data-ttu-id="41cef-172">이 매개 변수는 *단순* 매개 변수가 지정 된 경우에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-172">This parameter has no effect if the *Shallow* parameter is specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases: UBPO, Base

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-173">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="41cef-173">-CertificateThumbprint</span></span>
<span data-ttu-id="41cef-174">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-174">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="41cef-175">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-175">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="41cef-176">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-176">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="41cef-177">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-177">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="41cef-178">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-178">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="41cef-179">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="41cef-179">-ComputerName</span></span>
<span data-ttu-id="41cef-180">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-180">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="41cef-181">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-181">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="41cef-182">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-182">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="41cef-183">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-183">The local computer is the default.</span></span>
<span data-ttu-id="41cef-184">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-184">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="41cef-185">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-185">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-186">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="41cef-186">-ConnectionURI</span></span>
<span data-ttu-id="41cef-187">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-187">Specifies the connection endpoint.</span></span>
<span data-ttu-id="41cef-188">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-188">The format of this string is as follows:</span></span>

<span data-ttu-id="41cef-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="41cef-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="41cef-190">다음 문자열은이 매개 변수의 형식이 올바르게 지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-190">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="41cef-191">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-191">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-192">-Credential</span><span class="sxs-lookup"><span data-stu-id="41cef-192">-Credential</span></span>
<span data-ttu-id="41cef-193">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-193">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="41cef-194">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-194">The default is the current user.</span></span>
<span data-ttu-id="41cef-195">User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-195">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="41cef-196">또는 Get-Credential cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-196">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="41cef-197">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-197">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-198">-언어</span><span class="sxs-lookup"><span data-stu-id="41cef-198">-Dialect</span></span>
<span data-ttu-id="41cef-199">필터 조건자에 사용할 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-199">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="41cef-200">원격 서비스에서 지원되는 모든 언어가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-200">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="41cef-201">언어 URI에 다음과 같은 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-201">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="41cef-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="41cef-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="41cef-203">선택기 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="41cef-203">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="41cef-204">연결 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="41cef-204">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-205">-Enumerate</span><span class="sxs-lookup"><span data-stu-id="41cef-205">-Enumerate</span></span>
<span data-ttu-id="41cef-206">이 cmdlet은 관리 리소스의 모든 인스턴스를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-206">Indicates that this cmdlet returns all of the instances of a management resource.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-207">-Filter</span><span class="sxs-lookup"><span data-stu-id="41cef-207">-Filter</span></span>
<span data-ttu-id="41cef-208">열거를 위한 필터 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-208">Specifies the filter expression for the enumeration.</span></span>
<span data-ttu-id="41cef-209">이 매개 변수를 지정 하는 경우 *언어* 도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-209">If you specify this parameter, you must also specify *Dialect*.</span></span>

<span data-ttu-id="41cef-210">이 매개 변수의 유효한 값은 *언어* 에 지정 된 언어에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-210">The valid values of this parameter depend on the dialect that is specified in *Dialect*.</span></span>
<span data-ttu-id="41cef-211">예를 들어 *언어가* WQL 인 경우 *Filter* 매개 변수는 문자열을 포함 해야 하며 문자열은 다음 쿼리와 같은 유효한 WQL 쿼리를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-211">For example, if *Dialect* is WQL, the *Filter* parameter must contain a string, and the string must contain a valid WQL query such as the following query:</span></span>

`"Select * from Win32_Service where State != Running"`

<span data-ttu-id="41cef-212">*언어가* 연결 인 경우 *필터* 는 문자열을 포함 해야 하며 문자열에는 다음 필터와 같은 올바른 필터가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-212">If *Dialect* is Association, *Filter* must contain a string, and the string must contain a valid filter, such as the following filter:</span></span>

`-filter:Object=EPR\[;AssociationClassName=AssocClassName\]\[;ResultClassName=ClassName\]\[;Role=RefPropertyName\]\[;ResultRole=RefPropertyName\]}`

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-213">-조각</span><span class="sxs-lookup"><span data-stu-id="41cef-213">-Fragment</span></span>
<span data-ttu-id="41cef-214">지정된 작업을 위해 업데이트하거나 검색할 인스턴스 내의 섹션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-214">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="41cef-215">예를 들어 스풀러 서비스의 상태를 가져오려면 다음을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-215">For example, to get the status of a spooler service, specify the following:</span></span>

`-Fragment Status`

```yaml
Type: System.String
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-216">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="41cef-216">-OptionSet</span></span>
<span data-ttu-id="41cef-217">요청의 특성을 수정 하거나 구체화 하기 위해 서비스에 대 한 스위치 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-217">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="41cef-218">이러한 스위치는 서비스 마다 다르기 때문에 명령줄 셸에 사용 되는 스위치와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-218">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="41cef-219">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-219">Any number of options can be specified.</span></span>

<span data-ttu-id="41cef-220">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-220">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: OS

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-221">-Port</span><span class="sxs-lookup"><span data-stu-id="41cef-221">-Port</span></span>
<span data-ttu-id="41cef-222">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-222">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="41cef-223">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-223">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="41cef-224">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-224">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="41cef-225">전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-225">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="41cef-226">그러나 *Skipcncheck* 매개 변수가 *sessionoption* 매개 변수의 일부로 지정 된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-226">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="41cef-227">*Skipcncheck* 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-227">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-228">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="41cef-228">-ResourceURI</span></span>
<span data-ttu-id="41cef-229">리소스 클래스 또는 인스턴스의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-229">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="41cef-230">URI는 컴퓨터에서 특정 유형의 리소스 (예: 디스크 또는 프로세스)를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-230">The URI identifies a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="41cef-231">URI는 접두사와 리소스 경로로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-231">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="41cef-232">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="41cef-232">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: RURI

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-233">-ReturnType</span><span class="sxs-lookup"><span data-stu-id="41cef-233">-ReturnType</span></span>
<span data-ttu-id="41cef-234">반환할 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-234">Specifies the type of data to be returned.</span></span>
<span data-ttu-id="41cef-235">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-235">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="41cef-236">Object</span><span class="sxs-lookup"><span data-stu-id="41cef-236">Object</span></span>
- <span data-ttu-id="41cef-237">EPR</span><span class="sxs-lookup"><span data-stu-id="41cef-237">EPR</span></span>
- <span data-ttu-id="41cef-238">ObjectAndEPR</span><span class="sxs-lookup"><span data-stu-id="41cef-238">ObjectAndEPR</span></span>

<span data-ttu-id="41cef-239">기본값은 Object입니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-239">The default value is Object.</span></span>

<span data-ttu-id="41cef-240">개체를 지정 하거나이 매개 변수를 지정 하지 않으면이 cmdlet은 개체만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-240">If you specify Object or do not specify this parameter, this cmdlet returns only objects.</span></span>
<span data-ttu-id="41cef-241">끝점 참조 (EPR)를 지정 하는 경우이 cmdlet은 개체의 끝점 참조만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-241">If you specify endpoint reference (EPR) this cmdlet returns only the endpoint references of the objects.</span></span>
<span data-ttu-id="41cef-242">엔드포인트 참조는 인스턴스의 리소스 URI 및 선택기에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-242">Endpoint references contain information about the resource URI and the selectors for the instance.</span></span>
<span data-ttu-id="41cef-243">ObjectAndEPR를 지정 하는 경우이 cmdlet은 개체와 연결 된 끝점 참조를 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-243">If you specify ObjectAndEPR, this cmdlet returns both the object and its associated endpoint references.</span></span>

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases: RT
Accepted values: object, epr, objectandepr

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-244">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="41cef-244">-SelectorSet</span></span>
<span data-ttu-id="41cef-245">특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-245">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="41cef-246">*SelectorSet* 매개 변수는 리소스의 인스턴스가 둘 이상 있을 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-246">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="41cef-247">*SelectorSet* 매개 변수 값은 해시 테이블 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-247">The value of the *SelectorSet* parameter must be a hash table.</span></span>

<span data-ttu-id="41cef-248">다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-248">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-249">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="41cef-249">-SessionOption</span></span>
<span data-ttu-id="41cef-250">WS-Management 세션에 대 한 확장 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-250">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="41cef-251">New-WSManSessionOption cmdlet을 사용 하 여 만든 **Sessionoption** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-251">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="41cef-252">사용할 수 있는 옵션에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="41cef-252">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: SO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-253">-단순</span><span class="sxs-lookup"><span data-stu-id="41cef-253">-Shallow</span></span>
<span data-ttu-id="41cef-254">이 cmdlet은 리소스 URI에 지정 된 기본 클래스의 인스턴스만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-254">Indicates that this cmdlet returns only instances of the base class that is specified in the resource URI.</span></span>
<span data-ttu-id="41cef-255">이 매개 변수를 지정 하지 않으면이 cmdlet은 URI 및 모든 파생 클래스에서 지정 된 기본 클래스의 인스턴스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-255">If you do not specify this parameter,, this cmdlet returns instances of the base class that is specified in the URI and in all its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-256">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="41cef-256">-UseSSL</span></span>
<span data-ttu-id="41cef-257">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-257">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="41cef-258">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-258">By default, SSL is not used.</span></span>

<span data-ttu-id="41cef-259">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-259">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="41cef-260">*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-260">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="41cef-261">연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-261">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SSL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41cef-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41cef-262">CommonParameters</span></span>
<span data-ttu-id="41cef-263">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41cef-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41cef-264">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41cef-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41cef-265">입력</span><span class="sxs-lookup"><span data-stu-id="41cef-265">INPUTS</span></span>

### <span data-ttu-id="41cef-266">없음</span><span class="sxs-lookup"><span data-stu-id="41cef-266">None</span></span>
<span data-ttu-id="41cef-267">이 명령은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-267">This command does not accept any input.</span></span>

## <span data-ttu-id="41cef-268">출력</span><span class="sxs-lookup"><span data-stu-id="41cef-268">OUTPUTS</span></span>

### <span data-ttu-id="41cef-269">System.Xml.Xml요소</span><span class="sxs-lookup"><span data-stu-id="41cef-269">System.Xml.XmlElement</span></span>
<span data-ttu-id="41cef-270">이 cmdlet은 **XMLElement** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="41cef-270">This cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="41cef-271">참고</span><span class="sxs-lookup"><span data-stu-id="41cef-271">NOTES</span></span>

## <span data-ttu-id="41cef-272">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41cef-272">RELATED LINKS</span></span>

[<span data-ttu-id="41cef-273">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="41cef-273">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="41cef-274">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="41cef-274">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="41cef-275">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="41cef-275">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="41cef-276">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="41cef-276">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="41cef-277">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="41cef-277">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="41cef-278">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="41cef-278">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="41cef-279">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="41cef-279">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="41cef-280">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="41cef-280">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="41cef-281">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="41cef-281">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="41cef-282">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="41cef-282">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="41cef-283">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="41cef-283">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="41cef-284">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="41cef-284">Test-WSMan</span></span>](Test-WSMan.md)

