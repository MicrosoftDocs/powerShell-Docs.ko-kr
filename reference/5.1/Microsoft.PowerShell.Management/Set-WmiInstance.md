---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214410"
---
# Set-WmiInstance

## 개요
기존 WMI(Windows Management Instrumentation) 클래스의 인스턴스를 만들거나 업데이트합니다.

## SYNTAX

### 클래스 (기본값)

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Query

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
`Set-WmiInstance`Cmdlet은 기존 WMI(Windows Management Instrumentation) (WMI) 클래스의 인스턴스를 만들거나 업데이트 합니다.
만들거나 업데이트한 인스턴스는 WMI 리포지토리에 기록됩니다.

Windows PowerShell 3.0에 도입된 새 CIM cmdlet은 WMI cmdlet과 동일한 작업을 수행합니다.
CIM cmdlet은 WSMan (WS-Management) 표준과 CIM(Common Information Model) (CIM) 표준을 준수 합니다.
이렇게 하면 cmdlet이 동일한 기술을 사용 하 여 Windows 기반 컴퓨터 및 다른 운영 체제를 실행 하는 컴퓨터를 관리할 수 있습니다.
를 사용 하는 대신 `Set-WmiInstance` [Ciminstance 개체로](/powershell/module/cimcmdlets/set-ciminstance) 또는 [ciminstance 개체로](/powershell/module/cimcmdlets/new-ciminstance) cmdlet을 사용 하는 것이 좋습니다.

## 예제

### 예제 1: WMI 로깅 수준 설정

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

이 명령은 WMI 로깅 수준을 2로 설정합니다.
이 명령은 인수 매개 변수에 설정 된 속성 및 값 쌍으로 간주 되는 값을 전달 합니다.
매개 변수는 @{property = value} 생성으로 정의된 해시 테이블을 사용합니다.
반환된 클래스 정보에는 새 값이 반영됩니다.

### 예제 2: 환경 변수 및 해당 값 만들기

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

이 명령은 testvar 값을 가진 testvar 환경 변수를 만듭니다.
**Win32_Environment** WMI 클래스의 새 인스턴스를 만들어이를 수행 합니다.
이 작업을 수행 하려면 적절 한 자격 증명이 필요 하며 새 환경 변수를 보기 위해 Windows PowerShell을 다시 시작 해야 할 수 있습니다.

### 예 3: 여러 원격 컴퓨터에 대 한 WMI 로깅 수준 설정

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

이 명령은 WMI 로깅 수준을 2로 설정합니다.
이 명령은 인수 매개 변수에 설정 된 속성 및 값 쌍으로 간주 되는 값을 전달 합니다.
매개 변수는 @{property = value} 생성으로 정의된 해시 테이블을 사용합니다.
반환된 클래스 정보에는 새 값이 반영됩니다.

## PARAMETERS

### -Arguments
변경할 속성 이름과 해당 속성의 새 값을 지정합니다.
이름 및 값은 이름-값 쌍 이어야 합니다.
이름-값 쌍은 명령줄에서 해시 테이블로 전달 됩니다.
다음은 그 예입니다. 

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
이 cmdket 백그라운드 작업으로 실행 됨을 나타냅니다.
이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.

*AsJob* 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다.
작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.
원격 컴퓨터에 대해 **set-wmiinstance** 를 사용 하는 경우에는 로컬 컴퓨터에 작업이 생성 되 고 원격 컴퓨터의 결과가 로컬 컴퓨터에 자동으로 반환 됩니다.
작업을 관리 하려면 **job** 명사 ( **job** cmdlet)를 포함 하는 cmdlet을 사용 합니다.
작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.

이 매개 변수를 원격 컴퓨터와 함께 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.
또한 windows Vista 이상 버전의 windows 운영 체제에서 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 해야 합니다.
자세한 내용은 about_Remote_Requirements를 참조하세요.

Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 about_Jobs 및 about_Remote_Jobs를 참조 하세요.

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
WMI 연결에 사용 해야 하는 인증 수준을 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- -1: 변경 되지 않습니다.
- 0: 기본값
- 1: 없음.
인증이 수행 되지 않았습니다.
- 2: 연결
인증은 클라이언트가 응용 프로그램과의 관계를 설정 하는 경우에만 수행 됩니다.
- 3:를 호출 합니다.
응용 프로그램에서 요청을 받으면 각 호출이 시작 될 때만 인증이 수행 됩니다.
- 4: 패킷.
클라이언트에서 수신 된 모든 데이터에 대해 인증이 수행 됩니다.
- 5: PacketIntegrity.
클라이언트와 응용 프로그램 간에 전송 되는 모든 데이터는 인증 되 고 확인 됩니다.
- 6: PacketPrivacy.
다른 인증 수준의 속성을 사용 하 고 모든 데이터를 암호화 합니다.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority
WMI 연결을 인증하는 데 사용할 권한을 지정합니다.
표준 NTLM 또는 Kerberos 인증을 지정할 수 있습니다.
NTLM을 사용하려면 권한 설정을 ntlmdomain:\<DomainName\>으로 설정합니다. 여기서 \<DomainName\>은 유효한 NTLM 도메인 이름을 식별합니다.
Kerberos를 사용 하려면 kerberos를 지정 \<DomainName\> \\ \<ServerName\> 합니다.
로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -클래스
WMI 클래스 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
이 cmdlet이 실행 되는 컴퓨터의 이름을 지정 합니다.
기본값은 로컬 컴퓨터입니다.

하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.
로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.
원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 *ComputerName* 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet에 의해 생성 된 개체)를 입력 합니다.
사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

이 매개 변수는 Windows PowerShell과 함께 설치 된 모든 공급자가 매개 변수와 함께 설치 된 공급자에서 지원 되지 않습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges
이 cmdlet은 WMI 호출을 수행 하기 전에 현재 사용자의 모든 권한을 사용 하도록 설정 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
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

- 0: 기본값
기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다. 일반적으로 3: Impersonate로 설정 됩니다.
- 1: 익명.
호출자의 자격 증명을 숨깁니다.
- 2:를 식별 합니다.
개체가 호출자의 자격 증명을 쿼리할 수 있습니다.
- 3: Impersonate
개체가 호출자의 자격 증명을 사용할 수 있습니다.
- 4: 대리자.
개체가 다른 개체가 호출자의 자격 증명을 사용하도록 허용할 수 있습니다.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
입력으로 사용할 **Managementobject** 개체를 지정 합니다.
이 매개 변수를 사용 하는 경우 *Arguments* 매개 변수를 제외한 다른 모든 매개 변수는 무시 됩니다.

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Locale
WMI 개체의 기본 설정 로캘을 지정합니다.
*로캘* 매개 변수는 MS_ 형식의 배열에서 \<LCID\> 기본 순서로 지정 됩니다.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace
*클래스* 매개 변수와 함께 사용 될 때 참조 된 wmi 클래스가 있는 wmi 리포지토리 네임 스페이스를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
만들거나 업데이트 하려는 인스턴스의 WMI 개체 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PutType
WMI 인스턴스를 만들지 또는 업데이트할지를 나타냅니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- UpdateOnly.
기존 WMI 인스턴스를 업데이트합니다.
- CreateOnly.
새 WMI 인스턴스를 만듭니다.
- UpdateOrCreate.
WMI 인스턴스가 있을 경우 업데이트하고 인스턴스가 없을 경우 새 인스턴스를 만듭니다.

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수는 *AsJob* 매개 변수와 함께 사용 됩니다.
제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

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

### -Confirm
cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet은 입력을 받지 않습니다.

## 출력

### 없음
이 cmdlet은 출력을 생성하지 않습니다.

## 참고

## 관련 링크

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)
