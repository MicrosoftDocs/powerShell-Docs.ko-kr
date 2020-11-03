---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: e2d4f321609a386c6795949a4a706323b4889f69
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216105"
---
# Rename-Computer

## 개요
컴퓨터를 이름을 바꿉니다.

## SYNTAX

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Rename-Computer`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 이름을 바꿉니다.
각 명령에서 컴퓨터 이름을 하나씩 바꿉니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 로컬 컴퓨터 이름 바꾸기

이 명령은 로컬 컴퓨터의 이름을 `Server044` 바꾼 후 다시 시작 하 여 변경 내용을 적용 합니다.

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### 예 2: 원격 컴퓨터 이름 바꾸기

이 명령은 컴퓨터의 이름을 `Srv01` 로 바꿉니다 `Server001` . 컴퓨터를 다시 시작 하지 않습니다.

**DomainCredential** 매개 변수는 도메인에 있는 컴퓨터의 이름을 바꿀 수 있는 권한을 가진 사용자의 자격 증명을 지정 합니다.

**Force** 매개 변수는 확인 메시지를 표시 하지 않습니다.

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## PARAMETERS

### -ComputerName

지정된 원격 컴퓨터를 이름을 바꿉니다.
기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.
로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ) 또는을 입력 합니다 `localhost` .

이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.
**ComputerName** `Rename-Computer` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DomainCredential

도메인에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다.
도메인에 가입된 컴퓨터의 이름을 바꾸려면 명시적 자격 증명이 필요합니다.

또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

**ComputerName** 매개 변수로 지정된 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.

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

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### -LocalCredential

**ComputerName** 매개 변수로 지정된 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

도메인에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **DomainCredential** 매개 변수를 사용합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewName

컴퓨터의 새 이름을 지정합니다.
이 매개 변수는 필수적 요소입니다.

표준 이름에는 문자 ( `a-z` ), ( `A-Z` ), 숫자 ( `0-9` ) 및 하이픈 ()이 포함 될 수 `-` 있지만 공백 또는 마침표 ()는 포함 되지 않습니다 `.` . 이름은 숫자로만 구성 될 수 없으며 63 자 보다 길 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

명령의 결과를 반환합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

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

### -Restart

이 cmdlet은 이름이 바뀐 컴퓨터를 다시 시작 함을 나타냅니다.
변경 내용을 적용하려면 컴퓨터를 자주 다시 시작해야 합니다.

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

이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- **기본**
- **CredSSP**
- **기본값**
- **다이제스트**
- **Kerberos**
- **결정할**

기본값은 **Default** 입니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.

> [!WARNING]
> 사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.
> 이렇게 하면 원격 작업의 보안 위험이 커집니다.
> 원격 컴퓨터가 손상 된 경우이 컴퓨터로 전달 된 자격 증명을 사용 하 여 네트워크 세션 >을 제어할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet에는 값으로 입력을 사용하는 매개 변수가 없습니다.
그러나 개체의 **ComputerName** 및 **NewName** 속성 값을 이 cmdlet으로 파이프할 수 있습니다.

## 출력

### Microsoft. PowerShell. ComputerChangeInfo

**PassThru** 매개 변수를 지정 하는 경우이 Cmdlet은 **computerchangeinfo** 개체를 반환 합니다.
그러지 않으면 어떠한 출력도 반환되지 않습니다.

## 참고

## 관련 링크

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
