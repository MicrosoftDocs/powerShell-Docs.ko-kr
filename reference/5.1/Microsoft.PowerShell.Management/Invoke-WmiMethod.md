---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93217993"
---
# Invoke-WmiMethod

## 개요
WMI 메서드를 호출합니다.

## SYNTAX

### 클래스 (기본값)

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Query

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Invoke-WmiMethod`Cmdlet은 WMI (WMI(Windows Management Instrumentation)) 개체의 메서드를 호출 합니다.

Windows PowerShell 3.0에 도입 된 새로운 CIM(Common Information Model) (CIM) cmdlet은 WMI cmdlet과 동일한 작업을 수행 합니다. CIM cmdlet은 WSMan (WS-Management) 표준과 CIM 표준을 준수 하 여 cmdlet이 동일한 기술을 사용 하 여 Windows 컴퓨터 및 다른 운영 체제를 실행 하는 운영 체제를 관리할 수 있도록 합니다. 를 사용 하는 대신 `Invoke-WmiMethod` [invoke-cimmethod](../cimcmdlets/invoke-cimmethod.md)를 사용 하는 것이 좋습니다.

## 예제

### 예제 1: WMI 개체의 필수 순서 나열

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

이 명령은 개체의 필요한 순서를 나열합니다. PowerShell 3.0에서의 WMI 호출은 다른 메서드와 다르며, 개체 값을 특정 순서로 입력해야 합니다.

### 예제 2: 응용 프로그램의 인스턴스 시작

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

이 명령은 `Create` **Win32_Process** 클래스의 메서드를 호출 하 여 메모장의 인스턴스를 시작 합니다.

**ReturnValue** 속성은 0으로 채워지고, 명령이 완료 되 면 **ProcessId** 속성이 정수 (다음 프로세스 ID 번호)로 채워집니다.

### 예제 3: 파일 이름 바꾸기

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

이 명령은 파일의 이름을 바꿉니다. **Path** 매개 변수를 사용 하 여 **CIM_DataFile** 클래스의 인스턴스를 참조 합니다. 그다음에 해당 특정 인스턴스에 Rename 메서드를 적용합니다.

명령이 완료 되 면 **ReturnValue** 속성은 0으로 채워집니다.

### 예제 4:를 사용 하 여 값 배열 전달 `-ArgumentList`

개체 배열을 사용 하 `$binSD` 고 그 뒤에 값을 사용 하는 예제 `$null` 입니다.

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## PARAMETERS

### -ArgumentList

호출된 메서드에 전달할 매개 변수를 지정합니다. 이 매개 변수 값은 개체의 배열 이어야 하며, 호출 된 메서드에 필요한 순서로 표시 되어야 합니다. Cmdlet에는 `Invoke-CimCommand` 이러한 제한 사항이 없습니다.

이러한 개체를 나열할 순서를 확인 하려면 `GetMethodParameters()` 이 항목의 끝 부분에 있는 예제 1에 나와 있는 것 처럼 WMI 클래스에서 메서드를 실행 합니다.

> [!IMPORTANT]
> 첫 번째 값이 둘 이상의 요소를 포함하는 배열인 경우 두 번째 값 $null이 필요합니다. 그러지 않으면 명령에서 "'System.Byte' 형식 개체를 'System.Array' 형식으로 캐스팅할 수 없습니다."와 같은 오류가 생성됩니다. 위의 예 4를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다. 이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.

**AsJob** 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시합니다. 작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다. `Invoke-WmiMethod`가 원격 컴퓨터에 대해 사용 되는 경우 작업은 로컬 컴퓨터에 만들어지고 원격 컴퓨터의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다. 작업을 관리하려면 Job 명사(Job cmdlets)가 포함된 cmdlet을 사용합니다. 작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.

원격 컴퓨터에 이 매개 변수를 사용하려면 원격을 사용하도록 로컬 및 원격 컴퓨터를 구성해야 합니다. 또한 windows Vista 이상 버전의 windows에서 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 해야 합니다. 자세한 내용은 about_Remote_Requirements를 참조하세요.

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

WMI 연결에 사용되는 인증 수준을 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

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

WMI 연결을 인증하는 데 사용할 권한을 지정합니다. 표준 Windows NTLM (NT LAN Manager) 또는 Kerberos 인증을 지정할 수 있습니다. NTLM을 사용하려면 권한 설정을 ntlmdomain:\<DomainName\>으로 설정합니다. 여기서 \<DomainName\>은 유효한 NTLM 도메인 이름을 식별합니다. Kerberos를 사용하려면 kerberos:\<DomainName\ServerName\>을 지정합니다. 로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.

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

호출할 정적 메서드를 포함하는 WMI 클래스를 지정합니다.

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

이 cmdlet이 명령을 실행 하는 컴퓨터를 문자열 배열로 지정 합니다. 기본값은 로컬 컴퓨터입니다.

하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다. 원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

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

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다. 사용자 이름 (예:, 또는)을 입력 `User01` `Domain01\User01` `User@Contoso.com` 합니다. 또는 Get-Credential cmdlet에서 반환 된 개체와 같은 **PSCredential** 개체를 입력 합니다. 사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.

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

명령에서 WMI 호출을 수행 하기 전에이 cmdlet이 현재 사용자의 모든 권한을 사용 하도록 설정 함을 나타냅니다.

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

사용할 가장 수준을 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 0: 기본값 (일반적으로 "3: Impersonate"로 설정 되는 기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다.)
- 1: Anonymous (호출자의 자격 증명을 숨깁니다.)
- 2: 식별 (개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용)
- 3: Impersonate (개체가 호출자의 자격 증명을 사용할 수 있도록 허용)
- 4: Delegate (개체가 다른 개체에서 호출자의 자격 증명을 사용할 수 있도록 허용)

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

입력으로 사용할 **Managementobject** 개체를 지정 합니다. 이 매개 변수를 사용 하면 **Flag** 및 **Argument** 매개 변수를 제외한 다른 모든 매개 변수는 무시 됩니다.

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

WMI 개체의 기본 설정 로캘을 지정합니다. **로캘** 매개 변수의 값을 `MS_<LCID>` 원하는 순서로 형식의 배열로 지정 합니다.

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

### -Name

호출할 메서드의 이름을 지정합니다. 이 매개 변수는 필수이며 null이거나 비어 있을 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

**Class** 매개 변수와 함께 사용할 경우이 매개 변수는 참조 된 wmi 클래스 또는 개체가 있는 wmi 리포지토리 네임 스페이스를 지정 합니다.

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

WMI 클래스의 WMI 개체 경로를 지정하거나 WMI 클래스 인스턴스의 WMI 개체 경로를 지정합니다. 지정 하는 클래스나 인스턴스에는 **Name** 매개 변수에 지정 된 메서드가 포함 되어야 합니다.

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

### -ThrottleLimit

동시에 실행할 수 있는 WMI 작업 수에 대 한 제한 값을 지정 합니다.
이 매개 변수는 **AsJob** 매개 변수와 함께 사용 됩니다. 제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

이 cmdlet은 어떠한 입력도 허용하지 않습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

## 관련 링크

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[Get-WmiObject](Get-WmiObject.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)
