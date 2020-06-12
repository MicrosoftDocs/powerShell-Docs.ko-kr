---
title: WMI 작업
description: PowerShell은 처음부터 WMI 작업을 위한 cmdlet을 제공했습니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438294"
---
# <a name="chapter-7---working-with-wmi"></a>7장 - WMI 작업

## <a name="wmi-and-cim"></a>WMI 및 CIM

PowerShell은 WMI(Windows Management Instrumentation)와 같은 다른 기술 관련 작업을 위한 cmdlet을 기본으로 제공합니다. 추가 소프트웨어나 모듈을 설치하지 않고도 PowerShell에서 다양한 기본 WMI cmdlet을 이용할 수 있습니다.

PowerShell은 처음부터 WMI 작업을 위한 cmdlet을 제공했습니다. `Get-Command`를 이용하면 PowerShell에 있는 WMI cmdlet을 확인할 수 있습니다. 다음은 PowerShell 버전 5.1을 실행하는 필자의 Windows 10 랩 환경 컴퓨터에서 얻은 결과입니다. 실행 중인 PowerShell 버전에 따라 결과가 다를 수 있습니다.

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

CIM(Common Information Model) cmdlet은 PowerShell 버전 3.0에서 도입되었습니다. CIM cmdlet은 Windows 및 비 Windows 컴퓨터 모두에서 사용할 수 있도록 설계되었습니다. WMI cmdlet은 더 이상 사용되지 않으므로 이전 WMI 대신 CIM cmdlet 사용을 권장합니다.

CIM cmdlet은 모두 단일 모듈 내에 포함됩니다. CIM cmdlet 목록을 얻고 싶다면 아래 예제에서처럼 `Get-Command`를 **Module** 매개 변수와 함께 사용해야 합니다.

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

CIM cmdlet은 WMI 작업을 계속해서 지원하기 때문에 "내가 PowerShell CIM cmdlet으로 WMI를 쿼리할 때면..."이라는 말을 들어도 혼란스러워할 필요가 없습니다.

앞에서도 설명했지만 WMI는 PowerShell과는 별개의 기술이며 지금은 CIM cmdlet을 WMI에 액세스하는 용도로만 사용합니다. 다음 예제에서처럼 WQL(WMI Query Language)을 사용하는 구형 VBScript를 사용하여 WMI를 쿼리할 때도 있습니다.

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

이러한 VBScript에서 WQL 쿼리를 가져온 다음 수정 없이 `Get-CimInstance` cmdlet과 함께 사용할 수 있습니다.

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

필자가 PowerShell에서 WMI를 쿼리할 때 자주 쓰는 방법은 아니지만, 이 기능을 사용하면 기존 VBScript를 PowerShell로 쉽게 마이그레이션할 수 있습니다. WMI 쿼리를 위해 원라이너를 작성할 때 필자는 다음 구문을 사용합니다.

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

일련 번호만 필요하다면 출력을 `Select-Object`로 파이프하고 **SerialNumber** 속성만 지정합니다.

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

기본적으로 백그라운드에서 검색되며 절대 사용되지 않는 다양한 속성이 존재합니다.
이 사실은 로컬 컴퓨터에서 WMI를 쿼리할 때는 큰 문제가 되지 않습니다. 하지만 원격 컴퓨터 쿼리를 시작했다면 정보를 반환하느라 추가 처리 시간이 필요하며 불필요한 추가 정보를 네트워크에서 끌어와야 합니다. `Get-CimInstance`에는 검색하는 정보를 제한하는 **Property** 매개 변수가 있습니다. 이 매개 변수를 이용하면 WMI 쿼리의 효율을 높일 수 있습니다.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

지금까지의 결과에서는 개체가 반환되었습니다. 단순 문자열을 반환하려면 **ExpandProperty** 매개 변수를 사용해야 합니다.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

점선 스타일 구문을 사용하여 단순 문자열을 반환할 수도 있습니다. 이렇게 하면 `Select-Object`에 파이프하지 않아도 됩니다.

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>CIM cmdlet을 이용한 원격 컴퓨터 쿼리

팔자는 지금도 도메인 사용자인 로컬 관리자로 PowerShell을 실행하고 있습니다. `Get-CimInstance` cmdlet을 사용하여 원격 컴퓨터에서 정보를 쿼리하면 액세스 거부 오류 메시지가 표시됩니다.

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

많은 사람들이 PowerShell을 사용할 때 보안을 걱정하지만 PowerShell에서는 GUI와 완전히 같은 권한을 사용할 수 있습니다. 권한이 많지도 않고 적지도 않죠. 이전 예제에는 PowerShell을 실행하는 사용자에게 DC01 서버에서 WMI 정보를 쿼리할 수 있는 권한이 없다는 문제가 있습니다. `Get-CimInstance`에는 **Credential** 매개 변수가 없기 때문에 도메인 관리자로 PowerShell을 다시 시작할 수 있습니다. 하지만 장담하건대 이것은 좋은 방법이 아닙니다. PowerShell에서의 모든 실행이 도메인 관리자로 실행되기 때문입니다. 이 경우 상황에 따라 보안이 위험해질 수도 있습니다.

필자는 최소 권한 원칙에 따라, 명령에 **Credential** 매개 변수가 있다면 이 변수를 이용해 각 명령의 권한을 도메인 관리자 계정으로 승격합니다. `Get-CimInstance`에는 **Credential** 매개 변수가 없으니 이런 상황에서는 먼저 **CimSession**을 만들어야 합니다. 그런 다음 컴퓨터 이름 대신 **CimSession**을 이용해 원격 컴퓨터에서 WMI를 쿼리합니다.

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

CIM 세션은 `$CimSession`이라는 변수에 저장됩니다. 필자는 또한 `Get-Credential` cmdlet을 괄호 안에 넣었기 때문에, 이 항목이 먼저 실행되어 새 세션을 만들기 전에 다른 자격 증명을 입력하라는 메시지가 표시됩니다. 이 장 후반부에 다른 자격 증명을 지정하는 데 더 효율적인 방법을 보여드리겠습니다. 하지만 복잡한 내용이 나오기 전에 이 기본 개념을 반드시 숙지하셔야 합니다.

이제 이전 예제에서 만든 CIM 세션을 `Get-CimInstance` cmdlet과 함께 사용하면 원격 컴퓨터의 WMI에서 BIOS 정보를 쿼리할 수 있습니다.

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

단순히 컴퓨터 이름을 지정하는 대신 CIM 세션을 사용하면 다양한 추가 이점을 얻을 수 있습니다. 같은 컴퓨터에서 여러 쿼리를 실행한다면 각 쿼리에 컴퓨터 이름을 사용하는 것보다 CIM 세션을 사용하는 방법이 더 효율적입니다. CIM 세션을 만들 때는 연결이 한 번만 설정됩니다.
그러면 여러 쿼리에서 동일한 세션을 사용하여 정보를 검색합니다. 컴퓨터 이름을 사용하려면 cmdlet은 개별 쿼리를 이용해 연결을 설정하고 분리해야 합니다.

`Get-CimInstance` cmdlet은 기본적으로 WSMan 프로토콜을 사용합니다. 따라서 원격 컴퓨터를 연결하려면 PowerShell 버전 3.0 이상을 사용해야 합니다. 사실 중요한 것은 PowerShell 버전이 아니라 스택 버전입니다. 스택 버전은 `Test-WSMan` cmdlet을 사용하여 확인할 수 있습니다.
버전은 3.0이어야 합니다. PowerShell 버전 3.0 이상에서 찾을 수 있는 버전입니다.

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

구형 WMI cmdlet은 이전 버전의 Windows와 호환되는 DCOM 프로토콜을 사용합니다. 하지만 DCOM은 Windows 이후 버전에서는 일반적으로 방화벽에 의해 차단됩니다. `New-CimSessionOption` cmdlet을 사용하면 `New-CimSession`과 함께 사용할 DCOM 프로토콜 연결을 만들 수 있습니다. 이렇게 하면 `Get-CimInstance` cmdlet을 사용하여 windows Server 2000 이전 버전의 Windows와 통신할 수 있습니다. 따라서 `Get-CimInstance` cmdlet을 DCOM 프로토콜을 사용하도록 구성된 CimSession과 함께 사용할 때는 원격 컴퓨터에 PowerShell이 없어도 됩니다.

`New-CimSessionOption` cmdlet을 사용하여 DCOM 프로토콜 옵션을 만들고 변수에 저장합니다.

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

도메인 관리자 또는 승격된 자격 증명을 변수에 저장하면 명령별로 계속 입력할 필요가 없어 효율성을 높일 수 있습니다.

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

필자에게는 Windows Server 2008(R2 이외)을 실행하는 SQL03라는 서버가 있습니다. PowerShell이 기본적으로 설치되지 않는 최신 Windows Server 운영 체제입니다.

DCOM을 사용하여 SQL03에 대한 **CimSession**을 만듭니다.

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

이전 명령과는 달리 이번에는 **Credential** 매개 변수의 값을 수동으로 다시 입력하는 대신 `$Cred`라는 변수를 값으로 지정했습니다.

사용하는 기본 프로토콜에 관계없이 동일한 쿼리가 출력됩니다.

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

`Get-CimSession` cmdlet은 **CimSessions**가 현재 연결되어 있는 대상과 사용 중인 프로토콜을 확인하는 용도로 사용합니다.

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

이전에 만든 **CimSessions** 두 개를 모두를 검색하여 `$CimSession`이라는 변수에 저장합니다.

```powershell
$CimSession = Get-CimSession
```

하나는 WSMan 프로토콜을 사용하는 명령으로, 다른 하나는 DCOM을 사용하는 명령으로 두 컴퓨터를 모두 쿼리합니다.

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

필자는 WMI 및 CIM cmdlet에 관한 수많은 블로그 문서를 작성했습니다. 가장 유용한 문서는 WSMan과 DCOM 중 무엇을 사용해야 하는지를 자동으로 결정하고, CIM 세션을 수동으로 확인하는 대신 자동으로 설정하고자 작성한 함수 관련 문서입니다. 이 블로그 문서의 제목은 [Dcom으로의 대체를 이용해 원격 컴퓨터에 대한 CimSessions를 만드는 PowerShell 함수][]입니다.

CIM 세션이 끝나면 `Remove-CimSession` cmdlet을 사용하여 이 세션을 제거해야 합니다. 모든 CIM 세션을 제거하려면 `Get-CimSession`을 `Remove-CimSession`으로 파이프하기만 하면 됩니다.

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>요약

이 장에서는 PowerShell을 사용하여 로컬 및 원격 컴퓨터 모두에서 WMI를 사용하는 방법을 알아보았습니다. 또한 CIM cmdlet을 사용하여 WSMan이나 DCOM 프로토콜을 사용하는 원격 컴퓨터에서 작업하는 방법도 알아보았습니다.

## <a name="review"></a>검토

1. WMI와 CIM cmdlet의 차이점은 무엇인가요?
1. 기본적으로 `Get-CimInstance` cmdlet에서는 어떤 프로토콜을 사용하나요?
1. `Get-CimInstance`를 사용하여 컴퓨터 이름을 지정하는 대신 CIM 세션을 사용하면 어떤 이점을 얻을 수 있나요?
1. `Get-CimInstance`에 사용할 프로토콜을 기본 프로토콜이 아닌 다른 프로토콜로 지정하려면 어떻게 해야 하나요?
1. CIM 세션을 닫거나 제거하려면 어떻게 해야 하나요?

## <a name="recommended-reading"></a>권장 참조 항목

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [CimCmdlets Module][]
- [비디오: CIM Cmdlet 및 CIM 세션 사용][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[비디오: CIM Cmdlet 및 CIM 세션 사용]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Dcom으로의 대체를 이용해 원격 컴퓨터에 대한 CimSessions를 만드는 PowerShell 함수]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
