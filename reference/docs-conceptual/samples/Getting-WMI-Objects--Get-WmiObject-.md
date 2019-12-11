---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: WMI 개체 가져오기(Get WmiObject)
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030220"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>WMI 개체 가져오기(Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>WMI 개체 가져오기(Get-WmiObject)

WMI(Windows Management Instrumentation)는 다양한 정보를 일관되게 표시하므로 Windows 시스템 관리를 위한 핵심 기술입니다. WMI가 표시하는 정보의 양이 제한되어 있기 때문에 WMI 개체에 액세스하기 위한 Windows PowerShell cmdlet인 **Get-WmiObject**는 실제 작업을 수행하는 데 있어서 가장 유용한 도구 중 하나입니다. 이 장에서는 Get-WmiObject를 사용하여 WMI 개체에 액세스하는 방법과 WMI 개체를 사용하여 특정 작업을 수행하는 방법을 차례로 설명합니다.

### <a name="listing-wmi-classes"></a>WMI 클래스 표시

대부분의 WMI 사용자가 겪는 첫 번째 문제는 WMI를 사용하여 수행할 수 있는 작업을 검색하려고 할 때 발생합니다. WMI 클래스는 관리 가능한 리소스를 설명합니다. 이러한 WMI 클래스는 수백 개가 있고 일부 클래스에는 수십 개의 속성이 포함되어 있습니다.

**Get-WmiObject**는 이 문제를 해결하기 위해 WMI를 검색 가능하게 합니다. 다음과 같이 입력하면 로컬 컴퓨터에서 사용할 수 있는 WMI 클래스의 목록을 볼 수 있습니다.

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

다음과 같이 ComputerName 매개 변수를 사용하여 컴퓨터 이름과 IP 주소를 지정하면 원격 컴퓨터에서도 이 정보를 검색할 수 있습니다.

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

원격 컴퓨터에서 반환되는 클래스 목록은 컴퓨터가 실행 중인 운영 체제와 설치된 애플리케이션에서 추가한 WMI 확장에 따라 다를 수 있습니다.

> [!NOTE]
> Get-WmiObject를 사용하여 원격 컴퓨터에 연결할 때는 원격 컴퓨터에서 WMI를 실행 중이어야 하고, 기본 구성에서는 사용 중인 계정이 원격 컴퓨터의 로컬 관리자 그룹에 있어야 합니다. 원격 시스템에는 Windows PowerShell을 설치하지 않아도 됩니다. 이 경우 관리자는 Windows PowerShell을 실행 중이지 않지만 WMI를 사용할 수 있는 운영 체제를 관리할 수 있습니다.

로컬 시스템에 연결할 때 ComputerName을 포함할 수도 있습니다. 로컬 컴퓨터의 이름, IP 주소(또는 루프백 주소 127.0.0.1) 또는 WMI 스타일 '.'를 컴퓨터 이름으로 사용할 수 있습니다. IP 주소가 192.168.1.90이고 이름이 Admin01인 컴퓨터에서 Windows PowerShell을 실행 중인 경우 다음 명령을 실행하면 이 컴퓨터에서 사용할 수 있는 모든 WMI 클래스 목록이 반환됩니다.

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject는 기본적으로 root/cimv2 네임스페이스를 사용합니다. 다른 WMI 네임스페이스를 지정하려면 다음과 같이 **Namespace** 매개 변수를 사용하고 해당 네임스페이스 경로를 지정합니다.

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>WMI 클래스 세부 정보 표시

WMI 클래스의 이름을 알고 있으면 이 이름을 사용하여 정보를 즉시 볼 수 있습니다. 예를 들어 컴퓨터에 대한 정보를 검색하는 데 일반적으로 사용되는 WMI 클래스 중 하나는 **Win32_OperatingSystem**입니다.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

이 명령에는 매개 변수가 모두 나와 있지만 불필요한 매개 변수를 표시하지 않을 수 있습니다. 로컬 시스템에 연결할 때는 **ComputerName** 매개 변수가 필요하지 않습니다. 여기에 이 매개 변수를 표시한 것은 가장 일반적인 경우를 보여 주고 이 매개 변수가 있다는 것을 알려 주기 위한 것입니다. **Namespace**는 기본적으로 root/cimv2로 설정되며 마찬가지로 생략될 수 있습니다. 마지막으로 대부분의 cmdlet에서는 일반적인 매개 변수의 이름을 생략할 수 있습니다. Get-WmiObject를 사용할 때 첫 번째 매개 변수의 이름을 지정하지 않으면 Windows PowerShell은 이 매개 변수를 **Class** 매개 변수로 처리합니다. 즉, 다음과 같이 입력하여 위 명령을 실행할 수도 있습니다.

```powershell
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** 클래스에는 여기에 표시된 것보다 훨씬 더 많은 속성이 있습니다. Get-Member를 사용하면 이러한 속성을 모두 볼 수 있습니다. 다음과 같이 WMI 클래스의 속성도 다른 개체 속성처럼 자동으로 사용할 수 있습니다.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Format Cmdlet을 사용하여 기본 속성이 아닌 속성 표시

기본적으로 표시되지 않는 **Win32_OperatingSystem** 클래스에 포함된 정보를 보려면 **Format** cmdlet을 사용하여 표시할 수 있습니다. 예를 들어 사용 가능한 메모리 데이터를 보려면 다음과 같이 입력합니다.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> **Format-Table**의 속성 이름에 와일드카드를 사용할 수 있으므로 최종 파이프라인 요소를 `Format-Table -Property Total,Free`로 줄일 수 있습니다.

다음과 같이 입력하여 메모리 데이터를 목록으로 표시하면 더 쉽게 읽을 수 있습니다.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
