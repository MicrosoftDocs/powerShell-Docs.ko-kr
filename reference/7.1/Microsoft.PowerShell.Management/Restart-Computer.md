---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 1912df403e3204be623a8c15c04b528c705169e1
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218314"
---
# Restart-Computer

## 개요
로컬 및 원격 컴퓨터에서 운영 체제를 다시 시작 합니다.

## SYNTAX

### DefaultSet (기본값)

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Restart-Computer`Cmdlet은 로컬 및 원격 컴퓨터에서 운영 체제를 다시 시작 합니다.

의 매개 변수를 사용 하 여 `Restart-Computer` 다시 시작 작업을 실행 하 고, 인증 수준 및 대체 자격 증명을 지정 하 고, 동시에 실행 되는 작업을 제한 하 고, 강제로 즉시 다시 시작할 수 있습니다.

Windows PowerShell 3.0부터 다음 명령을 실행 하기 전에 다시 시작이 완료 될 때까지 기다릴 수 있습니다. 대기 시간 제한 및 쿼리 간격을 지정 하 고, 다시 시작 된 컴퓨터에서 특정 서비스를 사용할 수 있을 때까지 기다립니다. 이 기능을 사용 하면 `Restart-Computer` 스크립트 및 함수에서 효과적으로 사용할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터 다시 시작

`Restart-Computer` 로컬 컴퓨터를 다시 시작 합니다.

```powershell
Restart-Computer
```

### 예 2: 여러 컴퓨터 다시 시작

`Restart-Computer` 원격 컴퓨터와 로컬 컴퓨터를 다시 시작할 수 있습니다. **ComputerName** 매개 변수는 컴퓨터 이름 배열을 허용 합니다.

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### 예제 3: 텍스트 파일에서 컴퓨터 이름 가져오기

`Restart-Computer` 텍스트 파일에서 컴퓨터 이름 목록을 가져오고 컴퓨터를 다시 시작 합니다. **ComputerName** 매개 변수가 지정 되지 않았습니다. 하지만이 매개 변수는 첫 번째 위치 매개 변수 이기 때문에 파이프라인으로 전송 되는 텍스트 파일의 컴퓨터 이름을 허용 합니다.

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

`Get-Content` 는 **Path** 매개 변수를 사용 하 여 텍스트 파일에서 컴퓨터 이름 목록을 가져올 **Domain01.txt** 합니다. 컴퓨터 이름이 파이프라인으로 전송 됩니다. `Restart-Computer` 각 컴퓨터를 다시 시작 합니다.

### 예제 4: 텍스트 파일에 나열 된 컴퓨터를 강제로 다시 시작

이 예제에서는 파일에 나열 된 컴퓨터를 강제로 즉시 다시 시작 `Domain01.txt` 합니다. 텍스트 파일의 컴퓨터 이름은 변수에 저장 됩니다. **Force** 매개 변수는 강제로 즉시 다시 시작 합니다.

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

`Get-Content` 는 **Path** 매개 변수를 사용 하 여 텍스트 파일에서 컴퓨터 이름 목록을 가져올 **Domain01.txt** 합니다. 컴퓨터 이름은 변수에 저장 됩니다 `$Names` . `Get-Credential` 사용자 이름과 암호를 묻는 메시지를 표시 하 고 해당 값을 변수에 저장 `$Creds` 합니다. `Restart-Computer` 는 해당 변수와 함께 **ComputerName** 및 **Credential** 매개 변수를 사용 합니다. **Force** 매개 변수를 설정 하면 각 컴퓨터를 즉시 다시 시작 합니다.

### 예 6: 원격 컴퓨터를 다시 시작 하 고 PowerShell 대기

`Restart-Computer` 는 원격 컴퓨터를 다시 시작 하 고, 계속 하기 전에 다시 시작 된 컴퓨터에서 PowerShell을 사용할 수 있게 될 때까지 최대 5 분 (300 초) 동안 대기 합니다.

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 **Server01** 를 지정 합니다. **Wait** 매개 변수는 다시 시작이 완료 될 때까지 기다립니다. **의** 은 PowerShell에서 원격 컴퓨터의 명령을 실행할 수 있도록 지정 합니다. **Timeout** 매개 변수는 5 분 대기를 지정 합니다. **Delay** 매개 변수는 2 초 마다 원격 컴퓨터를 쿼리하여 다시 시작할지 여부를 확인 합니다.

### 예 7: WsmanAuthentication를 사용 하 여 컴퓨터 다시 시작

`Restart-Computer`**WsmanAuthentication** 메커니즘을 사용 하 여 원격 컴퓨터를 다시 시작 합니다.
Kerberos 인증 현재 사용자에 게 원격 컴퓨터를 다시 시작할 수 있는 권한이 있는지 여부를 확인 합니다. 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터 **Server01** 를 지정 합니다.
**WsmanAuthentication** 매개 변수는 인증 방법을 **Kerberos** 로 지정 합니다.

## PARAMETERS

### -ComputerName

컴퓨터 이름 하나 또는 쉼표로 구분 된 컴퓨터 이름 배열을 지정 합니다. `Restart-Computer` 파이프라인 또는 변수의 **ComputerName** 개체를 허용 합니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 또는 localhost를 입력 합니다 `.` .

이 매개 변수는 PowerShell 원격을 사용 하지 않습니다. 컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

**ComputerName** 매개 변수를 지정 하지 않으면에서 `Restart-Computer` 로컬 컴퓨터를 다시 시작 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### -Delay

쿼리의 빈도 (초)를 지정 합니다. PowerShell은 **For** 매개 변수로 지정 된 서비스를 쿼리하여 컴퓨터를 다시 시작한 후 서비스를 사용할 수 있는지 여부를 확인 합니다.

이 매개 변수는 **Wait** 및 **For** 매개 변수와 함께 사용할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

**Delay** 매개 변수를 지정 하지 않으면에서 `Restart-Computer` 5 초 지연 시간을 사용 합니다.

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -의 경우

컴퓨터를 다시 시작한 후 지정 된 서비스 또는 기능을 사용할 수 있을 때까지 기다리는 PowerShell의 동작을 지정 합니다. 이 매개 변수는 **Wait** 매개 변수에만 사용할 수 있습니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- **기본값** : PowerShell이 다시 시작 될 때까지 대기 합니다.
- **Powershell** : 컴퓨터의 powershell 원격 세션에서 명령을 실행할 수 있습니다.
- **WMI** : 컴퓨터에 대 한 Win32_ComputerSystem 쿼리에 대 한 응답을 받습니다.
- **WinRM** : ws-management를 사용 하 여 컴퓨터에 대 한 원격 세션을 설정할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

컴퓨터를 강제로 즉시 다시 시작 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -시간 제한

대기 기간(초)을 지정합니다. 시간이 경과할 때 컴퓨터를 `Restart-Computer` 다시 시작 하지 않아도 명령 프롬프트로 돌아갑니다.

**Timeout** 매개 변수는 **Wait** 매개 변수에만 사용할 수 있습니다. **Timeout** 은 **대기** 매개 변수의 무한 대기 기간을 재정의 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

`Restart-Computer` PowerShell 프롬프트를 표시 하지 않고 컴퓨터가 다시 시작 될 때까지 파이프라인을 차단 합니다. 스크립트에서이 매개 변수를 사용 하 여 컴퓨터를 다시 시작한 다음 다시 시작이 완료 되 면 계속 처리할 수 있습니다.

**Wait** 매개 변수는 컴퓨터를 다시 시작할 때까지 무기한 대기 합니다. **시간 제한** 을 사용 하 여 타이밍을 조정 하 고 **For** 및 **Delay** 매개 변수를 사용 하 여 다시 시작 된 컴퓨터에서 특정 서비스를 사용할 수 있을 때까지 기다릴 수 있습니다.

로컬 컴퓨터를 다시 시작 하는 경우에는 **Wait** 매개 변수가 유효 하지 않습니다. **ComputerName** 매개 변수 값에 원격 컴퓨터와 로컬 컴퓨터의 이름이 포함 된 경우에서 `Restart-Computer` 로컬 컴퓨터의 **대기** 에 대 한 종료 되지 않는 오류를 생성 하지만 원격 컴퓨터를 다시 시작할 때까지 기다립니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -WsmanAuthentication

사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다. 이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

이 매개 변수에 허용 되는 값은 **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** 및 **Negotiate** 입니다.

자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.

> [!WARNING]
> 사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

실행 하기 전에 확인 메시지를 표시 `Restart-Computer` 합니다.

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

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Restart-Computer` . `Restart-Computer`Cmdlet이 실행 되지 않습니다.

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

### System.String

`Restart-Computer` 파이프라인 또는 변수의 컴퓨터 이름을 허용 합니다.

## 출력

### 없음

`Restart-Computer` 는 출력을 생성 하지 않습니다.

## 참고

- Windows에서는 `Restart-Computer` WMI(Windows Management Instrumentation) (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) 클래스의 [Win32Shutdown 메서드](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) 를 사용 합니다. 이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.
- Linux 및 Mac OS에서는 `Restart-Computer` `/sbin/shutdown` bash 도구를 사용 합니다.

## 관련 링크

[Windows 원격 관리 정보](/windows/desktop/WinRM/about-windows-remote-management)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[WS-Management 프로토콜](/windows/desktop/WinRM/ws-management-protocol)
