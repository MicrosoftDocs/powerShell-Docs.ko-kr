---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 3178c12dbc14b9d0841f1d924a695ae2f761f579
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224738"
---
# Test-WSMan

## 개요
WinRM 서비스가 로컬 컴퓨터에서 실행되고 있는지 또는 원격 컴퓨터에서 실행되고 있는지를 테스트합니다.

## SYNTAX

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## 설명
**WSMan** Cmdlet은 WinRM 서비스가 로컬 컴퓨터에서 실행 되 고 있는지 또는 원격 컴퓨터에서 실행 되 고 있는지를 확인 하는 식별 요청을 제출 합니다.
테스트된 컴퓨터가 이 서비스를 실행하고 있는 경우 이 cmdlet은 테스트된 서비스의 WS-Management ID 스키마, 프로토콜 버전, 제품 공급업체 및 제품 버전을 표시합니다.

## 예제

### 예 1: WinRM 서비스의 상태 확인

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

이 명령은 WinRM 서비스가 로컬 컴퓨터에서 실행되고 있는지 또는 원격 컴퓨터에서 실행되고 있는지를 확인합니다.

### 예 2: 원격 컴퓨터의 WinRM 서비스 상태 확인

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

이 명령은 WinRM 서비스가 server01 컴퓨터에서 실행 되 고 있는지 여부를 확인 합니다.

### 예 3: WinRM 서비스 및 운영 체제 버전의 상태 확인

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

이 명령은 인증 매개 변수를 사용 하 여 WS-Management (WinRM) 서비스가 로컬 컴퓨터에서 실행 되 고 있는지를 테스트 합니다.

Authentication 매개 변수를 사용 하면 **테스트-WSMan** 에서 운영 체제 버전을 반환할 수 있습니다.

### 예 4: 원격 컴퓨터의 WinRM 서비스 및 운영 체제 버전 상태 확인

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

이 명령은 인증 매개 변수를 사용 하 여 WS-Management (WinRM) 서비스가 server01 이라는 컴퓨터에서 실행 되 고 있는지를 테스트 합니다.

Authentication 매개 변수를 사용 하면 **테스트-WSMan** 에서 운영 체제 버전을 반환할 수 있습니다.

## PARAMETERS

### -ApplicationName
연결의 애플리케이션 이름을 지정합니다.
*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.
원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

`http://server01:8080/WSMAN`

세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.
이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.
이 매개 변수는 많은 컴퓨터에서 Windows PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.
이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.

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

### -인증
서버에서 사용할 인증 메커니즘을 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본.
Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.
- 기본.
WS-Management 프로토콜로 구현된 인증 방법을 사용합니다.
이것이 기본값입니다.
- 다이제스트.
Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.
- Kerberos.
클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용하여 상호 인증합니다.
- Negotiate
Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.
예를 들어이 매개 변수 값은 협상을 통해 Kerberos 프로토콜 또는 NTLM이 사용 되는지 여부를 결정할 수 있습니다.
- CredSSP.
사용자가 자격 증명을 위임할 수 있도록 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.
이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.

주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.
이렇게 하면 원격 작업의 보안 위험이 증가합니다.
원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.

중요: *인증* 매개 변수를 지정 하지 않으면 인증을 사용 하지 않고 **테스트 WSMan** 요청이 익명으로 원격 컴퓨터로 전송 됩니다.
요청을 익명으로 만든 경우에는 운영 체제 버전과 관련 된 정보를 반환 하지 않습니다.
대신이 cmdlet은 운영 체제 버전 및 Service Pack 수준 (OS: 0.0.0 SP: 0.0)에 대 한 null 값을 표시 합니다.

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint
이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.
인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다.
인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 Windows PowerShell Cert: 드라이브의 Get-Item 또는 Get-ChildItem 명령을 사용합니다.

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

### -ComputerName
관리 작업을 실행할 컴퓨터를 지정 합니다.
이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.
로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.
로컬 컴퓨터가 기본값입니다.
원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.
이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.
User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 합니다.
또는 Get-Credential cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다.
사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port
클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.
전송이 HTTP인 경우 기본 포트는 80입니다.
전송이 HTTPS인 경우 기본 포트는 443입니다.

전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.

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

### -UseSSL
원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.
기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.
*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.
연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet은 어떠한 입력도 허용하지 않습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력 개체도 생성하지 않습니다.

## 참고

* 기본적으로 **테스트-WSMan** cmdlet은 인증을 사용 하지 않고 WinRM 서비스를 쿼리 하며 운영 체제 버전과 관련 된 정보를 반환 하지 않습니다. 대신, 운영 체제 버전 및 Service Pack 수준 (OS: 0.0.0 SP: 0.0)에 대 한 null 값이 표시 됩니다.

*

## 관련 링크

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)
