---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/13/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: c89f7351e9c874cea2cc0cd5e0912e3ca0d8b0bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213842"
---
# Invoke-RestMethod

## 개요
HTTP 또는 HTTPS 요청을 RESTful 웹 서비스로 보냅니다.

## 구문

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## Description

Cmdlet은 다양 `Invoke-RestMethod` 한 구조화 된 데이터를 반환 하는 REST (Representational State Transfer) 웹 서비스로 HTTP 및 HTTPS 요청을 보냅니다.

Windows PowerShell은 데이터 형식에 따라 응답 형식을 지정합니다. RSS 또는 ATOM 피드의 경우 Windows PowerShell에서 항목 또는 항목 XML 노드를 반환합니다. JSON(JavaScript Object Notation) 또는 XML의 경우 Windows PowerShell에서 내용을 개체로 변환(또는 역직렬화)합니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

> [!NOTE]
> 기본적으로 페이지를 구문 분석 하 여 속성을 채우도록 웹 페이지의 스크립트 코드를 실행할 수 있습니다 `ParsedHtml` . **Usebasicparsing 분석** 스위치를 사용 하 여이를 표시 하지 않습니다.

## 예

### 예제 1: PowerShell RSS 피드 가져오기

```powershell
Invoke-RestMethod -Uri https://devblogs.microsoft.com/powershell/feed/ |
  Format-Table -Property Title, pubDate
```

```Output
Title                                                                pubDate
-----                                                                -------
Join the PowerShell 10th Anniversary Celebration!                    Tue, 08 Nov 2016 23:00:04 +0000
DSC Resource Kit November 2016 Release                               Thu, 03 Nov 2016 00:19:07 +0000
PSScriptAnalyzer Community Call - Oct 18, 2016                       Thu, 13 Oct 2016 17:52:35 +0000
New Home for In-Box DSC Resources                                    Sat, 08 Oct 2016 07:13:10 +0000
New Social Features on Gallery                                       Fri, 30 Sep 2016 23:04:34 +0000
PowerShellGet and PackageManagement in PowerShell Gallery and GitHub Thu, 29 Sep 2016 22:21:42 +0000
PowerShell Security at DerbyCon                                      Wed, 28 Sep 2016 01:13:19 +0000
DSC Resource Kit September Release                                   Thu, 22 Sep 2016 00:25:37 +0000
PowerShell DSC and implicit remoting broken in KB3176934             Tue, 23 Aug 2016 15:07:50 +0000
PowerShell on Linux and Open Source!                                 Thu, 18 Aug 2016 15:32:02 +0000
```

이 명령은 cmdlet을 사용 하 여 `Invoke-RestMethod` PowerShell 블로그 RSS 피드에서 정보를 가져옵니다. 이 명령은 cmdlet을 사용 하 여 `Format-Table` 각 블로그의 **Title** 및 **pubDate** 속성 값을 테이블에 표시 합니다.

### 예제 2

다음 예제에서는 사용자가 `Invoke-RestMethod` 를 실행 하 여 사용자 조직의 인트라넷 웹 사이트에서 POST 요청을 수행 합니다.

```powershell
$Cred = Get-Credential

# Next, allow the use of self-signed SSL certificates.

[System.Net.ServicePointManager]::ServerCertificateValidationCallback = { $True }

# Create variables to store the values consumed by the Invoke-RestMethod command.
# The search variable contents are later embedded in the body variable.

$Server = 'server.contoso.com'
$Url = "https://${server}:8089/services/search/jobs/export"
$Search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"

# The cmdlet handles URL encoding. The body variable describes the search criteria, specifies CSV as
# the output mode, and specifies a time period for returned data that starts two days ago and ends
# one day ago. The body variable specifies values for parameters that apply to the particular REST
# API with which Invoke-RestMethod is communicating.

$Body = @{
    search = $Search
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}

# Now, run the Invoke-RestMethod command with all variables in place, specifying a path and file
# name for the resulting CSV output file.

Invoke-RestMethod -Method Post -Uri $url -Credential $Cred -Body $body -OutFile output.csv

{"preview":true,"offset":0,"result":{"sourcetype":"contoso1","count":"9624"}}

{"preview":true,"offset":1,"result":{"sourcetype":"contoso2","count":"152"}}

{"preview":true,"offset":2,"result":{"sourcetype":"contoso3","count":"88494"}}

{"preview":true,"offset":3,"result":{"sourcetype":"contoso4","count":"15277"}}
```

### 예제 3: 여러 헤더 전달

이 예제에서는에서 여러 헤더를 REST API에 전달 하는 방법을 보여 줍니다 `hash-table` .

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

Api는 인증, 유효성 검사 등을 위해 헤더를 전달 해야 하는 경우가 많습니다.

### 예제 3: 양식 데이터 전송

본문이 폼 이거나 다른 호출의 출력 인 경우 `Invoke-WebRequest` PowerShell은 양식 필드에 요청 콘텐츠를 설정 합니다.

다음은 그 예입니다. 

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## 매개 변수

### -본문

요청의 본문을 지정합니다. 본문은 헤더 뒤에 오는 요청 내용입니다.
본문 값을로 파이프 할 수도 있습니다 `Invoke-RestMethod` .

**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.

입력이 GET 요청이고 본문이 IDictionary(일반적으로 해시 테이블)이면 본문이 쿼리 매개 변수로 URI에 추가됩니다. 다른 요청 유형(예: POST)의 경우 본문이 표준 이름=값 형식의 요청 본문 값으로 설정됩니다.

> [!WARNING]
> `with -1-byte payload`본문의 크기가 모두 알려지고 HTTP 헤더에 전송 되더라도 게시 본문의 자세한 정보 출력은로 종료 됩니다 `Content-Length` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -인증서

보안 웹 요청에 사용되는 클라이언트 인증서를 지정합니다. 인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.

인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 () 드라이브에서 cmdlet을 사용 `Cert:` 합니다. 인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

요청을 보낼 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` Windows PowerShell () 드라이브에서 또는 명령을 사용 `Cert:` 합니다.

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

### -ContentType

웹 요청의 콘텐츠 형식을 지정합니다.

이 매개 변수를 생략 하 고 요청 메서드가 POST 이면 `Invoke-RestMethod` 내용 유형을 "application/x-www-form-urlencoded"로 설정 합니다. 그러지 않으면 호출에서 콘텐츠 형식이 지정되지 않습니다.

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

### -Credential

요청을 보낼 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

HTTP 헤더의 **KeepAlive** 값을 False로 설정합니다. 기본적으로 **KeepAlive** 는 True입니다.
**KeepAlive** 는 후속 요청의 신속한 처리를 위해 서버에 대한 영구 연결을 설정합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: KeepAlive
Accept pipeline input: False
Accept wildcard characters: False
```

### -헤더

웹 요청의 헤더를 지정합니다. 해시 테이블 또는 사전을 입력합니다.

UserAgent 헤더를 설정하려면 **UserAgent** 매개 변수를 사용합니다. 이 매개 변수를 사용하여 UserAgent 또는 쿠키 헤더를 지정할 수 없습니다.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InFile

파일에서 웹 요청의 내용을 가져옵니다.

경로와 파일 이름을 입력합니다. 경로를 생략할 경우 기본값은 현재 위치입니다.

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

### -MaximumRedirection

연결이 실패하기 전에 Windows PowerShell에서 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션하는 횟수를 결정합니다. 기본값은 5입니다. 값 0은 모든 리디렉션을 차단합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -메서드

웹 요청에 사용되는 메서드를 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- DELETE
- 가져오기
- Head
- 병합
- 옵션
- 패치
- 게시
- Put
- 추적

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -출력

응답 본문을 지정한 출력 파일에 저장합니다. 경로와 파일 이름을 입력합니다. 경로를 생략할 경우 기본값은 현재 위치입니다.

기본적으로는 `Invoke-RestMethod` 결과를 파이프라인으로 반환 합니다. 결과를 파일과 파이프라인으로 보내려면 **Passthru** 매개 변수를 사용합니다.

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

### -PassThru

결과를 반환하고 파일에 씁니다. 이 매개 변수는 명령에 **OutFile** 매개 변수도 사용된 경우에만 유효합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No output
Accept pipeline input: False
Accept wildcard characters: False
```

### -프록시

인터넷 리소스에 직접 연결하는 대신 요청에 프록시 서버를 사용합니다. 네트워크 프록시 서버의 URI를 입력합니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다. 동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

현재 사용자의 자격 증명을 사용하여 **Proxy** 매개 변수에 지정된 프록시 서버에 액세스합니다.

이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다. 동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.

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

### -SessionVariable

웹 요청 세션을 만들어 지정한 변수 값에 저장합니다. 달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.

세션 변수를 지정 하면에서 `Invoke-RestMethod` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다. 명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.

원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다. 쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다. 이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.

후속 웹 요청에서 웹 요청 세션을 사용하려면 **WebSession** 매개 변수 값에 세션 변수를 지정합니다. Windows PowerShell은 새 연결을 설정할 때 웹 요청 세션 개체의 데이터를 사용합니다. 웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다. 매개 변수 값이 웹 요청 세션의 값보다 우선합니다.

동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

시간이 초과 되기 전에 요청이 보류 될 수 있는 기간을 지정 합니다. 초 단위로 값을 입력 합니다. 기본값 0은 무기한 시간 제한을 지정합니다.

DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 TimeoutSec를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 WebException이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -전송자 인코딩

transfer-encoding HTTP 응답 헤더의 값을 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 청크
- 압축
- Deflate
- GZip
- ID

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uri

웹 요청이 전송되는 인터넷 리소스의 URI(Uniform Resource Identifier)를 지정합니다. 이 매개 변수는 HTTP, HTTPS, FTP 및 FILE 값을 지원합니다.

이 매개 변수는 필수적 요소입니다. 매개 변수 이름 ( **Uri** )은 선택 사항입니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseBasicParsing 분석

Cmdlet에서 기본 구문 분석을 사용 함을 나타냅니다. Cmdlet은 **문자열** 개체의 원시 HTML을 반환 합니다.

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

### -UseDefaultCredentials

현재 사용자의 자격 증명을 사용하여 웹 요청을 보냅니다.

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

### -UserAgent

웹 요청에 대한 사용자 에이전트 문자열을 지정합니다.

기본 사용자 에이전트는 각 운영 체제와 플랫폼마다 약간 변형되지만 "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0"과 유사합니다.

대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, Internet Explorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands) 클래스의 속성을 사용 합니다.

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

### -WebSession

웹 요청 세션을 지정합니다. 달러 기호 ()를 포함 하 여 변수 이름을 입력 `$` 합니다.

웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다. 매개 변수 값이 웹 요청 세션의 값보다 우선합니다.

원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다. 쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다. 이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.

웹 요청 세션을 만들려면 명령의 **sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-RestMethod` 합니다. `Invoke-RestMethod` 세션을 만들어 변수에 저장 합니다. 후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.

동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
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

### System.Object

웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-RestMethod` .

## outputs

### System.Xml.Xml문서, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.string

cmdlet의 출력은 검색된 콘텐츠의 형식에 따라 달라집니다.

### PSObject

요청에서 JSON 문자열을 반환 하는 경우는 `Invoke-RestMethod` 문자열을 나타내는 PSObject를 반환 합니다.

## 메모

## 관련 링크

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
