---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218257"
---
# Stop-Computer

## 개요
로컬 및 원격 컴퓨터를 중지(종료)합니다.

## SYNTAX

### 모두

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Stop-Computer`Cmdlet은 로컬 컴퓨터와 원격 컴퓨터를 종료 합니다.

의 매개 변수를 사용 하 여 `Stop-Computer` 종료 작업을 백그라운드 작업으로 실행 하 고, 인증 수준 및 대체 자격 증명을 지정 하 고, 명령을 실행 하기 위해 만들어지는 동시 연결을 제한 하 고, 강제로 즉시 종료할 수 있습니다.

**AsJob** 매개 변수를 사용 하지 않으면이 Cmdlet은 PowerShell 원격을 요구 하지 않습니다.

## 예제

### 예 1: 로컬 컴퓨터 종료

이 예제에서는 로컬 컴퓨터를 종료 합니다.

```powershell
Stop-Computer -ComputerName localhost
```

### 예 2: 원격 컴퓨터와 로컬 컴퓨터를 종료 합니다.

이 예제에서는 두 원격 컴퓨터와 로컬 컴퓨터를 중지 합니다.

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 원격 컴퓨터와 로컬 컴퓨터를 지정 합니다. 각 컴퓨터는 종료 됩니다.

### 예 3: 원격 컴퓨터를 백그라운드 작업으로 종료

이 예제에서는 `Stop-Computer` 두 원격 컴퓨터에서 백그라운드 작업으로 실행 됩니다.

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 개의 원격 컴퓨터를 지정 합니다. **AsJob** 매개 변수는 명령을 백그라운드 작업으로 실행 합니다. 작업 개체는 변수에 저장 됩니다 `$j` .

변수의 작업 개체는 `$j` 파이프라인에서로 전송 되 고 `Receive-Job` 작업 결과를 가져옵니다. 개체는 변수에 저장 됩니다 `$results` . `$results`변수는 PowerShell 콘솔의 작업 정보를 표시 합니다.

**AsJob** 은 로컬 컴퓨터에 작업을 만들고 결과를 로컬 컴퓨터에 자동으로 반환 하기 때문에 로컬 명령으로를 실행할 수 있습니다 `Receive-Job` .

### 예 4: 원격 컴퓨터 종료

이 예제에서는 지정 된 인증을 사용 하 여 원격 컴퓨터를 종료 합니다.

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다. **가장** 매개 변수는 사용자 지정 된 가장을 지정 하 고 **DcomAuthentication** 매개 변수는 인증 수준 설정을 지정 합니다.

### 예 5: 도메인의 컴퓨터 종료

이 예에서 명령은 지정 된 도메인에 있는 모든 컴퓨터를 강제로 즉시 종료 합니다.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

`Get-Content`**Path** 매개 변수를 사용 하 여 현재 디렉터리에서 도메인 컴퓨터의 목록으로 파일을 가져옵니다. 개체는 변수에 저장 됩니다 `$s` .

`Get-Credential`**Credential** 매개 변수를 사용 하 여 도메인 관리자의 자격 증명을 지정 합니다. 자격 증명은 변수에 저장 됩니다 `$c` .

`Stop-Computer` 컴퓨터의 **ComputerName** 매개 변수 목록에서 변수에 지정 된 컴퓨터를 종료 `$s` 합니다. **Force** 매개 변수는 강제로 즉시 종료 됩니다. **ThrottleLimit** 매개 변수는 명령을 10 개의 동시 연결로 제한 합니다. **Credential** 매개 변수는 변수에 저장 된 자격 증명을 제출 합니다 `$c` .

## PARAMETERS

### -AsJob

이 cmdlet이 백그라운드 작업으로 실행 됨을 나타냅니다.

이 매개 변수를 사용 하려면 원격을 사용 하도록 로컬 및 원격 컴퓨터를 구성 해야 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다. 자세한 내용은 [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md)을 참조하세요.

**AsJob** 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환 합니다. 작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다. AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다. 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) 및 [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

중지할 컴퓨터를 지정 합니다. 기본값은 로컬 컴퓨터입니다.

하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름 또는 localhost를 입력 합니다.

이 매개 변수는 PowerShell 원격을 사용 하지 않습니다. 컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### -Credential

이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

이 cmdlet이 WMI와 함께 사용 하는 인증 수준을 지정 합니다. `Stop-Computer` WMI를 사용 합니다. 기본값은 **Packet** 입니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- **기본값** : Windows 인증.
- **None** : COM 인증을 수행 하지 않습니다.
- **연결** : 연결 수준 COM 인증입니다.
- **호출** : 호출 수준 COM 인증입니다.
- **패킷** : 패킷 수준 COM 인증입니다.
- **PacketIntegrity** : 패킷 무결성 수준 COM 인증입니다.
- **PacketPrivacy** : 패킷 개인 정보 수준 COM 인증입니다.
- **변경 되지 않음** : 이전 명령과 동일 합니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationlevel](/dotnet/api/system.management.authenticationlevel)을 참조 하세요.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

컴퓨터를 강제로 즉시 종료 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -가장

이 cmdlet이 WMI를 호출할 때 사용할 가장 수준을 지정 합니다. 기본값은 **Impersonate** 입니다.

`Stop-Computer` WMI를 사용 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- **기본값** : 기본 가장.
- **Anonymous** : 호출자의 id를 숨깁니다.
- **식별** : 개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용 합니다.
- **Impersonate** : 개체가 호출자의 자격 증명을 사용할 수 있습니다.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

컴퓨터를 다시 시작하는 데 사용할 프로토콜을 지정합니다. 이 매개 변수에 허용 되는 값은 **WSMan** 및 **DCOM** 입니다. 기본값은 **DCOM** 입니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.

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

### -WsmanAuthentication

이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다. 기본값은 **Default** 입니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- Basic
- CredSSP
- 기본값
- 다이제스트
- Kerberos
- Negotiate

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.

> [!CAUTION]
> 사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

이 cmdlet에는 입력을 파이프 할 수 없습니다.

## 출력

### 없음 또는 System.web. Remorerereor 작업

**AsJob** 매개 변수를 지정 하는 경우이 Cmdlet은 **system.object** 를 반환 합니다. 그렇지 않으면 출력을 생성 하지 않습니다.

## 참고

이 cmdlet은 **Win32_OperatingSystem** WMI 클래스의 **Win32Shutdown** 메서드를 사용 합니다. 이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.

## 관련 링크

[Add-Computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Test-Connection](Test-Connection.md)
