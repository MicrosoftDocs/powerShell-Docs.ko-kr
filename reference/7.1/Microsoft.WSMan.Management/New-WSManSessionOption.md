---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: c0730daaed26fac1e8e8023532f201233fd90013
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215793"
---
# New-WSManSessionOption

## 개요
WS-Management cmdlet에 대 한 입력 매개 변수로 사용할 세션 옵션 해시 테이블을 만듭니다.

## SYNTAX

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## 설명
**새-WSManSessionOption** cmdlet은 wsman cmdlet에 전달할 수 있는 wsman 세션 옵션 해시 테이블을 만듭니다.

- Get-WSManInstance
- Set-WSManInstance
- Invoke-WSManAction
- Connect-WSMan

## 예제

### 예 1: 연결 옵션을 사용 하는 연결 만들기

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

이 예에서는 server01 **옵션** 으로 정의 된 연결 옵션을 사용 하 여 원격 컴퓨터에 대 한 연결을 만듭니다.

첫 번째 명령은 **New-WSManSessionOption** 을 사용 하 여 $a 변수에 연결 설정 옵션 집합을 저장 합니다.
이 경우 세션 옵션은 연결 시간 제한을 30초(30,000밀리초)로 설정합니다.

두 번째 명령은 *Sessionoption* 매개 변수를 사용 하 여 $a 변수에 저장 된 자격 증명을 **연결-WSMan** 에 전달 합니다.
그런 다음, **연결-WSMan** 은 지정 된 세션 옵션을 사용 하 여 원격 server01 컴퓨터에 연결 합니다.

**연결-wsman** 은 일반적으로 원격 컴퓨터 (이 경우 server01 컴퓨터)에 연결 하기 위해 wsman 공급자의 컨텍스트에서 사용 됩니다.
그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터에 대한 연결을 설정할 수도 있습니다.
이러한 연결은 **ComputerName** 목록에 표시 됩니다.

## PARAMETERS

### -NoEncryption
연결에서 HTTP를 통한 원격 작업에 암호화를 사용 하지 않음을 나타냅니다.

암호화 되지 않은 트래픽은 기본적으로 사용 하도록 설정 되어 있지 않습니다.
로컬 구성에서 사용 하도록 설정 해야 합니다.

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

### -OperationTimeout
WS-Management 작업에 대 한 제한 시간 (밀리초)을 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -System.management.automation.remoting.proxyaccesstype
프록시 서버가 배치되는 메커니즘을 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- ProxyIEConfig.
현재 사용자의 Internet Explorer 프록시 구성을 사용 합니다.
- ProxyWinHttpConfig.
WSMan 클라이언트는 ProxyCfg.exe 유틸리티를 사용 하 여 WinHTTP에 대해 구성 된 프록시 설정을 사용 합니다.
- ProxyAutoDetect.
프록시 서버 자동 검색을 강제로 실행 합니다.
- ProxyNoProxyServer.
프록시 서버를 사용 하지 마십시오.
모든 호스트 이름을 로컬에서 확인 합니다.

기본값은 ProxyIEConfig입니다.

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication
프록시에 사용할 인증 방법을 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본.
Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.
- 다이제스트.
Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.
- Negotiate
Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.
이러한 예로는 Kerberos 프로토콜 및 NTLM이 있습니다.

기본값은 Negotiate입니다.

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential
중간 웹 프록시를 통해 액세스할 수 있는 권한이 있는 사용자 계정을 지정 합니다.

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

### -SkipCACheck
HTTPS를 통해 연결 하는 경우 클라이언트에서 서버 인증서가 신뢰할 수 있는 CA (인증 기관)에 의해 서명 되었는지 확인 하지 않도록 지정 합니다.
원격 컴퓨터가 물리적으로 안전 하 고 격리 된 네트워크에 속해 있거나 원격 컴퓨터가 WS-Management 구성에서 신뢰할 수 있는 호스트로 나열 되어 있는 경우와 같이 원격 컴퓨터를 다른 방법으로 신뢰할 수 있는 경우에만이 옵션을 사용 합니다.

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

### -SkipCNCheck
서버의 인증서 CN (일반 이름)이 서버의 호스트 이름과 일치할 필요가 없도록 지정 합니다.
이 옵션은 HTTPS를 사용하는 원격 작업에만 사용됩니다.
이 옵션은 신뢰할 수 있는 컴퓨터에만 사용해야 합니다.

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

### -SkipRevocationCheck
연결에서 서버 인증서의 해지 상태를 확인 하지 않음을 나타냅니다.

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

### -SPNPort
원격 서버의 연결 서비스 사용자 이름 (SPN)에 추가할 포트 번호를 지정 합니다.
SPN은 인증 메커니즘이 Kerberos 또는 Negotiate인 경우 사용됩니다.

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

### -UseUTF16
연결이 UTF8 형식 대신 UTF16 형식으로 요청을 인코드 함을 나타냅니다.
기본값은 UTF8 인코딩입니다.

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

## 출력

### SessionOption

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

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

