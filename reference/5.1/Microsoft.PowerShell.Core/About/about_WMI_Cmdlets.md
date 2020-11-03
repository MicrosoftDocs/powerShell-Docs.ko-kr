---
description: WMI(Windows Management Instrumentation) 및 Windows PowerShell에 대한 배경 정보를 제공합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223193"
---
# <a name="about-wmi-cmdlets"></a><span data-ttu-id="b2718-104">WMI Cmdlet 정보</span><span class="sxs-lookup"><span data-stu-id="b2718-104">About WMI Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="b2718-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b2718-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b2718-106">WMI(Windows Management Instrumentation) 및 Windows PowerShell에 대한 배경 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-106">Provides background information about Windows Management Instrumentation (WMI) and Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b2718-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="b2718-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b2718-108">이 항목에서는 WMI 기술, Windows PowerShell 용 WMI cmdlet, WMI 기반 원격 서비스, WMI 가속기 및 WMI 문제 해결에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-108">This topic provides information about WMI technology, the WMI cmdlets for Windows PowerShell, WMI-based remoting, WMI accelerators, and WMI troubleshooting.</span></span> <span data-ttu-id="b2718-109">이 항목에는 WMI에 대 한 자세한 정보 링크도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-109">This topic also provides links to more information about WMI.</span></span>

### <a name="about-wmi"></a><span data-ttu-id="b2718-110">WMI 정보</span><span class="sxs-lookup"><span data-stu-id="b2718-110">ABOUT WMI</span></span>

<span data-ttu-id="b2718-111">WMI(Windows Management Instrumentation)는 엔터프라이즈 환경에서 관리 정보에 액세스하기 위한 표준 기술을 개발하는 업계 이니셔티브인 WBEM(Web-Based Enterprise Management)의 Microsoft 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-111">Windows Management Instrumentation (WMI) is the Microsoft implementation of Web-Based Enterprise Management (WBEM), which is an industry initiative to develop a standard technology for accessing management information in an enterprise environment.</span></span> <span data-ttu-id="b2718-112">WMI는 CIM(Common Information Model) 산업 표준을 사용하여 시스템, 애플리케이션, 네트워크, 디바이스 및 기타 관리되는 구성 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-112">WMI uses the Common Information Model (CIM) industry standard to represent systems, applications, networks, devices, and other managed components.</span></span> <span data-ttu-id="b2718-113">CIM은 DMTF(Distributed Management Task Force)에서 개발하고 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-113">CIM is developed and maintained by the Distributed Management Task Force (DMTF).</span></span> <span data-ttu-id="b2718-114">WMI를 사용 하 여 로컬 컴퓨터와 원격 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-114">You can use WMI to manage both local and remote computers.</span></span> <span data-ttu-id="b2718-115">예를 들어 WMI를 사용 하 여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-115">For example, you can use WMI to do the following:</span></span>

- <span data-ttu-id="b2718-116">원격 컴퓨터에서 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-116">Start a process on a remote computer.</span></span>
- <span data-ttu-id="b2718-117">원격으로 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-117">Restart a computer remotely.</span></span>
- <span data-ttu-id="b2718-118">로컬 또는 원격 컴퓨터에 설치 된 응용 프로그램 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-118">Get a list of the applications that are installed on a local or remote computer.</span></span>
- <span data-ttu-id="b2718-119">로컬 또는 원격 컴퓨터의 Windows 이벤트 로그를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-119">Query the Windows event logs on a local or remote computer.</span></span>

### <a name="the-wmi-cmdlets-for-windows-powershell"></a><span data-ttu-id="b2718-120">WINDOWS POWERSHELL 용 WMI CMDLET</span><span class="sxs-lookup"><span data-stu-id="b2718-120">THE WMI CMDLETS FOR WINDOWS POWERSHELL</span></span>

<span data-ttu-id="b2718-121">Windows PowerShell은 기본적으로 Windows PowerShell에서 사용할 수 있는 일련의 cmdlet을 통해 WMI 기능을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-121">Windows PowerShell implements WMI functionality through a set of cmdlets that are available in Windows PowerShell by default.</span></span> <span data-ttu-id="b2718-122">이러한 cmdlet을 사용 하 여 로컬 및 원격 컴퓨터를 관리 하는 데 필요한 종단 간 작업을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-122">You can use these cmdlets to complete the end-to-end tasks necessary to manage local and remote computers.</span></span>

<span data-ttu-id="b2718-123">다음 WMI cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-123">The following WMI cmdlets are included.</span></span>

|<span data-ttu-id="b2718-124">cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2718-124">Cmdlet</span></span>           |<span data-ttu-id="b2718-125">Description</span><span class="sxs-lookup"><span data-stu-id="b2718-125">Description</span></span>                                   |
|-----------------|----------------------------------------------|
|<span data-ttu-id="b2718-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b2718-126">Get-WmiObject</span></span>    |<span data-ttu-id="b2718-127">WMI 클래스 또는 정보 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-127">Gets instances of WMI classes or information</span></span>  |
|                 |<span data-ttu-id="b2718-128">사용 가능한 클래스에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-128">about the available classes.</span></span>                  |
|<span data-ttu-id="b2718-129">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="b2718-129">Invoke-WmiMethod</span></span> |<span data-ttu-id="b2718-130">WMI 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-130">Calls WMI methods.</span></span>                            |
|<span data-ttu-id="b2718-131">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="b2718-131">Register-WmiEvent</span></span>|<span data-ttu-id="b2718-132">WMI 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-132">Subscribes to a WMI event.</span></span>                    |
|<span data-ttu-id="b2718-133">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b2718-133">Remove-WmiObject</span></span> |<span data-ttu-id="b2718-134">WMI 클래스 및 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-134">Deletes WMI classes and instances.</span></span>            |
|<span data-ttu-id="b2718-135">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="b2718-135">Set-WmiInstance</span></span>  |<span data-ttu-id="b2718-136">WMI 클래스의 인스턴스를 만들거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-136">Creates or modifies instances of WMI classes.</span></span> |

### <a name="sample-commands"></a><span data-ttu-id="b2718-137">샘플 명령</span><span class="sxs-lookup"><span data-stu-id="b2718-137">SAMPLE COMMANDS</span></span>
<span data-ttu-id="b2718-138">다음 명령은 로컬 컴퓨터의 BIOS 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-138">The following command displays the BIOS information for the local computer.</span></span>

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

<span data-ttu-id="b2718-139">다음 명령은 원격 컴퓨터 3 대의 WinRM 서비스에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-139">The following command displays information about the WinRM service for three remote computers.</span></span>

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

<span data-ttu-id="b2718-140">다음과 같은 더 복잡 한 명령은 프로그램의 모든 인스턴스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-140">The following more complex command exits all instances of a program.</span></span>

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a><span data-ttu-id="b2718-141">WMI 기반 원격 서비스</span><span class="sxs-lookup"><span data-stu-id="b2718-141">WMI-BASED REMOTING</span></span>

<span data-ttu-id="b2718-142">WMI를 통해 로컬 시스템을 관리 하는 기능이 유용 하지만 WMI를 강력한 관리 도구로 만드는 원격 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-142">While the ability to manage a local system through WMI is useful, it is the remoting capabilities that make WMI a powerful administrative tool.</span></span> <span data-ttu-id="b2718-143">WMI는 Microsoft의 DCOM (Distributed Component Object Model)을 사용 하 여 시스템에 연결 하 고 시스템을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-143">WMI uses Microsoft's Distributed Component Object Model (DCOM) to connect to and manage systems.</span></span> <span data-ttu-id="b2718-144">일부 시스템에서 DCOM 연결을 허용 하도록 구성 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-144">You might have to configure some systems to allow DCOM connections.</span></span>
<span data-ttu-id="b2718-145">방화벽 설정 및 잠긴 DCOM 권한은 WMI에서 시스템을 원격으로 관리 하는 기능을 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-145">Firewall settings and locked-down DCOM permissions can block WMI's ability to remotely manage systems.</span></span>

### <a name="wmi-type-accelerators"></a><span data-ttu-id="b2718-146">WMI 유형 가속기</span><span class="sxs-lookup"><span data-stu-id="b2718-146">WMI TYPE ACCELERATORS</span></span>

<span data-ttu-id="b2718-147">Windows PowerShell에는 WMI 유형 가속기가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-147">Windows PowerShell includes WMI type accelerators.</span></span> <span data-ttu-id="b2718-148">이러한 WMI 유형 액셀러레이터 (바로 가기)를 사용 하면 비 유형별 가속기 접근 방식에서 허용 하는 것 보다 더 많은 WMI 개체에 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-148">These WMI type accelerators (shortcuts) allow more direct access to a WMI objects than a non-type accelerator approach would allow.</span></span>

<span data-ttu-id="b2718-149">WMI에서 지원 되는 형식 액셀러레이터는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-149">The following type accelerators are supported with WMI:</span></span>

<span data-ttu-id="b2718-150">[WMISEARCHER]-WMI 개체를 검색 하는 바로 가기입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-150">[WMISEARCHER] - A shortcut for searching for WMI objects.</span></span>

<span data-ttu-id="b2718-151">[WMICLASS]-클래스의 정적 속성 및 메서드에 액세스 하기 위한 바로 가기입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-151">[WMICLASS] - A shortcut for accessing the static properties and methods of a class.</span></span>

<span data-ttu-id="b2718-152">[WMI]-클래스의 단일 인스턴스를 가져오기 위한 바로 가기입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-152">[WMI] - A shortcut for getting a single instance of a class.</span></span>

<span data-ttu-id="b2718-153">[WMISEARCHER]는 ManagementObjectSearcher의 형식 액셀러레이터입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-153">[WMISEARCHER] is a type accelerator for a ManagementObjectSearcher.</span></span> <span data-ttu-id="b2718-154">문자열 생성자를 사용 하 여 GET ()을 수행할 수 있는 검색자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-154">It can take a string constructor to create a searcher that you can then do a GET() on.</span></span>

<span data-ttu-id="b2718-155">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b2718-155">For example:</span></span>

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

<span data-ttu-id="b2718-156">[WMICLASS]는 ManagementClass의 형식 액셀러레이터입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-156">[WMICLASS] is a type accelerator for ManagementClass.</span></span> <span data-ttu-id="b2718-157">여기에는 WMI 클래스에 대 한 로컬 또는 절대 WMI 경로를 사용 하 고 해당 클래스에 바인딩된 개체를 반환 하는 문자열 생성자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-157">This has a string constructor that takes a local or absolute WMI path to a WMI class and returns an object that is bound to that class.</span></span>

<span data-ttu-id="b2718-158">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b2718-158">For example:</span></span>

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

<span data-ttu-id="b2718-159">[WMI]는 ManagementObject에 대 한 유형 가속기입니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-159">[WMI] is a type accelerator for ManagementObject.</span></span> <span data-ttu-id="b2718-160">여기에는 WMI 인스턴스에 대 한 로컬 또는 절대 WMI 경로를 사용 하 고 해당 인스턴스에 바인딩된 개체를 반환 하는 문자열 생성자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-160">This has a string constructor that takes a local or absolute WMI path to a WMI instance and returns an object that is bound to that instance.</span></span>

<span data-ttu-id="b2718-161">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b2718-161">For example:</span></span>

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a><span data-ttu-id="b2718-162">WMI 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b2718-162">WMI TROUBLESHOOTING</span></span>

<span data-ttu-id="b2718-163">원격 컴퓨터에 연결 하려고 할 때 발생할 수 있는 가장 일반적인 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-163">The following problems are the most common problems that might occur when you try to connect to a remote computer.</span></span>

<span data-ttu-id="b2718-164">문제 1: 원격 컴퓨터가 온라인 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-164">Problem 1: The remote computer is not online.</span></span>

<span data-ttu-id="b2718-165">컴퓨터가 오프 라인 상태인 경우에는 WMI를 사용 하 여 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-165">If a computer is offline, you will not be able to connect to it by using WMI.</span></span>
<span data-ttu-id="b2718-166">다음과 같은 오류 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-166">You may receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

<span data-ttu-id="b2718-167">이 오류 메시지가 표시 되 면 컴퓨터가 온라인 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-167">If you receive this error message, verify that the computer is online.</span></span> <span data-ttu-id="b2718-168">원격 컴퓨터를 ping 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-168">Try to ping the remote computer.</span></span>

<span data-ttu-id="b2718-169">문제 2: 원격 컴퓨터에 대 한 로컬 관리자 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-169">Problem 2: You do not have local administrator rights on the remote computer.</span></span>

<span data-ttu-id="b2718-170">WMI를 원격으로 사용 하려면 원격 컴퓨터에 대 한 로컬 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-170">To use WMI remotely, you must have local administrator rights on the remote computer.</span></span> <span data-ttu-id="b2718-171">이렇게 하지 않으면 해당 컴퓨터에 대 한 액세스가 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-171">If you do not, access to that computer will be denied.</span></span>

<span data-ttu-id="b2718-172">네임 스페이스 보안을 확인 하려면:</span><span class="sxs-lookup"><span data-stu-id="b2718-172">To verify namespace security:</span></span>

1. <span data-ttu-id="b2718-173">시작을 클릭 하 고 내 컴퓨터를 마우스 오른쪽 단추로 클릭 한 다음 관리를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-173">Click Start, right-click My Computer, and then click Manage.</span></span>
2. <span data-ttu-id="b2718-174">컴퓨터 관리에서 서비스 및 응용 프로그램을 확장 하 고 WMI 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 속성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-174">In Computer Management, expand Services and Applications, right-click WMI Control, and then click Properties.</span></span>
3. <span data-ttu-id="b2718-175">WMI 컨트롤 속성 대화 상자에서 보안 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-175">In the WMI Control Properties dialog box, click  the Security tab.</span></span>

<span data-ttu-id="b2718-176">문제 3: 방화벽에서 원격 컴퓨터에 대 한 액세스를 차단 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-176">Problem 3: A firewall is blocking access to the remote computer.</span></span>

<span data-ttu-id="b2718-177">WMI는 DCOM (분산 COM) 및 RPC (원격 프로시저 호출) 프로토콜을 사용 하 여 네트워크를 트래버스 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-177">WMI uses the DCOM (Distributed COM) and RPC (Remote Procedure Call) protocols to traverse the network.</span></span> <span data-ttu-id="b2718-178">기본적으로 많은 방화벽은 DCOM 및 RPC 트래픽을 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-178">By default, many firewalls block DCOM and RPC traffic.</span></span> <span data-ttu-id="b2718-179">방화벽이 이러한 프로토콜을 차단 하는 경우 연결이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-179">If your firewall is blocking these protocols, your connection will fail.</span></span> <span data-ttu-id="b2718-180">예를 들어 Microsoft Windows XP 서비스 팩 2의 Windows 방화벽은 DCOM 및 WMI를 비롯 한 모든 원하지 않는 네트워크 트래픽을 자동으로 차단 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-180">For example, Windows Firewall in Microsoft Windows XP Service Pack 2 is configured to automatically block all unsolicited network traffic, including DCOM and WMI.</span></span> <span data-ttu-id="b2718-181">기본 구성에서 Windows 방화벽은 들어오는 WMI 요청을 거부 하 고 다음과 같은 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2718-181">In its default configuration, Windows Firewall rejects an incoming WMI request, and you receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a><span data-ttu-id="b2718-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2718-182">SEE ALSO</span></span>

[<span data-ttu-id="b2718-183">WMI 정보</span><span class="sxs-lookup"><span data-stu-id="b2718-183">About WMI</span></span>](/windows/win32/wmisdk/about-wmi)

[<span data-ttu-id="b2718-184">WMI 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b2718-184">WMI Troubleshooting</span></span>](/windows/win32/wmisdk/wmi-troubleshooting)

[<span data-ttu-id="b2718-185">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b2718-185">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="b2718-186">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="b2718-186">Invoke-WmiMethod</span></span>](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[<span data-ttu-id="b2718-187">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="b2718-187">Register-WmiEvent</span></span>](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[<span data-ttu-id="b2718-188">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b2718-188">Remove-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[<span data-ttu-id="b2718-189">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="b2718-189">Set-WmiInstance</span></span>](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
