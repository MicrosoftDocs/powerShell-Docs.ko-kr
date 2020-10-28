---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: WMI 개체 가져오기 Get CimInstance
description: 이 문서에서는 컴퓨터 시스템에서 WMI 개체의 인스턴스를 가져오는 방법에 대한 몇 가지 예를 보여줍니다.
ms.openlocfilehash: f7a005bbf39cf141e6474815d3e050314830453c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500456"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="84b84-104">WMI 개체 가져오기(Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="84b84-104">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="84b84-105">WMI 개체 가져오기(Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="84b84-105">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="84b84-106">WMI(Windows Management Instrumentation)는 다양한 정보를 일관되게 표시하므로 Windows 시스템 관리를 위한 핵심 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-106">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="84b84-107">WMI가 표시하는 정보의 양이 제한되어 있기 때문에 WMI 개체에 액세스하기 위한 PowerShell cmdlet인 `Get-CimInstance`는 실제 작업을 수행하는 데 있어서 가장 유용한 도구 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-107">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="84b84-108">이 장에서는 CimCmdlets를 사용하여 WMI 개체에 액세스하는 방법과 WMI 개체를 사용하여 특정 작업을 수행하는 방법을 차례로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-108">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="84b84-109">WMI 클래스 표시</span><span class="sxs-lookup"><span data-stu-id="84b84-109">Listing WMI Classes</span></span>

<span data-ttu-id="84b84-110">대부분의 WMI 사용자가 겪는 첫 번째 문제는 WMI를 사용하여 수행할 수 있는 작업을 검색하려고 할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-110">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="84b84-111">WMI 클래스는 관리 가능한 리소스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-111">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="84b84-112">이러한 WMI 클래스는 수백 개가 있고 일부 클래스에는 수십 개의 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-112">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="84b84-113">`Get-CimClass`는 이 문제를 해결하기 위해 WMI를 검색 가능하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-113">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="84b84-114">다음과 같이 입력하면 로컬 컴퓨터에서 사용할 수 있는 WMI 클래스의 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-114">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

<span data-ttu-id="84b84-115">다음과 같이 **ComputerName** 매개 변수를 사용하여 컴퓨터 이름과 IP 주소를 지정하면 원격 컴퓨터에서도 이 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-115">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="84b84-116">원격 컴퓨터에서 반환되는 클래스 목록은 컴퓨터가 실행 중인 운영 체제와 설치된 애플리케이션에서 추가한 WMI 확장에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-116">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="84b84-117">CIM cmdlet을 사용하여 원격 컴퓨터에 연결할 때는 원격 컴퓨터에서 WMI를 실행 중이어야 하고, 사용 중인 계정이 원격 컴퓨터의 로컬 관리자 그룹에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-117">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="84b84-118">원격 시스템에는 PowerShell을 설치하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-118">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="84b84-119">이 경우 관리자는 PowerShell을 실행 중이지 않지만 WMI를 사용할 수 있는 운영 체제를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-119">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="84b84-120">WMI 클래스 세부 정보 표시</span><span class="sxs-lookup"><span data-stu-id="84b84-120">Displaying WMI Class Details</span></span>

<span data-ttu-id="84b84-121">WMI 클래스의 이름을 알고 있으면 이 이름을 사용하여 정보를 즉시 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-121">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="84b84-122">예를 들어 컴퓨터에 대한 정보를 검색하는 데 일반적으로 사용되는 WMI 클래스 중 하나는 **Win32_OperatingSystem** 입니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-122">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem** .</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="84b84-123">이 명령에는 매개 변수가 모두 나와 있지만 불필요한 매개 변수를 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-123">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="84b84-124">로컬 시스템에 연결할 때는 **ComputerName** 매개 변수가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-124">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="84b84-125">여기에 이 매개 변수를 표시한 것은 가장 일반적인 경우를 보여 주고 이 매개 변수가 있다는 것을 알려 주기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-125">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="84b84-126">**Namespace** 는 기본적으로 `root/CIMV2`로 설정되며 마찬가지로 생략될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-126">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="84b84-127">마지막으로 대부분의 cmdlet에서는 일반적인 매개 변수의 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-127">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="84b84-128">`Get-CimInstance`를 사용할 때 첫 번째 매개 변수의 이름을 지정하지 않으면 PowerShell은 이 매개 변수를 **Class** 매개 변수로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-128">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="84b84-129">즉, 다음과 같이 입력하여 위 명령을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-129">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="84b84-130">**Win32_OperatingSystem** 클래스에는 여기에 표시된 것보다 훨씬 더 많은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-130">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="84b84-131">Get-Member를 사용하면 이러한 속성을 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-131">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="84b84-132">다음과 같이 WMI 클래스의 속성도 다른 개체 속성처럼 자동으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-132">The properties of a WMI class are automatically available like other object properties:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="84b84-133">Format Cmdlet을 사용하여 기본 속성이 아닌 속성 표시</span><span class="sxs-lookup"><span data-stu-id="84b84-133">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="84b84-134">기본적으로 표시되지 않는 **Win32_OperatingSystem** 클래스에 포함된 정보를 보려면 **Format** cmdlet을 사용하여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-134">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="84b84-135">예를 들어 사용 가능한 메모리 데이터를 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-135">For example, if you want to display available memory data, type:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> <span data-ttu-id="84b84-136">`Format-Table`의 속성 이름에 와일드카드를 사용할 수 있으므로 최종 파이프라인 요소를 `Format-Table -Property Total*Memory*, Free*`로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-136">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="84b84-137">다음과 같이 입력하여 메모리 데이터를 목록으로 표시하면 더 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b84-137">The memory data might be more readable if you format it as a list by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
