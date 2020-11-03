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
# <a name="about-wmi-cmdlets"></a>WMI Cmdlet 정보

## <a name="short-description"></a>간단한 설명

WMI(Windows Management Instrumentation) 및 Windows PowerShell에 대한 배경 정보를 제공합니다.

## <a name="long-description"></a>자세한 설명

이 항목에서는 WMI 기술, Windows PowerShell 용 WMI cmdlet, WMI 기반 원격 서비스, WMI 가속기 및 WMI 문제 해결에 대 한 정보를 제공 합니다. 이 항목에는 WMI에 대 한 자세한 정보 링크도 제공 됩니다.

### <a name="about-wmi"></a>WMI 정보

WMI(Windows Management Instrumentation)는 엔터프라이즈 환경에서 관리 정보에 액세스하기 위한 표준 기술을 개발하는 업계 이니셔티브인 WBEM(Web-Based Enterprise Management)의 Microsoft 구현입니다. WMI는 CIM(Common Information Model) 산업 표준을 사용하여 시스템, 애플리케이션, 네트워크, 디바이스 및 기타 관리되는 구성 요소를 나타냅니다. CIM은 DMTF(Distributed Management Task Force)에서 개발하고 유지 관리합니다. WMI를 사용 하 여 로컬 컴퓨터와 원격 컴퓨터를 관리할 수 있습니다. 예를 들어 WMI를 사용 하 여 다음을 수행할 수 있습니다.

- 원격 컴퓨터에서 프로세스를 시작 합니다.
- 원격으로 컴퓨터를 다시 시작 합니다.
- 로컬 또는 원격 컴퓨터에 설치 된 응용 프로그램 목록을 가져옵니다.
- 로컬 또는 원격 컴퓨터의 Windows 이벤트 로그를 쿼리 합니다.

### <a name="the-wmi-cmdlets-for-windows-powershell"></a>WINDOWS POWERSHELL 용 WMI CMDLET

Windows PowerShell은 기본적으로 Windows PowerShell에서 사용할 수 있는 일련의 cmdlet을 통해 WMI 기능을 구현 합니다. 이러한 cmdlet을 사용 하 여 로컬 및 원격 컴퓨터를 관리 하는 데 필요한 종단 간 작업을 완료할 수 있습니다.

다음 WMI cmdlet이 포함 되어 있습니다.

|cmdlet           |Description                                   |
|-----------------|----------------------------------------------|
|Get-WmiObject    |WMI 클래스 또는 정보 인스턴스를 가져옵니다.  |
|                 |사용 가능한 클래스에 대해 알아봅니다.                  |
|Invoke-WmiMethod |WMI 메서드를 호출합니다.                            |
|Register-WmiEvent|WMI 이벤트를 구독 합니다.                    |
|Remove-WmiObject |WMI 클래스 및 인스턴스를 삭제합니다.            |
|Set-WmiInstance  |WMI 클래스의 인스턴스를 만들거나 수정합니다. |

### <a name="sample-commands"></a>샘플 명령
다음 명령은 로컬 컴퓨터의 BIOS 정보를 표시 합니다.

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

다음 명령은 원격 컴퓨터 3 대의 WinRM 서비스에 대 한 정보를 표시 합니다.

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

다음과 같은 더 복잡 한 명령은 프로그램의 모든 인스턴스를 종료 합니다.

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a>WMI 기반 원격 서비스

WMI를 통해 로컬 시스템을 관리 하는 기능이 유용 하지만 WMI를 강력한 관리 도구로 만드는 원격 기능입니다. WMI는 Microsoft의 DCOM (Distributed Component Object Model)을 사용 하 여 시스템에 연결 하 고 시스템을 관리 합니다. 일부 시스템에서 DCOM 연결을 허용 하도록 구성 해야 할 수도 있습니다.
방화벽 설정 및 잠긴 DCOM 권한은 WMI에서 시스템을 원격으로 관리 하는 기능을 차단할 수 있습니다.

### <a name="wmi-type-accelerators"></a>WMI 유형 가속기

Windows PowerShell에는 WMI 유형 가속기가 포함 됩니다. 이러한 WMI 유형 액셀러레이터 (바로 가기)를 사용 하면 비 유형별 가속기 접근 방식에서 허용 하는 것 보다 더 많은 WMI 개체에 직접 액세스할 수 있습니다.

WMI에서 지원 되는 형식 액셀러레이터는 다음과 같습니다.

[WMISEARCHER]-WMI 개체를 검색 하는 바로 가기입니다.

[WMICLASS]-클래스의 정적 속성 및 메서드에 액세스 하기 위한 바로 가기입니다.

[WMI]-클래스의 단일 인스턴스를 가져오기 위한 바로 가기입니다.

[WMISEARCHER]는 ManagementObjectSearcher의 형식 액셀러레이터입니다. 문자열 생성자를 사용 하 여 GET ()을 수행할 수 있는 검색자를 만들 수 있습니다.

다음은 그 예입니다. 

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

[WMICLASS]는 ManagementClass의 형식 액셀러레이터입니다. 여기에는 WMI 클래스에 대 한 로컬 또는 절대 WMI 경로를 사용 하 고 해당 클래스에 바인딩된 개체를 반환 하는 문자열 생성자가 있습니다.

다음은 그 예입니다. 

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

[WMI]는 ManagementObject에 대 한 유형 가속기입니다. 여기에는 WMI 인스턴스에 대 한 로컬 또는 절대 WMI 경로를 사용 하 고 해당 인스턴스에 바인딩된 개체를 반환 하는 문자열 생성자가 있습니다.

다음은 그 예입니다. 

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a>WMI 문제 해결

원격 컴퓨터에 연결 하려고 할 때 발생할 수 있는 가장 일반적인 문제는 다음과 같습니다.

문제 1: 원격 컴퓨터가 온라인 상태가 아닙니다.

컴퓨터가 오프 라인 상태인 경우에는 WMI를 사용 하 여 연결할 수 없습니다.
다음과 같은 오류 메시지가 표시될 수 있습니다.

```
Remote server machine does not exist or is unavailable
```

이 오류 메시지가 표시 되 면 컴퓨터가 온라인 상태 인지 확인 합니다. 원격 컴퓨터를 ping 해 봅니다.

문제 2: 원격 컴퓨터에 대 한 로컬 관리자 권한이 없습니다.

WMI를 원격으로 사용 하려면 원격 컴퓨터에 대 한 로컬 관리자 권한이 있어야 합니다. 이렇게 하지 않으면 해당 컴퓨터에 대 한 액세스가 거부 됩니다.

네임 스페이스 보안을 확인 하려면:

1. 시작을 클릭 하 고 내 컴퓨터를 마우스 오른쪽 단추로 클릭 한 다음 관리를 클릭 합니다.
2. 컴퓨터 관리에서 서비스 및 응용 프로그램을 확장 하 고 WMI 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 속성을 클릭 합니다.
3. WMI 컨트롤 속성 대화 상자에서 보안 탭을 클릭 합니다.

문제 3: 방화벽에서 원격 컴퓨터에 대 한 액세스를 차단 하 고 있습니다.

WMI는 DCOM (분산 COM) 및 RPC (원격 프로시저 호출) 프로토콜을 사용 하 여 네트워크를 트래버스 합니다. 기본적으로 많은 방화벽은 DCOM 및 RPC 트래픽을 차단 합니다. 방화벽이 이러한 프로토콜을 차단 하는 경우 연결이 실패 합니다. 예를 들어 Microsoft Windows XP 서비스 팩 2의 Windows 방화벽은 DCOM 및 WMI를 비롯 한 모든 원하지 않는 네트워크 트래픽을 자동으로 차단 하도록 구성 됩니다. 기본 구성에서 Windows 방화벽은 들어오는 WMI 요청을 거부 하 고 다음과 같은 오류 메시지가 표시 됩니다.

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a>참고 항목

[WMI 정보](/windows/win32/wmisdk/about-wmi)

[WMI 문제 해결](/windows/win32/wmisdk/wmi-troubleshooting)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[Invoke-WmiMethod](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[Register-WmiEvent](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[Remove-WmiObject](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[Set-WmiInstance](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
