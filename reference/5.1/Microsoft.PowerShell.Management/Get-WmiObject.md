---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215393"
---
# Get-WmiObject

## 개요
WMI(Windows Management Instrumentation) 클래스 인스턴스 또는 사용 가능한 클래스에 대한 정보를 가져옵니다.

## SYNTAX

### 쿼리 (기본값)

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### list

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### WQLQuery

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### class

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### path

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## 설명

PowerShell 3.0부터이 cmdlet은로 대체 되었습니다 `Get-CimInstance` .

`Get-WmiObject`Cmdlet은 wmi 클래스의 인스턴스 또는 사용 가능한 wmi 클래스에 대 한 정보를 가져옵니다. 원격 컴퓨터를 지정하려면 **ComputerName** 매개 변수를 사용합니다. **List** 매개 변수를 지정하면 cmdlet에서 지정된 네임 스페이스에서 사용할 수 있는 WMI 클래스에 대한 정보를 가져옵니다. **Query** 매개 변수를 지정한 경우 cmdlet이 WQL(WMI Query Language) 문을 실행합니다.

`Get-WmiObject`이 cmdlet은 원격 작업을 수행 하는 데 Windows PowerShell 원격을 사용 하지 않습니다.
**ComputerName** `Get-WmiObject` 컴퓨터가 windows powershell 원격에 대 한 요구 사항을 충족 하지 않거나 windows powershell에서 원격 기능에 대해 구성 되지 않은 경우에도 cmdlet의 ComputerName 매개 변수를 사용할 수 있습니다.

Windows PowerShell 3.0부터을 반환 하는 개체의 **__Server** 속성에는 `Get-WmiObject` **PSComputerName** 별칭이 있습니다. 따라서 출력 및 보고서에 원본 컴퓨터 이름을 더 쉽게 포함할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에서 프로세스 가져오기

이 예제에서는 로컬 컴퓨터의 프로세스를 가져옵니다.

```powershell
Get-WmiObject -Class Win32_Process
```

### 예 2: 원격 컴퓨터의 서비스를 가져옵니다.

이 예제에서는 원격 컴퓨터의 서비스를 가져옵니다. **ComputerName** 매개 변수는 원격 컴퓨터의 IP 주소를 지정 합니다. 기본적으로 현재 사용자 계정은 원격 컴퓨터에서 **Administrators** 그룹의 구성원 이어야 합니다.

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### 예제 3: 로컬 컴퓨터의 루트 또는 기본 네임 스페이스에 WMI 클래스 가져오기

이 예제에서는 로컬 컴퓨터의 루트 또는 기본 네임 스페이스에 있는 WMI 클래스를 가져옵니다.

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### 예제 4: 여러 컴퓨터에 명명 된 서비스 가져오기

이 예제에서는 **ComputerName** 매개 변수 값으로 지정 된 컴퓨터의 WinRM 서비스를 가져옵니다.

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

파이프라인 연산자 (|)가 출력을 cmdlet으로 전송 합니다 `Format-List` . 그러면이 cmdlet이 **PSComputerName** 속성을 기본 출력에 추가 합니다. **PSComputerName** 는을 반환 하는 개체의 **__Server** 속성에 대 한 별칭입니다 `Get-WmiObject` . 이 별칭은 PowerShell 3.0에서 도입 되었습니다.

### 예 5: 원격 컴퓨터에서 서비스 중지

이 예제에서는 원격 컴퓨터의 WinRM 서비스를 중지 합니다. `Get-WmiObject` Server01에 있는 WinRM 서비스 개체의 인스턴스를 가져옵니다. 그런 다음 해당 개체에 **Win32_Service** WMI 클래스의 **StopService** 메서드를 호출 합니다.

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

Cmdlet을 사용 하는 것과 같습니다 `Stop-Service` .

### 예 6: 로컬 컴퓨터에서 BIOS 가져오기

이 예제에서는 로컬 컴퓨터에서 BIOS 정보를 가져옵니다. Cmdlet의 **Property** 매개 변수는 `Format-List` 반환 된 개체의 모든 속성을 목록으로 표시 하는 데 사용 됩니다. 기본적으로 구성 파일에 정의 된 속성의 하위 집합만 `Types.ps1xml` 표시 됩니다.

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### 예 7: 원격 컴퓨터에서 서비스 가져오기

이 예에서는 cmdlet의 **Credential** 매개 변수를 사용 하 여 `Get-WmiObject` 원격 컴퓨터의 서비스를 가져옵니다. **Credential** 매개 변수 값은 사용자 계정 이름입니다. 암호를 입력하라는 메시지가 표시됩니다.

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> 로컬 컴퓨터를 대상으로 하는 경우 자격 증명을 사용할 수 없습니다.

## PARAMETERS

### -수정

WMI에서 반환되는 개체에 수정된 정보가 포함될지를 나타내는 값을 가져오거나 설정합니다. 일반적으로 수정된 정보는 지역화할 수 있는 정보(예: WMI 개체에 연결된 개체 및 속성 설명)입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

명령을 백그라운드 작업으로 실행합니다. 이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.

**AsJob** 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시합니다. 작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다. `Get-WmiObject`가 원격 컴퓨터에서 사용 되는 경우 작업은 로컬 컴퓨터에 만들어지고 원격 컴퓨터의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다. 작업을 관리하려면 Job cmdlet을 포함하는 cmdlet을 사용합니다. 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

> [!NOTE]
> 원격 컴퓨터에 이 매개 변수를 사용하려면 원격을 사용하도록 로컬 및 원격 컴퓨터를 구성해야 합니다. 또한 Windows Vista 이상 버전의 Windows에서 "관리자 권한으로 실행" 옵션을 사용하여 Windows PowerShell을 시작해야 합니다. 자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)을 참조하세요.

Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -인증

WMI 연결에 사용되는 인증 수준을 지정합니다.
유효한 값은 다음과 같습니다.

- -1: 변경 되지 않음
- 0: 기본값
- 1: 없음 (인증이 수행 되지 않음)
- 2: 연결 (클라이언트가 응용 프로그램과의 관계를 설정 하는 경우에만 인증이 수행 됨)
- 3: 호출 (응용 프로그램이 요청을 받을 때 각 호출이 시작 될 때만 인증이 수행 됩니다.)
- 4: 패킷 (클라이언트에서 받은 모든 데이터에 대해 인증이 수행 됩니다.)
- 5: PacketIntegrity (클라이언트와 응용 프로그램 간에 전송 되는 모든 데이터는 인증 되 고 확인 됩니다.)
- 6: PacketPrivacy (다른 인증 수준의 속성이 사용 되며 모든 데이터가 암호화 됩니다.)

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority

WMI 연결을 인증하는 데 사용할 권한을 지정합니다. 표준 NTLM 또는 Kerberos 인증을 지정할 수 있습니다. NTLM을 사용 하려면 권한 설정을로 설정 합니다 `ntlmdomain:<DomainName>` . 여기서은 `<DomainName>` 유효한 NTLM 도메인 이름을 식별 합니다. Kerberos를 사용 하려면를 지정 `kerberos:<DomainName>\<ServerName>` 합니다. 로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.

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

### -클래스

WMI 클래스 이름을 지정합니다. 이 매개 변수를 사용하면 WMI 클래스의 인스턴스를 검색합니다.

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

관리 작업의 대상 컴퓨터를 지정합니다. FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 입력 합니다. 원격 컴퓨터가 로컬 컴퓨터와 다른 도메인에 있는 경우 정규화된 도메인 이름이 필요합니다.

기본값은 로컬 컴퓨터입니다. 컴퓨터 이름 목록 등과 같은 형식으로 로컬 컴퓨터를 지정하려면 "localhost", 로컬 컴퓨터 이름 또는 점(.)을 사용합니다.

이 매개 변수는 WS-Management를 사용하는 Windows PowerShell 원격 기능을 사용하지 않습니다. **ComputerName** `Get-WmiObject` 컴퓨터가 원격 명령 WS-Management 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다. 사용자 이름 (예: "User01", "Domain01\User01")을 입력 User@Contoso.com 합니다. 또는 cmdlet에서 반환 된 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다. 로컬 컴퓨터를 대상으로 하는 경우 자격 증명을 사용할 수 없습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DirectRead

지정된 클래스에 대해 해당 기본 클래스나 파생 클래스와 관계없이 WMI 공급자에 대한 직접 액세스가 요청되었는지 여부를 지정합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

명령에서 WMI 호출을 수행하기 전에 현재 사용자의 모든 권한을 사용하도록 설정합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

필터로 사용할 **Where** 절을 지정합니다. WQL(WMI Query Language) 언어 구문을 사용합니다.

> [!IMPORTANT]
> 매개 변수 값에 **Where** 키워드를 포함하지 마세요. 예를 들어 다음 명령은 **DeviceID** 가 'c:'인 논리 디스크와 **Where** 키워드를 사용하지 않는 'WinRM' 이름의 서비스만 반환합니다.

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -가장

사용할 가장 수준을 지정합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 0: 기본값 기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다. 기본값은 일반적으로 **Impersonate** 로 설정 됩니다.
- 1: 익명. 호출자의 자격 증명을 숨깁니다.
- 2:를 식별 합니다. 개체가 호출자의 자격 증명을 쿼리할 수 있습니다.
- 3: Impersonate 개체가 호출자의 자격 증명을 사용할 수 있습니다.
- 4: 대리자. 개체가 다른 개체가 호출자의 자격 증명을 사용하도록 허용할 수 있습니다.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -목록

**Namespace** 매개 변수로 지정된 WMI 리포지토리 네임 스페이스의 WMI 클래스의 이름을 가져옵니다.

**List** 매개 변수를 지정 하 고 **Namespace** 매개 변수는 지정 하지 않으면는 `Get-WmiObject` 기본적으로 **Root\Cimv2** 네임 스페이스를 사용 합니다. 이 cmdlet은 레지스트리 키의 **기본 네임 스페이스** 레지스트리 항목을 사용 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` 하 여 기본 네임 스페이스를 결정 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Locale

WMI 개체의 기본 설정 로캘을 지정합니다.
MS_\<LCID\> 형식으로 값을 입력합니다.

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

### -Namespace

**Class** 매개 변수와 함께 사용하는 경우 **Namespace** 매개 변수가 지정된 WMI 클래스가 있는 리포지토리 네임스페이스를 지정합니다. **List** 매개 변수와 함께 사용하는 경우 이 매개 변수는 WMI 클래스 정보를 수집할 네임스페이스를 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

이 cmdlet이 정보를 가져오는 WMI 클래스 속성을 지정 합니다. 속성 이름을 입력합니다.

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

지정된 WQL(WMI Query Language) 문을 실행합니다. 이 매개 변수는 이벤트 쿼리를 지원하지 않습니다.

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -재귀

**Class** 매개 변수로 지정된 클래스 이름의 현재 네임스페이스 및 기타 모든 네임스페이스를 검색합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

동시에 실행할 수 있는 최대 WMI 작업의 수를 지정합니다. 이 매개 변수는 **AsJob** 매개 변수가 명령에 사용 되는 경우에만 유효 합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

입력을로 파이프 할 수 없습니다 `Get-WmiObject` .

## 출력

### PSObject 또는 System.web. Remorerejob

**AsJob** 매개 변수를 사용하는 경우 이 cmdlet 에서 작업 개체를 반환합니다. 그렇지 않으면를 반환 하는 개체는 `Get-WmiObject` **클래스** 매개 변수의 값에 따라 달라 집니다.

## 참고

원격 컴퓨터의 WMI 정보에 액세스하려면 해당 컴퓨터의 로컬 관리자 그룹의 구성원인 계정으로 cmdlet을 실행해야 합니다. 또는 다른 계정에 대한 액세스 권한을 제공하기 위해 원격 리포지토리의 WMI 네임스페이스에 대한 기본 액세스 제어를 변경할 수 있습니다.

기본적으로 각 WMI 클래스의 일부 속성만 표시됩니다. 각 WMI 클래스에 대해 표시되는 속성 집합은 Types.ps1xml 구성 파일에 지정됩니다. WMI 개체의 모든 속성을 가져오려면 또는 cmdlet을 사용 `Get-Member` `Format-List` 합니다.

## 관련 링크

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
