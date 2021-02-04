---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: f3545065d4879830a5051ef687f210c7fbd1251e
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860664"
---
# Invoke-WebRequest

## 개요
인터넷의 웹 페이지에서 콘텐츠를 가져옵니다.

## SYNTAX

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## 설명

`Invoke-WebRequest`Cmdlet은 HTTP, HTTPS, FTP 및 파일 요청을 웹 페이지나 웹 서비스로 보냅니다.
응답을 구문 분석하고 양식, 링크, 이미지 및 기타 중요한 HTML 요소 컬렉션을 반환합니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

> [!NOTE]
> 기본적으로 페이지를 구문 분석 하 여 속성을 채우도록 웹 페이지의 스크립트 코드를 실행할 수 있습니다 `ParsedHtml` .
> 스위치를 사용 `-UseBasicParsing` 하 여이를 표시 하지 않습니다.

## 예제

### 예제 1: 웹 요청 보내기

이 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` Bing.com 사이트에 웹 요청을 보냅니다.

```powershell
$R = Invoke-WebRequest -URI https://www.bing.com?q=how+many+feet+in+a+mile
$R.AllElements | Where-Object {
    $_.name -like "* Value" -and $_.tagName -eq "INPUT"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

첫 번째 명령은 요청을 실행 하 고 응답을 변수에 저장 합니다 `$R` .

두 번째 명령은 **Allelements** 속성에서 **name** 속성이 "* Value"와 비슷하며 **tagName** 이 "INPUT" 인 개체를 필터링 합니다. 필터링 된 결과를로 파이프 하 여 `Select-Object` **name** 및 **value** 속성을 선택 합니다.

### 예제 2: 상태 저장 웹 서비스 사용

이 예에서는 `Invoke-WebRequest` Facebook과 같은 상태 저장 웹 서비스에서 cmdlet을 사용 하는 방법을 보여 줍니다.

```powershell
$R = Invoke-WebRequest https://www.facebook.com/login.php -SessionVariable fb
# This command stores the first form in the Forms property of the $R variable in the $Form variable.
$Form = $R.Forms[0]
# This command shows the fields available in the Form.
$Form.fields
```

```Output
Key                     Value
---                     -----
...
email
pass
...
```

```powershell
# These commands populate the username and password of the respective Form fields.
$Form.Fields["email"]="User01@Fabrikam.com"
$Form.Fields["pass"]="P@ssw0rd"
# This command creates the Uri that will be used to log in to facebook.
# The value of the Uri parameter is the value of the Action property of the form.
$Uri = "https://www.facebook.com" + $Form.Action
# Now the Invoke-WebRequest cmdlet is used to sign into the Facebook web service.
# The WebRequestSession object in the $FB variable is passed as the value of the WebSession parameter.
# The value of the Body parameter is the hash table in the Fields property of the form.
# The value of the *Method* parameter is POST. The command saves the output in the $R variable.
$R = Invoke-WebRequest -Uri $Uri -WebSession $FB -Method POST -Body $Form.Fields
$R.StatusDescription
```

첫 번째 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` 로그인 요청을 보냅니다. 이 명령은 **sessionvariable** 매개 변수 값에 대해 "FB" 값을 지정 하 고 결과를 변수에 저장 합니다 `$R` . 명령이 완료 되 면 변수는 `$R` **Htmlwebresponseobject** 를 포함 하 고 `$FB` 변수는 **webrequestsession** 개체를 포함 합니다.

Cmdlet이 facebook에 로그인 한 후 `Invoke-WebRequest` 변수에 있는 웹 응답 개체의 **statusdescription** 속성은 사용자가 `$R` 성공적으로 로그인 했음을 나타냅니다.

### 예제 3: 웹 페이지에서 링크 가져오기

이 명령은 웹 페이지에 있는 링크를 가져옵니다.

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

`Invoke-WebRequest`Cmdlet은 웹 페이지 콘텐츠를 가져옵니다. 그러면 반환 된 **Htmlwebresponseobject** 의 **Links** 속성이 각 링크의 **Href** 속성을 표시 하는 데 사용 됩니다.

### 예제 4: Invoke-WebRequest에서 비 성공 메시지 Catch

에서 `Invoke-WebRequest` 비 성공 HTTP 메시지 (404, 500 등)를 발견 하면 출력을 반환 하지 않고 종료 오류를 throw 합니다. 오류를 catch 하 고 **StatusCode** 를 보려면 블록으로 실행을 묶을 수 있습니다 `try/catch` . 다음 예제에서는이를 수행 하는 방법을 보여 줍니다.

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost"
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

종료 오류는 `catch` **예외** 개체에서 **StatusCode** 를 검색 하는 블록에 의해 catch 됩니다.

## PARAMETERS

### -본문

요청의 본문을 지정합니다.
본문은 헤더 뒤에 오는 요청 내용입니다.
본문 값을로 파이프 할 수도 있습니다 `Invoke-WebRequest` .

**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.

입력이 GET 요청이 고 본문이 **IDictionary** (일반적으로 해시 테이블) 이면 본문이 쿼리 매개 변수로 URI에 추가 됩니다. 다른 GET 요청의 경우 본문은 표준 형식의 요청 본문 값으로 설정 됩니다 `name=value` .

본문이 폼 이거나 호출의 출력 인 경우 `Invoke-WebRequest` PowerShell은 양식 필드에 요청 콘텐츠를 설정 합니다.
예를 들면 다음과 같습니다.

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- 또는

`Invoke-RestMethod https://website.com/service.aspx -Body $r.Forms\[0\]`

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

인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` **인증서** () 드라이브에서 cmdlet을 사용 `Cert:` 합니다. 인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.

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

요청을 보낼 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다. 인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.

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

이 매개 변수를 생략 하 고 요청 메서드를 POST로 `Invoke-WebRequest` 설정 하면에서 콘텐츠 형식을 application/x-www-form-urlencoded로 설정 합니다. 그러지 않으면 호출에서 콘텐츠 형식이 지정되지 않습니다.

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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

Cmdlet이 HTTP 헤더의 **KeepAlive** 값을 **False** 로 설정 함을 나타냅니다. 기본적으로 **KeepAlive** 는 **True** 입니다. **KeepAlive** 는 후속 요청의 신속한 처리를 위해 서버에 대한 영구 연결을 설정합니다.

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

### -헤더

웹 요청의 헤더를 지정합니다. 해시 테이블 또는 사전을 입력합니다.

**UserAgent** 헤더를 설정 하려면 **UserAgent** 매개 변수를 사용 합니다. 이 매개 변수를 사용 하 여 **UserAgent** 또는 쿠키 헤더를 지정할 수 없습니다.

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

연결에 실패 하기 전에 PowerShell이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션하는 횟수를 지정 합니다. 기본값은 5입니다. 값 0은 모든 리디렉션을 차단합니다.

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

### -메서드

웹 요청에 사용되는 메서드를 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- DELETE
- 가져오기
- Head
- Merge
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -출력

이 cmdlet이 응답 본문을 저장 하는 출력 파일을 지정 합니다. 경로와 파일 이름을 입력합니다.
경로를 생략할 경우 기본값은 현재 위치입니다.

기본적으로는 `Invoke-WebRequest` 결과를 파이프라인으로 반환 합니다. 결과를 파일과 파이프라인으로 보내려면 **Passthru** 매개 변수를 사용합니다.

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

Cmdlet이 결과를 파일에 기록 하는 것 외에도 반환 함을 나타냅니다. 이 매개 변수는 명령에 **OutFile** 매개 변수도 사용된 경우에만 유효합니다.

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

### -프록시

인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.
네트워크 프록시 서버의 URI를 입력합니다.

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

또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다. 동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.

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

### -ProxyUseDefaultCredentials

Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 **프록시** 매개 변수로 지정 된 프록시 서버에 액세스 함을 나타냅니다.

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

이 cmdlet이 웹 요청 세션을 만들고 값에 저장 하는 데 사용할 변수를 지정 합니다.
달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.

세션 변수를 지정 하면에서 `Invoke-WebRequest` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다. 명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.

원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다. 쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다. 이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.

후속 웹 요청에서 웹 요청 세션을 사용하려면 **WebSession** 매개 변수 값에 세션 변수를 지정합니다. PowerShell은 새 연결을 설정할 때 웹 요청 세션 개체의 데이터를 사용 합니다. 웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다. 매개 변수 값이 웹 요청 세션의 값보다 우선합니다.

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

DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 **Timeoutsec** 를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 **WebException** 이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.

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

웹 요청이 전송되는 인터넷 리소스의 URI(Uniform Resource Identifier)를 지정합니다. URI를 입력합니다. 이 매개 변수는 HTTP, HTTPS, FTP 및 FILE 값을 지원합니다.

이 매개 변수는 필수입니다.

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

Cmdlet이 DOM (문서 개체 모델) 구문 분석 없이 HTML 콘텐츠에 대 한 응답 개체를 사용 함을 나타냅니다. 이 매개 변수는 Windows Server 운영 체제의 Server Core 설치와 같이 컴퓨터에 Internet Explorer가 설치되지 않은 경우에 필요합니다.

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

Cmdet가 현재 사용자의 자격 증명을 사용 하 여 웹 요청을 보내는 것을 나타냅니다.

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

웹 요청에 대한 사용자 에이전트 문자열을 지정합니다. 기본 사용자 에이전트는 `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` 각 운영 체제 및 플랫폼에 대해 약간 변형 된와 비슷합니다.

대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, InternetExplorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 클래스의 속성을 사용 합니다. 예를 들어 다음 명령은 Internet Explorer에 대 한 사용자 에이전트 문자열을 사용 합니다.

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

웹 요청 세션을 만들려면 명령의 **sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-WebRequest` 합니다. `Invoke-WebRequest` 세션을 만들어 변수에 저장 합니다. 후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.

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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Object

웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-WebRequest` .

## 출력

### Microsoft.PowerShell.Commands.HtmlWebResponseObject

## 참고

## 관련 링크

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
