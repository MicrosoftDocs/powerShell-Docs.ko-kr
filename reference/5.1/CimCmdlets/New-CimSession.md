---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 04d0b272995538e88fff2725eb8806c66d217460
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "93219610"
---
# New-CimSession

## 개요

CIM 세션을 만듭니다.

## SYNTAX

### CredentialParameterSet (기본값)

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### CertificatePrameterSet

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## 설명

`New-CimSession`Cmdlet은 CIM 세션을 만듭니다. CIM 세션은 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 연결을 나타내는 클라이언트 쪽 개체입니다. CIM 세션에는 **컴퓨터 이름** , 사용 된 프로토콜 또는 다양 한 식별자와 같은 연결에 대 한 정보가 포함 됩니다.

이 cmdlet은 다른 모든 CIM cmdlet에서 사용할 수 있는 CIM 세션 개체를 반환 합니다.

## 예제

### 예 1: 기본 옵션을 사용 하 여 CIM 세션 만들기

이 예에서는 기본 옵션을 사용 하 여 로컬 CIM 세션을 만듭니다. **ComputerName** 을 지정 하지 않으면에서 `New-CimSession` 로컬 컴퓨터에 대 한 DCOM 세션을 만듭니다.

```powershell
New-CimSession
```

### 예 2: 특정 컴퓨터에 대 한 CIM 세션 만들기

이 예제에서는 **ComputerName** 으로 지정 된 컴퓨터에 대 한 CIM 세션을 만듭니다.
기본적으로는 `New-CimSession` **ComputerName** 을 지정할 때 WSMan 세션을 만듭니다.

```powershell
New-CimSession -ComputerName Server01
```

### 예제 3: 여러 컴퓨터에 대 한 CIM 세션 만들기

이 예에서는 쉼표로 구분 된 목록에서 **ComputerName** 으로 지정 된 각 컴퓨터에 대 한 CIM 세션을 만듭니다.

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### 예제 4: 친숙 한 이름으로 CIM 세션 만들기

이 예에서는 쉼표로 구분 된 목록에서 **ComputerName** 으로 지정 된 각 컴퓨터에 대 한 원격 CIM 세션을 만들고 **이름** 을 지정 하 여 새 세션에 이름을 할당 합니다.

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

CIM 세션의 친숙 한 이름을 사용 하 여 다른 CIM cmdlet의 세션 (예: [CimSession)](Get-CimSession.md)을 참조할 수 있습니다.

### 예 5: PSCredential 개체를 사용 하 여 컴퓨터에 대 한 CIM 세션 만들기

이 예제에서는 **자격 증명** 으로 지정 된 **PSCredential** 개체와 **인증** 에 지정 된 인증 유형을 사용 하 여 **ComputerName** 에서 지정 된 컴퓨터에 대 한 CIM 세션을 만듭니다.

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

Cmdlet을 사용 하 여 **PSCredential** 개체를 만들 수 있습니다 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) .

### 예제 6: 특정 포트를 사용 하 여 컴퓨터에 대 한 CIM 세션 만들기

이 예제에서는 **포트** 에 지정 된 TCP 포트를 사용 하 여 **ComputerName** 에서 지정 된 컴퓨터에 대 한 CIM 세션을 만듭니다.

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### 예 7: DCOM을 사용 하 여 CIM 세션 만들기

이 예에서는 WSMan 대신 DCOM (Distributed COM) 프로토콜을 사용 하 여 CIM 세션을 만듭니다.

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## PARAMETERS

### -인증

사용자의 자격 증명에 사용 되는 인증 유형을 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- 다이제스트
- Negotiate
- Basic
- Kerberos
- NtlmDomain
- CredSsp

**NtlmDomain** 인증 유형을 사용 하 여 로컬 컴퓨터에 연결할 수 없습니다. **CredSSP** 인증은 windows Vista, windows Server 2008 및 이후 버전의 windows 에서만 사용할 수 있습니다.

> [!CAUTION]
> CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 경우와 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateThumbprint

이 작업을 수행할 수 있는 권한이 있는 사용자 계정의 디지털 공개 키 인증서 (x.509)를 지정 합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) PowerShell 인증서 공급자에서 또는 cmdlet을 사용 합니다.

자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: CertificatePrameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

CIM 세션을 만들 컴퓨터의 이름을 지정 합니다. 단일 컴퓨터 이름 또는 쉼표로 구분 된 여러 컴퓨터 이름을 지정 합니다.

**ComputerName** 을 지정 하지 않으면 로컬 컴퓨터에 대 한 CIM 세션이 만들어집니다. 다음 형식 중 하나로 컴퓨터 이름에 대 한 값을 지정할 수 있습니다.

- 하나 이상의 NetBIOS 이름
- 하나 이상의 IP 주소
- 하나 이상의 정규화 된 도메인 이름입니다.

컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화 된 도메인 이름을 지정 해야 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. **자격 증명** 을 지정 하지 않으면 현재 사용자 계정이 사용 됩니다.

다음 형식 중 하나를 사용 하 여 **자격 증명** 의 값을 지정 합니다.

- 사용자 이름: "User01"
- 도메인 이름 및 사용자 이름: "Domain01\User01"
- 사용자 계정 이름: " User@Domain.com "
- Cmdlet에서 반환 된 개체와 같은 PSCredential 개체 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 입니다.

사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

CIM 세션의 이름을 지정 합니다.

Cmdlet과 같은 다른 cmdlet을 사용 하는 경우 이름을 사용 하 여 CIM 세션을 참조할 수 있습니다 [`Get-CimSession`](Get-CimSession.md) .
이 이름은 컴퓨터나 현재 세션에서 고유하지 않아도 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Cmdlet이 서버의 응답을 대기 하는 기간입니다.

기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.

**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

이 명령에 사용되는 원격 컴퓨터의 네트워크 포트를 지정합니다.
원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.
기본 포트는 5985(HTTP용 WinRM 포트) 및 5986(HTTPS용 WinRM 포트)입니다.

대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.
다음 명령을 사용하여 수신기를 구성합니다.

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요. 명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SessionOption

새 CIM 세션의 고급 옵션을 설정 합니다. Cmdlet을 사용 하 여 만든 **CimSessionOption** 개체의 이름을 입력 합니다 [`New-CimSessionOption`](New-CimSessionOption.md) .

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipTestConnection

기본적으로 cmdlet은 원격 `New-CimSession` 서버가 **port** 매개 변수를 사용 하 여 지정 된 포트 번호에서 수신 대기 하 고 있는지 확인 하 고 지정 된 계정 자격 증명을 확인 하는 두 가지 이유로 원격 WS-Management 끝점과의 연결을 설정 합니다. 확인은 표준 WS-Identity 작업을 사용 하 여 수행 됩니다. 원격 WS-Management 끝점에서 WS-Id를 사용할 수 없는 경우 또는 일부 데이터 전송 시간을 줄이기 위해 **Skiptestconnection** 스위치 매개 변수를 추가할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet은 입력을 허용 하지 않습니다.

## 출력

### Microsoft.Management.Infrastructure.CimSession

## 참고

## 관련 링크

[Get-ChildItem](../Microsoft.Powershell.Management/Get-ChildItem.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-Item](../Microsoft.Powershell.Management/Get-Item.md)

[Get-CimSession](Get-CimSession.md)

[Remove-CimSession](Remove-CimSession.md)

[New-CimSessionOption](New-CimSessionOption.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
