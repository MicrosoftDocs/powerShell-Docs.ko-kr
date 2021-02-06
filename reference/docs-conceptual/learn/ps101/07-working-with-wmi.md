---
title: WMI 작업
description: PowerShell은 처음부터 WMI 작업을 위한 cmdlet을 제공했습니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 119bb3381ee55c70340da89d1c0690d84b3e70d2
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99601040"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="15605-103">7장 - WMI 작업</span><span class="sxs-lookup"><span data-stu-id="15605-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="15605-104">WMI 및 CIM</span><span class="sxs-lookup"><span data-stu-id="15605-104">WMI and CIM</span></span>

<span data-ttu-id="15605-105">PowerShell은 WMI(Windows Management Instrumentation)와 같은 다른 기술 관련 작업을 위한 cmdlet을 기본으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="15605-106">추가 소프트웨어나 모듈을 설치하지 않고도 PowerShell에서 다양한 기본 WMI cmdlet을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="15605-107">PowerShell은 처음부터 WMI 작업을 위한 cmdlet을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="15605-108">`Get-Command`를 이용하면 PowerShell에 있는 WMI cmdlet을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="15605-109">다음은 PowerShell 버전 5.1을 실행하는 필자의 Windows 10 랩 환경 컴퓨터에서 얻은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="15605-110">실행 중인 PowerShell 버전에 따라 결과가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="15605-111">CIM(Common Information Model) cmdlet은 PowerShell 버전 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="15605-112">CIM cmdlet은 Windows 및 비 Windows 컴퓨터 모두에서 사용할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="15605-113">WMI cmdlet은 더 이상 사용되지 않으므로 이전 WMI 대신 CIM cmdlet 사용을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="15605-114">CIM cmdlet은 모두 단일 모듈 내에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="15605-115">CIM cmdlet 목록을 얻고 싶다면 아래 예제에서처럼 `Get-Command`를 **Module** 매개 변수와 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="15605-116">CIM cmdlet은 WMI 작업을 계속해서 지원하기 때문에 "내가 PowerShell CIM cmdlet으로 WMI를 쿼리할 때면..."이라는 말을 들어도 혼란스러워할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="15605-117">앞에서도 설명했지만 WMI는 PowerShell과는 별개의 기술이며 지금은 CIM cmdlet을 WMI에 액세스하는 용도로만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="15605-118">다음 예제에서처럼 WQL(WMI Query Language)을 사용하는 구형 VBScript를 사용하여 WMI를 쿼리할 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="15605-119">이러한 VBScript에서 WQL 쿼리를 가져온 다음 수정 없이 `Get-CimInstance` cmdlet과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="15605-120">필자가 PowerShell에서 WMI를 쿼리할 때 자주 쓰는 방법은 아니지만,</span><span class="sxs-lookup"><span data-stu-id="15605-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="15605-121">이 기능을 사용하면 기존 VBScript를 PowerShell로 쉽게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="15605-122">WMI 쿼리를 위해 원라이너를 작성할 때 필자는 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="15605-123">일련 번호만 필요하다면 출력을 `Select-Object`로 파이프하고 **SerialNumber** 속성만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="15605-124">기본적으로 백그라운드에서 검색되며 절대 사용되지 않는 다양한 속성이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="15605-125">이 사실은 로컬 컴퓨터에서 WMI를 쿼리할 때는 큰 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="15605-126">하지만 원격 컴퓨터 쿼리를 시작했다면 정보를 반환하느라 추가 처리 시간이 필요하며 불필요한 추가 정보를 네트워크에서 끌어와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="15605-127">`Get-CimInstance`에는 검색하는 정보를 제한하는 **Property** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="15605-128">이 매개 변수를 이용하면 WMI 쿼리의 효율을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="15605-129">지금까지의 결과에서는 개체가 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-129">The previous results returned an object.</span></span> <span data-ttu-id="15605-130">단순 문자열을 반환하려면 **ExpandProperty** 매개 변수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="15605-131">점선 스타일 구문을 사용하여 단순 문자열을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="15605-132">이렇게 하면 `Select-Object`에 파이프하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="15605-133">CIM cmdlet을 이용한 원격 컴퓨터 쿼리</span><span class="sxs-lookup"><span data-stu-id="15605-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="15605-134">팔자는 지금도 도메인 사용자인 로컬 관리자로 PowerShell을 실행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="15605-135">`Get-CimInstance` cmdlet을 사용하여 원격 컴퓨터에서 정보를 쿼리하면 액세스 거부 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="15605-136">많은 사람들이 PowerShell을 사용할 때 보안을 걱정하지만 PowerShell에서는 GUI와 완전히 같은 권한을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="15605-137">권한이 많지도 않고 적지도 않죠.</span><span class="sxs-lookup"><span data-stu-id="15605-137">No more and no less.</span></span> <span data-ttu-id="15605-138">이전 예제에는 PowerShell을 실행하는 사용자에게 DC01 서버에서 WMI 정보를 쿼리할 수 있는 권한이 없다는 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="15605-139">`Get-CimInstance`에는 **Credential** 매개 변수가 없기 때문에 도메인 관리자로 PowerShell을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="15605-140">하지만 장담하건대 이것은 좋은 방법이 아닙니다. PowerShell에서의 모든 실행이 도메인 관리자로 실행되기 때문입니다. 이 경우 상황에 따라 보안이 위험해질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="15605-141">필자는 최소 권한 원칙에 따라, 명령에 **Credential** 매개 변수가 있다면 이 변수를 이용해 각 명령의 권한을 도메인 관리자 계정으로 승격합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="15605-142">`Get-CimInstance`에는 **Credential** 매개 변수가 없으니 이런 상황에서는 먼저 **CimSession** 을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="15605-143">그런 다음 컴퓨터 이름 대신 **CimSession** 을 이용해 원격 컴퓨터에서 WMI를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="15605-144">CIM 세션은 `$CimSession`이라는 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="15605-145">필자는 또한 `Get-Credential` cmdlet을 괄호 안에 넣었기 때문에, 이 항목이 먼저 실행되어 새 세션을 만들기 전에 다른 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="15605-146">이 장 후반부에 다른 자격 증명을 지정하는 데 더 효율적인 방법을 보여드리겠습니다. 하지만 복잡한 내용이 나오기 전에 이 기본 개념을 반드시 숙지하셔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="15605-147">이제 이전 예제에서 만든 CIM 세션을 `Get-CimInstance` cmdlet과 함께 사용하면 원격 컴퓨터의 WMI에서 BIOS 정보를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="15605-148">단순히 컴퓨터 이름을 지정하는 대신 CIM 세션을 사용하면 다양한 추가 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="15605-149">같은 컴퓨터에서 여러 쿼리를 실행한다면 각 쿼리에 컴퓨터 이름을 사용하는 것보다 CIM 세션을 사용하는 방법이 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="15605-150">CIM 세션을 만들 때는 연결이 한 번만 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="15605-151">그러면 여러 쿼리에서 동일한 세션을 사용하여 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="15605-152">컴퓨터 이름을 사용하려면 cmdlet은 개별 쿼리를 이용해 연결을 설정하고 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="15605-153">`Get-CimInstance` cmdlet은 기본적으로 WSMan 프로토콜을 사용합니다. 따라서 원격 컴퓨터를 연결하려면 PowerShell 버전 3.0 이상을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="15605-154">사실 중요한 것은 PowerShell 버전이 아니라 스택 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="15605-155">스택 버전은 `Test-WSMan` cmdlet을 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="15605-156">버전은 3.0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-156">It needs to be version 3.0.</span></span> <span data-ttu-id="15605-157">PowerShell 버전 3.0 이상에서 찾을 수 있는 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="15605-158">구형 WMI cmdlet은 이전 버전의 Windows와 호환되는 DCOM 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="15605-159">하지만 DCOM은 Windows 이후 버전에서는 일반적으로 방화벽에 의해 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="15605-160">`New-CimSessionOption` cmdlet을 사용하면 `New-CimSession`과 함께 사용할 DCOM 프로토콜 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="15605-161">이렇게 하면 `Get-CimInstance` cmdlet을 사용하여 windows Server 2000 이전 버전의 Windows와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="15605-162">따라서 `Get-CimInstance` cmdlet을 DCOM 프로토콜을 사용하도록 구성된 CimSession과 함께 사용할 때는 원격 컴퓨터에 PowerShell이 없어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="15605-163">`New-CimSessionOption` cmdlet을 사용하여 DCOM 프로토콜 옵션을 만들고 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="15605-164">도메인 관리자 또는 승격된 자격 증명을 변수에 저장하면 명령별로 계속 입력할 필요가 없어 효율성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="15605-165">필자에게는 Windows Server 2008(R2 이외)을 실행하는 SQL03라는 서버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="15605-166">PowerShell이 기본적으로 설치되지 않는 최신 Windows Server 운영 체제입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="15605-167">DCOM을 사용하여 SQL03에 대한 **CimSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15605-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="15605-168">이전 명령과는 달리 이번에는 **Credential** 매개 변수의 값을 수동으로 다시 입력하는 대신 `$Cred`라는 변수를 값으로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="15605-169">사용하는 기본 프로토콜에 관계없이 동일한 쿼리가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="15605-170">`Get-CimSession` cmdlet은 **CimSessions** 가 현재 연결되어 있는 대상과 사용 중인 프로토콜을 확인하는 용도로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="15605-171">이전에 만든 **CimSessions** 두 개를 모두를 검색하여 `$CimSession`이라는 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="15605-172">하나는 WSMan 프로토콜을 사용하는 명령으로, 다른 하나는 DCOM을 사용하는 명령으로 두 컴퓨터를 모두 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="15605-173">필자는 WMI 및 CIM cmdlet에 관한 수많은 블로그 문서를 작성했습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="15605-174">가장 유용한 문서는 WSMan과 DCOM 중 무엇을 사용해야 하는지를 자동으로 결정하고, CIM 세션을 수동으로 확인하는 대신 자동으로 설정하고자 작성한 함수 관련 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="15605-175">이 블로그 문서의 제목은 [Dcom으로의 대체를 이용해 원격 컴퓨터에 대한 CimSessions를 만드는 PowerShell 함수][]입니다.</span><span class="sxs-lookup"><span data-stu-id="15605-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="15605-176">CIM 세션이 끝나면 `Remove-CimSession` cmdlet을 사용하여 이 세션을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15605-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="15605-177">모든 CIM 세션을 제거하려면 `Get-CimSession`을 `Remove-CimSession`으로 파이프하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15605-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="15605-178">요약</span><span class="sxs-lookup"><span data-stu-id="15605-178">Summary</span></span>

<span data-ttu-id="15605-179">이 장에서는 PowerShell을 사용하여 로컬 및 원격 컴퓨터 모두에서 WMI를 사용하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="15605-180">또한 CIM cmdlet을 사용하여 WSMan이나 DCOM 프로토콜을 사용하는 원격 컴퓨터에서 작업하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="15605-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="15605-181">검토</span><span class="sxs-lookup"><span data-stu-id="15605-181">Review</span></span>

1. <span data-ttu-id="15605-182">WMI와 CIM cmdlet의 차이점은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="15605-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="15605-183">기본적으로 `Get-CimInstance` cmdlet에서는 어떤 프로토콜을 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="15605-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="15605-184">`Get-CimInstance`를 사용하여 컴퓨터 이름을 지정하는 대신 CIM 세션을 사용하면 어떤 이점을 얻을 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="15605-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="15605-185">`Get-CimInstance`에 사용할 프로토콜을 기본 프로토콜이 아닌 다른 프로토콜로 지정하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="15605-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="15605-186">CIM 세션을 닫거나 제거하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="15605-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="15605-187">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="15605-187">Recommended Reading</span></span>

- <span data-ttu-id="15605-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="15605-188">[about_WMI][]</span></span>
- <span data-ttu-id="15605-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="15605-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="15605-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="15605-190">[about_WQL][]</span></span>
- <span data-ttu-id="15605-191">[CimCmdlets Module][]</span><span class="sxs-lookup"><span data-stu-id="15605-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="15605-192">[비디오: CIM Cmdlet 및 CIM 세션 사용][]</span><span class="sxs-lookup"><span data-stu-id="15605-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[비디오: CIM Cmdlet 및 CIM 세션 사용]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Dcom으로의 대체를 이용해 원격 컴퓨터에 대한 CimSessions를 만드는 PowerShell 함수]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
