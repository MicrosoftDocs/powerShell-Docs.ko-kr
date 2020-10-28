---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 컴퓨터에 대한 정보 수집
description: 이 문서에서는 WMI 및 CIM cmdlet을 사용하여 컴퓨터 구성 정보를 수집하는 방법을 보여줍니다.
ms.openlocfilehash: 5088960ab7c049085a9d7c05ec4571b6fd7e3545
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500592"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="c55f6-104">컴퓨터에 대한 정보 수집</span><span class="sxs-lookup"><span data-stu-id="c55f6-104">Collecting Information About Computers</span></span>

<span data-ttu-id="c55f6-105">**CimCmdlets** 모듈의 Cmdlet은 일반 시스템 관리 작업에서 가장 중요한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-105">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="c55f6-106">모든 중요한 하위 시스템 설정은 WMI를 통해 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-106">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="c55f6-107">또한 WMI는 하나 이상의 항목 컬렉션에 있는 개체로 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-107">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="c55f6-108">Windows PowerShell은 개체에서도 작동하며 단일 또는 여러 개체를 동일한 방식으로 처리할 수 있게 해주는 파이프라인이 있기 때문에 일반적인 WMI 액세스를 통해 몇 가지 고급 작업을 매우 적은 노력으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-108">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="c55f6-109">데스크톱 설정 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-109">Listing Desktop Settings</span></span>

<span data-ttu-id="c55f6-110">먼저 로컬 컴퓨터에서 데스크톱 정보를 수집하는 명령을 실행하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-110">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="c55f6-111">이렇게 하면 사용 여부에 관계없이 모든 데스크톱에 대한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-111">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="c55f6-112">일부 WMI 클래스에서 반환되는 정보는 매우 자세할 수 있으며, WMI 클래스에 대한 메타데이터가 포함된 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-112">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="c55f6-113">이러한 메타데이터 속성에는 대부분 **Cim** 으로 시작하는 이름이 있으므로 `Select-Object`를 사용하여 속성을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-113">Because most of these metadata properties have names that begin with **Cim** , you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="c55f6-114">"Cim\*"를 사용하여 값으로 **-ExcludeProperty** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-114">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="c55f6-115">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-115">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="c55f6-116">메타데이터를 필터링하려면 파이프라인 연산자(|)를 사용하여 `Get-CimInstance` 명령의 결과를 `Select-Object -ExcludeProperty "CIM*"`으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-116">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="c55f6-117">BIOS 정보 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-117">Listing BIOS Information</span></span>

<span data-ttu-id="c55f6-118">WMI **Win32_BIOS** 클래스는 로컬 컴퓨터의 시스템 BIOS에 대한 전체 정보를 비교적 간결하게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-118">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="c55f6-119">프로세서 정보 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-119">Listing Processor Information</span></span>

<span data-ttu-id="c55f6-120">정보를 필터링하려는 경우가 많지만 WMI의 **Win32_Processor** 클래스를 사용하여 일반적인 프로세서 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-120">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="c55f6-121">프로세서 제품군에 대한 일반적인 설명 문자열을 위해 **SystemType** 속성을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-121">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="c55f6-122">컴퓨터 제조업체 및 모델 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-122">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="c55f6-123">**Win32_ComputerSystem** 을 통해 컴퓨터 모델 정보를 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-123">Computer model information is also available from **Win32_ComputerSystem** .</span></span> <span data-ttu-id="c55f6-124">OEM 데이터를 제공하기 위해 표시되는 표준 출력을 필터링하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-124">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="c55f6-125">일부 하드웨어의 정보를 직접 반환하는 이러한 명령의 출력 품질은 보유한 데이터에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-125">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="c55f6-126">일부 정보는 하드웨어 제조업체에서 제대로 구성하지 않아 제공되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-126">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="c55f6-127">설치된 핫픽스 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-127">Listing Installed Hotfixes</span></span>

<span data-ttu-id="c55f6-128">**Win32_QuickFixEngineering** 을 사용하여 설치된 모든 핫픽스를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-128">You can list all installed hotfixes by using **Win32_QuickFixEngineering** :</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="c55f6-129">이 클래스는 다음과 같은 핫픽스 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-129">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="c55f6-130">더 간결한 출력을 위해 일부 속성을 제외할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-130">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="c55f6-131">`Get-CimInstance`의 **Property** 매개 변수를 사용하여 **HotFixID** 만 선택할 수도 있지만, 이렇게 하면 기본적으로 모든 메타데이터가 표시되기 때문에 실제로 자세한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-131">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID** , doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

<span data-ttu-id="c55f6-132">`Get-CimInstance`의 **Property** 매개 변수는 PowerShell로 반환되는 개체가 아니라 WMI 클래스 인스턴스에서 반환되는 속성을 제한하기 때문에 추가 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-132">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="c55f6-133">출력을 줄이려면 `Select-Object`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-133">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="c55f6-134">운영 체제 버전 정보 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-134">Listing Operating System Version Information</span></span>

<span data-ttu-id="c55f6-135">**Win32_OperatingSystem** 클래스 속성에는 버전 및 서비스 팩 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-135">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="c55f6-136">이러한 속성만 명시적으로 선택하여 **Win32_OperatingSystem** 에서 버전 정보 요약을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-136">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem** :</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="c55f6-137">`Select-Object`의 **Property** 매개 변수와 함께 와일드카드를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-137">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="c55f6-138">**Build** 또는 **ServicePack** 으로 시작하는 모든 속성을 여기서 사용하는 것이 중요하기 때문에 다음과 같은 형태로 축약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-138">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="c55f6-139">로컬 사용자 및 소유자 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-139">Listing Local Users and Owner</span></span>

<span data-ttu-id="c55f6-140">사용이 허가된 사용자 수, 현재 사용자 수, 소유자 이름 등의 로컬 일반 사용자 정보는 **Win32_OperatingSystem** 클래스의 속성을 선택하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-140">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="c55f6-141">다음과 같이 표시할 속성을 명시적으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-141">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="c55f6-142">와일드카드를 사용하는 더 간결한 버전은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-142">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="c55f6-143">사용 가능한 디스크 공간 가져오기</span><span class="sxs-lookup"><span data-stu-id="c55f6-143">Getting Available Disk Space</span></span>

<span data-ttu-id="c55f6-144">로컬 드라이브의 디스크 공간 및 여유 공간을 보려면 Win32_LogicalDisk WMI 클래스를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-144">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="c55f6-145">DriveType이 3(WMI에서 고정 하드 디스크에 사용하는 값)인 인스턴스만 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-145">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a><span data-ttu-id="c55f6-146">로그온 세션 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="c55f6-146">Getting Logon Session Information</span></span>

<span data-ttu-id="c55f6-147">**Win32_LogonSession** WMI 클래스를 통해 사용자와 관련된 로그온 세션에 대한 일반적인 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-147">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="c55f6-148">컴퓨터에 로그온한 사용자 가져오기</span><span class="sxs-lookup"><span data-stu-id="c55f6-148">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="c55f6-149">Win32_ComputerSystem을 사용하여 특정 컴퓨터 시스템에 로그온한 사용자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-149">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="c55f6-150">이 명령은 시스템 데스크톱에 로그온한 사용자만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-150">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="c55f6-151">컴퓨터에서 로컬 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="c55f6-151">Getting Local Time from a Computer</span></span>

<span data-ttu-id="c55f6-152">**Win32_LocalTime** WMI 클래스를 사용하여 특정 컴퓨터에서 현재 로컬 시간을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-152">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a><span data-ttu-id="c55f6-153">서비스 상태 표시</span><span class="sxs-lookup"><span data-stu-id="c55f6-153">Displaying Service Status</span></span>

<span data-ttu-id="c55f6-154">특정 컴퓨터에서 모든 서비스의 상태를 보려면 앞에서 설명한 대로 `Get-Service` cmdlet을 로컬에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-154">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="c55f6-155">원격 시스템의 경우 **Win32_Service** WMI 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-155">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="c55f6-156">또한 `Select-Object`를 사용하여 결과를 **Status** , **Name** 및 **DisplayName** 으로 필터링하는 경우 출력 형식이 `Get-Service`의 출력 형식과 거의 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-156">If you also use `Select-Object` to filter the results to **Status** , **Name** , and **DisplayName** , the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="c55f6-157">이름이 매우 긴, 가끔 발생하는 서비스의 이름을 전체 표시하려면 **AutoSize** 및 **Wrap** 매개 변수와 함께 `Format-Table`을 사용하여 열 너비를 최적화하고 긴 이름이 잘리는 대신 줄 바꿈되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55f6-157">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
