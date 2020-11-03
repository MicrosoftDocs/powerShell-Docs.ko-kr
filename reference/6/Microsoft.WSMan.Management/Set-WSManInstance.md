---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 3f4ee9edf6e8dfce21a51ff9c055fe56a0cbef3c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218546"
---
# Set-WSManInstance

## 개요
리소스와 관련된 관리 정보를 수정합니다.

## SYNTAX

### ComputerName (기본값)

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## 설명

Set-WSManInstance cmdlet은 리소스와 관련된 관리 정보를 수정합니다.

이 cmdlet은 WinRM 연결/전송 계층을 사용하여 정보를 수정합니다.

## 예제

### 예제 1: 로컬 컴퓨터에서 수신기를 사용 하지 않도록 설정

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

이 명령은 로컬 컴퓨터에 https 수신기를 사용하지 않도록 설정합니다.

중요: *Valueset* 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.

예를 들어이 명령에서

실패: `-ValueSet @{enabled="False"}`

성공: `-ValueSet @{Enabled="False"}`

### 예 2: 로컬 컴퓨터의 최대 봉투 크기 설정

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

이 명령은 로컬 컴퓨터에 MaxEnvelopeSizekb 값을 200으로 설정합니다.

중요: ValueSet 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.

예를 들어 위의 명령을 사용합니다.

실패:-ValueSet @ {MaxEnvelopeSizeKB = "200"}

성공:-ValueSet @ {MaxEnvelopeSizekb = "200"}

### 예제 3: 원격 컴퓨터에서 수신기 사용 안 함

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

이 명령은 원격 컴퓨터 SERVER02에 https 수신기를 사용하지 않도록 설정합니다.

중요: ValueSet 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.

예를 들어 위의 명령을 사용합니다.

실패:-ValueSet @ {enabled = "False"}

성공:-ValueSet @ {Enabled = "False"}

## PARAMETERS

### -ApplicationName

연결의 애플리케이션 이름을 지정합니다.
ApplicationName 매개 변수의 기본값은 "WSMAN"입니다.
원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

다음은 그 예입니다. 

`http://server01:8080/WSMAN`

세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.
"WSMAN"의 이 기본 설정은 대부분의 사용자에게 적합합니다.
이 매개 변수는 많은 컴퓨터에서 Windows PowerShell을 실행하는 한 컴퓨터에 대한 원격 연결을 설정할 때 사용하도록 설계되었습니다.
이 경우 IIS는 효율성을 위해 WS-Management(관리용 웹 서비스)를 호스트합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### -인증

서버에서 사용할 인증 메커니즘을 지정합니다.
가능한 값은 다음과 같습니다.

- Basic: Basic은 사용자 이름과 암호가 일반 텍스트로 서버 또는 프록시에 전송 되는 체계입니다.
- 기본값: WS-Management 프로토콜에 의해 구현 된 인증 방법을 사용 합니다. 이것이 기본값입니다.
- 다이제스트: 다이제스트는 챌린지에 대해 서버 지정 데이터 문자열을 사용 하는 챌린지-응답 체계입니다.
- Kerberos: 클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용 하 여 상호 인증 합니다.
- Negotiate: Negotiate는 인증에 사용할 체계를 결정 하기 위해 서버 또는 프록시와 협상 하는 챌린지-응답 체계입니다. 예를 들어 이 매개 변수 값을 통해 협상에서 Kerberos 프로토콜이 사용되는지 또는 NTLM이 사용되는지를 결정할 수 있습니다.
- CredSSP: 사용자가 자격 증명을 위임할 수 있도록 허용 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다. 이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.

주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.
이렇게 하면 원격 작업의 보안 위험이 증가합니다.
원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

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

관리 작업을 실행하려는 컴퓨터를 지정합니다.
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
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

연결 엔드포인트를 지정합니다.
이 문자열의 형식은 다음과 같습니다.

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

다음 문자열은 이 매개 변수의 형식이 올바르게 지정된 값입니다.

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
사용자 이름 (예: "User01", "Domain01\User01" 또는 "")을 입력 User@Domain.com 합니다.
또는 PSCredential 개체(예: Get-Credential cmdlet에서 반환된 개체)를 입력합니다.
사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.

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

### -언어

필터 조건자에 사용할 언어를 지정합니다.
원격 서비스에서 지원되는 모든 언어가 가능합니다.
언어 URI에 다음과 같은 별칭을 사용할 수 있습니다.

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- 선택기 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- 연결 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

관리 리소스를 업데이트하는 데 사용되는 파일 경로를 지정합니다.
ResourceURI 매개 변수 및 SelectorSet 매개 변수를 사용하여 관리 리소스를 지정합니다.
예를 들어 다음 명령은 FilePath 매개 변수를 사용합니다.

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

이 명령은 파일의 입력을 사용하여 스풀러 서비스에 대해 StopService 메서드를 호출합니다.
Input.xml 파일은 다음 콘텐츠를 포함합니다.

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -조각

지정된 작업을 위해 업데이트하거나 검색할 인스턴스 내의 섹션을 지정합니다.
예를 들어 스풀러 서비스의 상태를 가져오려면 "-Fragment Status"를 지정합니다.

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

### -OptionSet

요청의 특성을 수정하거나 구체화하기 위해 스위치 집합을 서비스에 전달합니다.
이는 명령줄 셸에 사용되는 스위치와 유사한데, 서비스에 국한되기 때문입니다.
원하는 수의 옵션을 지정할 수 있습니다.

다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.

-OptionSet @{a=1;b=2;c=3}

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
전송으로 HTTPS를 사용하는 경우 ComputerName 매개 변수 값이 서버의 인증서 CN(일반 이름)과 일치해야 합니다.
그러나 SkipCNCheck 매개 변수가 SessionOption 매개 변수 서버의 일부로 지정된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.
SkipCNCheck 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용해야 합니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceURI

리소스 클래스 또는 인스턴스의 URI(Uniform Resource Identifier)를 포함합니다.
URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.

URI는 접두사와 리소스 경로로 구성됩니다.
다음은 그 예입니다. 

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SelectorSet

특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.
SelectorSet 매개 변수는 리소스의 인스턴스가 둘 이상 존재하는 경우 사용됩니다.
SelectorSet 매개 변수 값은 해시 테이블이어야 합니다.
다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.

-SelectorSet @{Name="WinRM";ID="yyy"}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

WS-Management 세션에 대한 확장된 옵션 집합을 정의합니다.
New-WSManSessionOption cmdlet을 사용하여 만든 SessionOption 개체를 입력합니다.
사용할 수 있는 옵션에 대한 자세한 내용은 New-WSManSessionOption을 참조하세요.

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

원격 컴퓨터에 대한 연결을 설정할 때 SSL(Secure Sockets Layer) 프로토콜이 반드시 사용되도록 지정합니다.
기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.
UseSSL 매개 변수를 사용하여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.
연결에 사용되는 포트에 SSL을 사용할 수 없는 경우에 이 매개 변수를 지정하면 명령이 실패합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ValueSet

관리 리소스를 수정하는 데 도움이 되는 해시 테이블을 지정합니다.
ResourceURI 매개 변수 및 SelectorSet 매개 변수를 사용하여 관리 리소스를 지정합니다.
ValueSet 매개 변수 값은 해시 테이블이어야 합니다.

```yaml
Type: System.Collections.Hashtable
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

이 cmdlet은 어떠한 입력도 허용하지 않습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

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

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
