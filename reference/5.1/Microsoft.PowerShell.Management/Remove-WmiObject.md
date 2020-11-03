---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214545"
---
# Remove-WmiObject

## 개요
기존 WMI(Windows Management Instrumentation) 클래스의 인스턴스를 삭제합니다.

## SYNTAX

### 클래스 (기본값)

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### path

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Query

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### list

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명
**Get-wmiobject** cmdlet은 기존 WMI(WINDOWS MANAGEMENT INSTRUMENTATION) (WMI) 클래스의 인스턴스를 삭제 합니다.

## 예제

### 예제 1: Win32 프로세스의 모든 인스턴스 닫기

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

이 예에서는 Notepad.exe의 모든 인스턴스를 닫습니다.

첫 번째 명령은 메모장의 인스턴스를 시작합니다.

두 번째 명령은 Get-WmiObject cmdlet을 사용 하 여 Notepad.exe에 해당 하는 Win32_Process 인스턴스를 검색 한 다음 $np 변수에 저장 합니다.

세 번째 명령은 $np 변수의 개체를 **get-wmiobject** 에 전달 하 여 Notepad.exe의 모든 인스턴스를 삭제 합니다.

### 예 2: 폴더 삭제

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

이 명령은 C:\Test 폴더를 삭제 합니다.

첫 번째 명령은 **get-wmiobject** 를 사용 하 여 C:\Test 폴더를 쿼리 한 다음 개체를 $a 변수에 저장 합니다.

두 번째 명령은 $a 변수를 **get-wmiobject** 로 파이프 하 여 폴더를 삭제 합니다.

## PARAMETERS

### -AsJob
이 cmdlet이 백그라운드 작업으로 실행 됨을 나타냅니다.
이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.

Windows PowerShell 3.0에 도입된 새 CIM cmdlet은 WMI cmdlet과 동일한 작업을 수행합니다.
CIM cmdlet은 WSMan (WS-Management) 표준과 Windows 운영 체제를 실행 하는 컴퓨터 및 다른 운영 체제를 실행 하는 컴퓨터를 관리 하는 데 동일한 기술을 사용할 수 있도록 하는 CIM (CIM(Common Information Model)) 표준을 준수 합니다.
**Get-wmiobject** 를 사용 하는 대신 ciminstance 개체로 cmdlet을 사용 하는 것이 좋습니다 https://go.microsoft.com/fwlink/?LinkId=227964 .

*AsJob* 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시합니다.
작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.
**Get-wmiobject** 가 원격 컴퓨터에 대해 사용 되는 경우 작업은 로컬 컴퓨터에 만들어지고 원격 컴퓨터의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다.
작업을 관리 하려면 **job** 명사 ( **job** cmdlet)를 포함 하는 cmdlet을 사용 합니다.
작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.

원격 컴퓨터에이 매개 변수를 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.
관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.
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
WMI 연결에 사용할 인증 수준을 지정합니다.
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
이 cmdlet이 삭제 하는 WMI 클래스의 이름을 지정 합니다.

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
이 매개 변수를 사용하면 다른 모든 매개 변수가 무시됩니다.

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
*로캘* 매개 변수는 기본 순서로 MS_ 형식의 배열로 지정 됩니다 \<LCID\> .

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
WMI 클래스의 WMI 개체 경로 또는 삭제할 WMI 클래스 인스턴스의 WMI 개체 경로를 지정합니다.

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

### System.object 개체
관리 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음, System.web. Remorerejob
*AsJob* 매개 변수를 지정 하는 경우이 cmdlet은 작업 개체를 반환 합니다.
그러지 않으면 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Set-WmiInstance](Set-WmiInstance.md)
