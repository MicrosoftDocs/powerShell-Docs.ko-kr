---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: d06ede0e27713b1a309aa2ed265f02881d34124e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217089"
---
# Connect-WSMan

## 개요
원격 컴퓨터의 WinRM 서비스에 연결합니다.

## SYNTAX

### ComputerName (기본값)

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## 설명
**연결-WSMan** cmdlet은 원격 컴퓨터의 WinRM 서비스에 연결 하 고 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.
WSMan 공급자의 컨텍스트에서이 cmdlet을 사용 하 여 원격 컴퓨터의 WinRM 서비스에 연결할 수 있습니다.
그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에 연결할 수도 있습니다.
원격 컴퓨터는 WSMan 공급자의 루트 디렉터리에 표시 됩니다.

클라이언트 컴퓨터와 서버 컴퓨터가 서로 다른 도메인 또는 작업 그룹에 있는 경우에는 명시적 자격 증명이 필요합니다.

원격 컴퓨터의 WinRM 서비스에서 연결을 끊는 방법에 대 한 자세한 내용은 Disconnect-WSMan cmdlet을 참조 하세요.

## 예제

### 예 1: 원격 컴퓨터에 연결

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

이 명령은 원격 server01 컴퓨터에 대한 연결을 만듭니다.

**연결-wsman** cmdlet은 일반적으로 원격 컴퓨터 (이 경우 server01 컴퓨터)에 연결 하기 위해 wsman 공급자의 컨텍스트에서 사용 됩니다.
그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터에 대한 연결을 설정할 수도 있습니다.
이러한 연결은 **ComputerName** 목록에 표시 됩니다.

### 예 2: 관리자 자격 증명을 사용 하 여 원격 컴퓨터에 연결

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

이 명령은 관리자 계정 자격 증명을 사용하여 원격 시스템 server01에 대한 연결을 만듭니다.

첫 번째 명령은 Get-Credential cmdlet을 사용하여 관리자 자격 증명을 가져온 후 $cred 변수에 저장합니다.
**Get 자격 증명** 은 대화 상자를 통해 사용자 이름 및 암호를 묻는 메시지를 표시 하 고, 시스템 레지스트리 설정에 따라 명령줄에서 암호를 입력 하 라는 메시지를 표시 합니다.

두 번째 명령은 *Credential* 매개 변수를 사용 하 여 $cred에 저장 된 자격 증명을 **연결-WSMan** 에 전달 합니다.
**연결-WSMan** 은 관리자 자격 증명을 사용 하 여 원격 시스템 server01에 연결 합니다.

### 예 3: 지정 된 포트를 통해 원격 컴퓨터에 연결

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

이 명령은 포트 80을 통해 원격 server01 컴퓨터에 대한 연결을 만듭니다.

### 예 4: 연결 옵션을 사용 하 여 원격 컴퓨터에 연결

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

이 예에서는 **New-WSManSessionOption** 명령에 정의 된 연결 옵션을 사용 하 여 원격 server01 컴퓨터에 대 한 연결을 만듭니다.

첫 번째 명령은 **New-WSManSessionOption** 을 사용 하 여 $a 변수에 연결 설정 옵션 집합을 저장 합니다.
이 경우 세션 옵션은 연결 시간 제한을 30초(30,000밀리초)로 설정합니다.

두 번째 명령은 *Sessionoption* 매개 변수를 사용 하 여 $a 변수에 저장 된 자격 증명을 **연결-WSMan** 에 전달 합니다.
그런 다음, **연결-WSMan** 은 지정 된 세션 옵션을 사용 하 여 원격 server01 컴퓨터에 연결 합니다.

## PARAMETERS

### -ApplicationName
연결의 애플리케이션 이름을 지정합니다.
*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.
원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

`http://server01:8080/WSMAN`

세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.
이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.
이 매개 변수는 많은 컴퓨터에서 PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.
이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName
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

인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.

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
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI
연결 엔드포인트를 지정합니다.
이 문자열의 형식은 다음과 같습니다.

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

다음 문자열은이 매개 변수의 형식이 올바르게 지정 된 값입니다.

`http://Server01:8080/WSMAN`

URI는 정규화된 URI여야 합니다.

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -OptionSet
요청의 특성을 수정 하거나 구체화 하기 위해 서비스에 대 한 스위치 집합을 지정 합니다.
이러한 스위치는 서비스 마다 다르기 때문에 명령줄 셸에 사용 되는 스위치와 유사 합니다.
원하는 수의 옵션을 지정할 수 있습니다.

다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port
클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.
전송이 HTTP인 경우 기본 포트는 80입니다.
전송이 HTTPS인 경우 기본 포트는 443입니다.

전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.
그러나 *Skipcncheck* 매개 변수가 *sessionoption* 매개 변수의 일부로 지정 된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.
*Skipcncheck* 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 해야 합니다.

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

### -SessionOption
WS-Management 세션에 대 한 확장 옵션을 지정 합니다.
New-WSManSessionOption cmdlet을 사용 하 여 만든 **Sessionoption** 개체를 입력 합니다.
사용할 수 있는 옵션에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help New-WSManSessionOption` .

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL
원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.
기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.
*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.
연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
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
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* WS-Management 세션을 만들지 않고도 원격 컴퓨터에서 관리 명령 또는 쿼리 관리 데이터를 실행할 수 있습니다. Invoke-WSManAction의 *ComputerName* 매개 변수와 Get-wsmaninstance를 사용 하 여이 작업을 수행할 수 있습니다. *ComputerName* 매개 변수를 사용 하는 경우 PowerShell은 단일 명령에 사용 되는 임시 연결을 만듭니다. 명령이 실행된 후 연결이 닫힙니다.

*

## 관련 링크

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

[Test-WSMan](Test-WSMan.md)
