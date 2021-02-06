---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602225"
---
# Stop-Computer

## 개요
로컬 및 원격 컴퓨터를 중지(종료)합니다.

## SYNTAX

### 모두

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Stop-Computer`Cmdlet은 로컬 컴퓨터와 원격 컴퓨터를 종료 합니다.

의 매개 변수를 사용 `Stop-Computer` 하 여 인증 수준 및 대체 자격 증명을 지정 하 고 강제로 즉시 종료할 수 있습니다.

PowerShell 7.1에서 `Stop-Computer` Linux 및 macOS에 대해이 (가) 추가 되었습니다. 매개 변수는 이러한 플랫폼에 영향을 주지 않습니다. 이 cmdlet은 네이티브 명령만 호출 하는 것입니다 `/sbin/shutdown` .

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

백그라운드 연산자는 `&` `Stop-Computer` 명령을 백그라운드 작업으로 실행 합니다. 자세한 내용은 [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)를 참조 하세요.

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 개의 원격 컴퓨터를 지정 합니다. `&`백그라운드 연산자는 명령을 백그라운드 작업으로 실행 합니다. 작업 개체는 변수에 저장 됩니다 `$j` .

변수의 작업 개체는 `$j` 파이프라인에서로 전송 되 고 `Receive-Job` 작업 결과를 가져옵니다. 개체는 변수에 저장 됩니다 `$results` . `$results`변수는 PowerShell 콘솔의 작업 정보를 표시 합니다.

### 예 4: 원격 컴퓨터 종료

이 예제에서는 지정 된 인증을 사용 하 여 원격 컴퓨터를 종료 합니다.

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다. **WsmanAuthentication** 매개 변수는 Kerberos를 사용 하 여 원격 연결을 설정 하도록 지정 합니다.

### 예 5: 도메인의 컴퓨터 종료

이 예에서 명령은 지정 된 도메인에 있는 모든 컴퓨터를 강제로 즉시 종료 합니다.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

`Get-Content`**Path** 매개 변수를 사용 하 여 현재 디렉터리에서 도메인 컴퓨터의 목록으로 파일을 가져옵니다. 개체는 변수에 저장 됩니다 `$s` .

`Get-Credential`**Credential** 매개 변수를 사용 하 여 도메인 관리자의 자격 증명을 지정 합니다. 자격 증명은 변수에 저장 됩니다 `$c` .

`Stop-Computer` 컴퓨터의 **ComputerName** 매개 변수 목록에서 변수에 지정 된 컴퓨터를 종료 `$s` 합니다. **Force** 매개 변수는 강제로 즉시 종료 됩니다. **Credential** 매개 변수는 변수에 저장 된 자격 증명을 제출 합니다 `$c` .

## PARAMETERS

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

### 없음

## 참고

이 cmdlet은 **Win32_OperatingSystem** WMI 클래스의 **Win32Shutdown** 메서드를 사용 합니다. 이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.

PowerShell 7.1에서 `Stop-Computer` Linux 및 macOS에 대해이 (가) 추가 되었습니다. 이러한 다룹니다 cmdlet은 네이티브 명령을 호출 합니다 `/sbin/shutdown` .

## 관련 링크

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Test-Connection](Test-Connection.md)

