---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 컴퓨터에 대한 정보 수집
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737239"
---
# <a name="collecting-information-about-computers"></a>컴퓨터에 대한 정보 수집

**CimCmdlets** 모듈의 Cmdlet은 일반 시스템 관리 작업에서 가장 중요한 cmdlet입니다. 모든 중요한 하위 시스템 설정은 WMI를 통해 노출됩니다. 또한 WMI는 하나 이상의 항목 컬렉션에 있는 개체로 데이터를 처리합니다. Windows PowerShell은 개체에서도 작동하며 단일 또는 여러 개체를 동일한 방식으로 처리할 수 있게 해주는 파이프라인이 있기 때문에 일반적인 WMI 액세스를 통해 몇 가지 고급 작업을 매우 적은 노력으로 수행할 수 있습니다.

## <a name="listing-desktop-settings"></a>데스크톱 설정 표시

먼저 로컬 컴퓨터에서 데스크톱 정보를 수집하는 명령을 실행하겠습니다.

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

이렇게 하면 사용 여부에 관계없이 모든 데스크톱에 대한 정보가 반환됩니다.

> [!NOTE]
> 일부 WMI 클래스에서 반환되는 정보는 매우 자세할 수 있으며, WMI 클래스에 대한 메타데이터가 포함된 경우도 있습니다.

이러한 메타데이터 속성에는 대부분 **Cim**으로 시작하는 이름이 있으므로 `Select-Object`를 사용하여 속성을 필터링할 수 있습니다. "Cim*"를 사용하여 값으로 **-ExcludeProperty** 매개 변수를 지정합니다. 다음은 그 예입니다.

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

메타데이터를 필터링하려면 파이프라인 연산자(|)를 사용하여 `Get-CimInstance` 명령의 결과를 `Select-Object -ExcludeProperty "CIM*"`으로 보냅니다.

## <a name="listing-bios-information"></a>BIOS 정보 표시

WMI **Win32_BIOS** 클래스는 로컬 컴퓨터의 시스템 BIOS에 대한 전체 정보를 비교적 간결하게 반환합니다.

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a>프로세서 정보 표시

정보를 필터링하려는 경우가 많지만 WMI의 **Win32_Processor** 클래스를 사용하여 일반적인 프로세서 정보를 검색할 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

프로세서 제품군에 대한 일반적인 설명 문자열을 위해 **SystemType** 속성을 반환할 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>컴퓨터 제조업체 및 모델 표시

**Win32_ComputerSystem**을 통해 컴퓨터 모델 정보를 확인할 수도 있습니다. OEM 데이터를 제공하기 위해 표시되는 표준 출력을 필터링하지 않아도 됩니다.

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

일부 하드웨어의 정보를 직접 반환하는 이러한 명령의 출력 품질은 보유한 데이터에 따라 달라집니다. 일부 정보는 하드웨어 제조업체에서 제대로 구성하지 않아 제공되지 않을 수도 있습니다.

## <a name="listing-installed-hotfixes"></a>설치된 핫픽스 표시

**Win32_QuickFixEngineering**을 사용하여 설치된 모든 핫픽스를 표시할 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

이 클래스는 다음과 같은 핫픽스 목록을 반환합니다.

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

더 간결한 출력을 위해 일부 속성을 제외할 수도 있습니다. `Get-CimInstance`의 **Property** 매개 변수를 사용하여 **HotFixID**만 선택할 수도 있지만, 이렇게 하면 기본적으로 모든 메타데이터가 표시되기 때문에 실제로 자세한 정보가 반환됩니다.

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

`Get-CimInstance`의 **Property** 매개 변수는 PowerShell로 반환되는 개체가 아니라 WMI 클래스 인스턴스에서 반환되는 속성을 제한하기 때문에 추가 데이터가 반환됩니다. 출력을 줄이려면 `Select-Object`를 사용합니다.

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>운영 체제 버전 정보 표시

**Win32_OperatingSystem** 클래스 속성에는 버전 및 서비스 팩 정보가 포함되어 있습니다. 이러한 속성만 명시적으로 선택하여 **Win32_OperatingSystem**에서 버전 정보 요약을 가져올 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

`Select-Object`의 **Property** 매개 변수와 함께 와일드카드를 사용할 수도 있습니다. **Build** 또는 **ServicePack**으로 시작하는 모든 속성을 여기서 사용하는 것이 중요하기 때문에 다음과 같은 형태로 축약할 수 있습니다.

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

## <a name="listing-local-users-and-owner"></a>로컬 사용자 및 소유자 표시

사용이 허가된 사용자 수, 현재 사용자 수, 소유자 이름 등의 로컬 일반 사용자 정보는 **Win32_OperatingSystem** 클래스의 속성을 선택하여 확인할 수 있습니다. 다음과 같이 표시할 속성을 명시적으로 선택할 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

와일드카드를 사용하는 더 간결한 버전은 다음과 같습니다.

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>사용 가능한 디스크 공간 가져오기

로컬 드라이브의 디스크 공간 및 여유 공간을 보려면 Win32_LogicalDisk WMI 클래스를 사용하면 됩니다.
DriveType이 3(WMI에서 고정 하드 디스크에 사용하는 값)인 인스턴스만 표시해야 합니다.

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

## <a name="getting-logon-session-information"></a>로그온 세션 정보 가져오기

**Win32_LogonSession** WMI 클래스를 통해 사용자와 관련된 로그온 세션에 대한 일반적인 정보를 가져올 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>컴퓨터에 로그온한 사용자 가져오기

Win32_ComputerSystem을 사용하여 특정 컴퓨터 시스템에 로그온한 사용자를 표시할 수 있습니다. 이 명령은 시스템 데스크톱에 로그온한 사용자만 반환합니다.

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a>컴퓨터에서 로컬 시간 가져오기

**Win32_LocalTime** WMI 클래스를 사용하여 특정 컴퓨터에서 현재 로컬 시간을 검색할 수 있습니다.

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

## <a name="displaying-service-status"></a>서비스 상태 표시

특정 컴퓨터에서 모든 서비스의 상태를 보려면 앞에서 설명한 대로 `Get-Service` cmdlet을 로컬에서 사용할 수 있습니다. 원격 시스템의 경우 **Win32_Service** WMI 클래스를 사용할 수 있습니다. 또한 `Select-Object`를 사용하여 결과를 **Status**, **Name** 및 **DisplayName**으로 필터링하는 경우 출력 형식이 `Get-Service`의 출력 형식과 거의 동일합니다.

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

이름이 매우 긴, 가끔 발생하는 서비스의 이름을 전체 표시하려면 **AutoSize** 및 **Wrap** 매개 변수와 함께 `Format-Table`을 사용하여 열 너비를 최적화하고 긴 이름이 잘리는 대신 줄 바꿈되도록 할 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
