---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 07c10f33b0cffd56d84ddf6aab3553a0b71e4017
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860714"
---
# Invoke-WebRequest

## 개요
인터넷의 웹 페이지에서 콘텐츠를 가져옵니다.

## SYNTAX

### StandardMethod (기본값)

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

## 설명

`Invoke-WebRequest`Cmdlet은 HTTP 및 HTTPS 요청을 웹 페이지나 웹 서비스로 보냅니다. 응답을 구문 분석 하 고 링크, 이미지 및 기타 중요 한 HTML 요소 컬렉션을 반환 합니다.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

PowerShell 7.0부터는 `Invoke-WebRequest` 환경 변수에 의해 정의 된 프록시 구성을 지원 합니다. 이 문서의 [참고](#notes) 섹션을 참조 하세요.

## 예제

### 예제 1: 웹 요청 보내기

이 예제에서는 cmdlet을 사용 하 여 `Invoke-WebRequest` Bing.com 사이트에 웹 요청을 보냅니다.

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

첫 번째 명령은 요청을 실행 하 고 응답을 변수에 저장 합니다 `$Response` .

두 번째 명령은 **Name** 속성이 다음과 같은 **inputfield** 를 가져옵니다 `"* Value"` . 필터링 된 결과를로 파이프 하 여 `Select-Object` **Name** 및 **Value** 속성을 선택 합니다.

### 예제 2: 상태 저장 웹 서비스 사용

이 예제에서는 `Invoke-WebRequest` 상태 저장 웹 서비스에서 cmdlet을 사용 하는 방법을 보여 줍니다.

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

에 대 한 첫 번째 호출은 `Invoke-WebRequest` 로그인 요청을 보냅니다. 이 명령은 **-sessionvariable** 매개 변수 값에 대해 "Session" 값을 지정 하 고 결과를 변수에 저장 합니다 `$LoginResponse` . 명령이 완료 되 면 `$LoginResponse` 변수에가 포함 되 `BasicHtmlWebResponseObject` 고 `$Session` 변수에 `WebRequestSession` 개체가 포함 됩니다. 그러면 사용자가 사이트에 기록 됩니다.

에 대 한 호출은 `$Session` `WebRequestSession` 변수의 개체를 표시 합니다.

두 번째 호출에서는 사용자가 `Invoke-WebRequest` 사이트에 로그인 해야 하는 사용자의 프로필을 페치합니다. 변수에 저장 된 세션 데이터는 `$Session` 로그인 중에 생성 된 사이트에 세션 쿠키를 제공 하는 데 사용 됩니다. 결과는 변수에 저장 됩니다 `$ProfileResponse` .

에 대 한 호출은 `$ProfileResponse` 변수에를 표시 합니다 `BasicHtmlWebResponseObject` .

### 예제 3: 웹 페이지에서 링크 가져오기

이 예제에서는 웹 페이지의 링크를 가져옵니다. Cmdlet을 사용 하 여 `Invoke-WebRequest` 웹 페이지 콘텐츠를 가져옵니다. 그런 다음  `BasicHtmlWebResponseObject` 를 반환 하는의 Links 속성과 `Invoke-WebRequest` 각 링크의 **Href** 속성을 사용 합니다.

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### 예제 4: 요청 된 페이지에 정의 된 인코딩을 사용 하 여 응답 콘텐츠를 파일에 씁니다.

이 예제에서는 cmdlet을 사용 하 여 `Invoke-WebRequest` PowerShell 설명서 페이지의 웹 페이지 콘텐츠를 검색 합니다.

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

첫 번째 명령은 페이지를 검색 하 고 응답 개체를 변수에 저장 합니다 `$Response` .

두 번째 명령은를 만들어 `StreamWriter` 응답 콘텐츠를 파일에 쓰는 데 사용 합니다. 응답 개체의 **encoding** 속성은 파일에 대 한 인코딩을 설정 하는 데 사용 됩니다.

마지막 몇 개의 명령은 **콘텐츠** 속성을 파일에 쓴 다음를 삭제 합니다 `StreamWriter` .

웹 요청이 텍스트 콘텐츠를 반환 하지 않는 경우 **Encoding** 속성은 null입니다.

### 예 5: 다중 파트/양식 데이터 파일 제출

이 예제에서는 cmdlet을 사용 하 여 `Invoke-WebRequest` 파일을 `multipart/form-data` 제출으로 업로드 합니다. 이 파일은가 `c:\document.txt` 인 양식 필드로 제출 됩니다 `document` `Content-Type` `text/plain` .

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### 예제 6: 간소화 된 다중 파트/양식 데이터 전송

일부 Api는 `multipart/form-data` 파일 및 혼합 콘텐츠를 업로드 하는 데 제출 해야 합니다. 이 예제에서는 사용자 프로필을 업데이트 하는 방법을 보여 줍니다.

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

프로필 양식에는,,,, `firstName` `lastName` `email` `avatar` `birthday` 및 `hobbies` 필드가 필요 합니다. API는 필드에 사용자 프로필 pic를 제공 하기 위한 이미지가 필요 `avatar` 합니다. API는 `hobbies` 동일한 형식으로 여러 항목을 전송할 수도 있습니다.

`$Form`해시 테이블을 만들 때 키 이름이 폼 필드 이름으로 사용 됩니다. 기본적으로 해시 테이블의 값은 문자열로 변환 됩니다. **System.object** 값이 있으면 파일 내용이 제출 됩니다. 배열 또는 목록과 같은 컬렉션이 있으면 폼 필드가 여러 번 전송 됩니다.

`Get-Item`키에서를 사용 하면 `avatar` `FileInfo` 개체가 값으로 설정 됩니다. 그 결과의 이미지 데이터가 `jdoe.png` 전송 됩니다.

키에 목록을 제공 하면 `hobbies` `hobbies` 필드는 각 목록 항목에 대해 한 번씩 제출에 표시 됩니다.

### 예 7: Invoke-WebRequest에서 비 성공 메시지 Catch

에서 `Invoke-WebRequest` 비 성공 HTTP 메시지 (404, 500 등)를 발견 하면 출력을 반환 하지 않고 종료 오류를 throw 합니다. 오류를 catch 하 고 **StatusCode** 를 보려면 블록으로 실행을 묶을 수 있습니다 `try/catch` .

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

### -AllowUnencryptedAuthentication

암호화 되지 않은 연결을 통해 자격 증명과 암호를 보낼 수 있습니다. 기본적으로로 시작 하지 않는 **Uri** 를 사용 하 여 **자격 증명** 을 제공 하거나 **인증** 옵션을 제공 하면 `https://` 오류가 발생 하 고 요청은 암호화 되지 않은 연결에 대 한 일반 텍스트의 암호를 실수로 통신 하지 않도록 중단 됩니다. 사용자의 위험에 따라이 동작을 재정의 하려면 **Allowunencryptedauthentication** 매개 변수를 제공 합니다.

> [!WARNING]
> 이 매개 변수를 사용 하는 것은 안전 하지 않으므로 사용 하지 않는 것이 좋습니다. 암호화 된 연결을 제공할 수 없는 레거시 시스템과의 호환성을 위해서만 제공 됩니다. 사용자의 위험에 따라를 사용 합니다.

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

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

### -인증

요청에 사용할 명시적 인증 유형을 지정 합니다. 기본값은 **None**(없음)입니다.
**UseDefaultCredentials** 에는 **인증** 을 사용할 수 없습니다.

사용 가능한 인증 옵션:

- **None**: **인증이** 제공 되지 않은 경우의 기본 옵션입니다. 명시적 인증을 사용 하지 않습니다.
- **기본**: **자격 증명이** 필요 합니다. 자격 증명은의 형식으로 RFC 7617 기본 인증 헤더에 전송 됩니다 `base64(user:password)` .
- **전달자**: **토큰이** 필요 합니다. `Authorization: Bearer`제공 된 토큰을 사용 하 여 RFC 6750 헤더를 보냅니다. **OAuth** 에 대 한 별칭입니다.
- **OAuth**: **토큰이** 필요 합니다. `Authorization: Bearer`제공 된 토큰을 사용 하 여 RFC 6750 헤더를 보냅니다. **전달자** 에 대 한 별칭입니다.

**인증** 을 제공 하면 `Authorization` **헤더** 에 제공 되거나 **websession** 에 포함 된 모든 헤더가 재정의 됩니다.

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -본문

요청의 본문을 지정합니다. 본문은 헤더 뒤에 오는 요청 내용입니다.
본문 값을로 파이프 할 수도 있습니다 `Invoke-WebRequest` .

**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.

입력이 GET 요청이 고 본문이 `IDictionary` (일반적으로 해시 테이블) 이면 본문이 쿼리 매개 변수로 URI에 추가 됩니다. 다른 요청 유형 (예: POST)의 경우 본문은 표준 형식의 요청 본문 값으로 설정 됩니다 `name=value` .

**Body** 매개 변수는 개체를 허용할 수도 있습니다 `System.Net.Http.MultipartFormDataContent` . 이렇게 하면 `multipart/form-data` 요청을 용이 하 게 합니다. **본문** 에 대해 **MultipartFormDataContent** 개체가 제공 되는 경우에는 **ContentType**, **헤더** 또는 **Websession** 매개 변수에 제공 된 모든 콘텐츠 관련 헤더가 **MultipartFormDataContent** 개체의 콘텐츠 헤더에 의해 재정의 됩니다. 이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

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

보안 웹 요청에 사용 되는 클라이언트 인증서를 지정 합니다. 인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.

인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 () 드라이브에서 cmdlet을 사용 `Cert:` 합니다. 인증서가 유효 하지 않거나 권한이 없는 경우 명령이 실패 합니다.

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

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 로컬 사용자 계정에만 매핑될 수 있습니다. 도메인 계정에서는 작동 하지 않습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.

> [!NOTE]
> 이 기능은 현재 Windows OS 플랫폼 에서만 지원 됩니다.

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

이 매개 변수를 생략 하 고 요청 메서드를 POST로 `Invoke-WebRequest` 설정 하면에서 콘텐츠 형식을로 설정 합니다 `application/x-www-form-urlencoded` . 그렇지 않으면 호출에서 콘텐츠 형식이 지정 되지 않습니다.

**MultipartFormDataContent** 개체가 **본문** 에 제공 되 면 **ContentType** 이 재정의 됩니다.

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

**자격 증명** 은 단독으로 사용 하거나 특정 **인증** 매개 변수 옵션과 함께 사용할 수 있습니다. 단독으로 사용 하는 경우 원격 서버에서 인증 챌린지 요청을 보내는 경우에만 원격 서버에 자격 증명을 제공 합니다. **인증** 옵션과 함께 사용 하는 경우 자격 증명을 명시적으로 보냅니다.

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

### -CustomMethod

웹 요청에 사용 되는 사용자 지정 메서드를 지정 합니다. 이는 끝점에 필요한 요청 메서드가 **메서드에서** 사용 가능한 옵션이 아닌 경우에 사용할 수 있습니다. **메서드** 및 **custommethod** 는 함께 사용할 수 없습니다.

이 예제에서는 `TEST` API에 대 한 HTTP 요청을 만듭니다.

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
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

### -폼

사전을 제출으로 변환 `multipart/form-data` 합니다. **폼** 은 **본문과** 함께 사용할 수 없습니다.
**ContentType** 을 사용 하면 무시 됩니다.

사전의 키는 양식 필드 이름으로 사용 됩니다. 기본적으로 양식 값은 문자열 값으로 변환 됩니다.

이 값이 **system.object** 이면 이진 파일 내용이 제출 됩니다. 파일 **이름은 파일 이름 속성으로** 제출 됩니다. MIME 형식은로 설정 됩니다 `application/octet-stream` . `Get-Item` 는 **system.object** 를 제공 하는 데 사용할 수 있습니다.

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

값이 배열 또는 목록과 같은 컬렉션 형식인 경우 for 필드는 여러 번 제출 됩니다.
목록의 값은 기본적으로 문자열로 처리 됩니다. 이 값이 **system.object** 이면 이진 파일 내용이 제출 됩니다. 중첩 컬렉션은 지원 되지 않습니다.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

위의 예제에서 필드는 `tags` 각, 및에 대해 한 번씩 폼에서 세 번 제공 됩니다 `Vacation` `Italy` `2017` . `pictures`또한이 필드는 폴더의 각 파일에 대해 한 번씩 제출 됩니다 `2017-Italy` . 해당 폴더에 있는 파일의 이진 내용이 값으로 전송 됩니다.

이 기능은 PowerShell 6.1.0에서 추가 되었습니다.

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

### -헤더

웹 요청의 헤더를 지정합니다. 해시 테이블 또는 사전을 입력합니다.

UserAgent 헤더를 설정하려면 **UserAgent** 매개 변수를 사용합니다. 이 매개 변수를 사용 하 여 **사용자 에이전트** 또는 쿠키 헤더를 지정할 수 없습니다.

`Content-Type` **본문** 에 대해 **MultipartFormDataContent** 개체를 제공 하면와 같은 콘텐츠 관련 헤더가 재정의 됩니다.

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

파일에서 웹 요청의 내용을 가져옵니다. 경로와 파일 이름을 입력합니다. 경로를 생략할 경우 기본값은 현재 위치입니다.

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
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRetryCount

400과 599 사이의 오류 코드를 수신 하는 경우 PowerShell에서 연결을 다시 시도 하는 횟수 304를 지정 합니다. 다시 시도 횟수를 지정 하는 **RetryIntervalSec** 매개 변수도 참조 하세요.

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

**Custommethod** 매개 변수는 위에 나열 되지 않은 요청 메서드에 사용할 수 있습니다.

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoProxy

Cmdlet이 대상에 연결 하는 데 프록시를 사용 하지 않음을 나타냅니다. 환경에 구성 된 프록시를 무시 해야 하는 경우이 스위치를 사용 합니다. 이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
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

### -PreserveAuthorizationOnRedirect

Cmdlet이 `Authorization` 리디렉션 전체에 헤더 (있는 경우)를 유지 해야 함을 나타냅니다.

기본적으로이 cmdlet은 `Authorization` 리디렉션하기 전에 헤더를 제거 합니다. 이 매개 변수를 지정 하면 헤더를 리디렉션 위치로 전송 해야 하는 경우에이 논리가 사용 되지 않습니다.

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

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
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 **User@Domain.Com** 하거나 `PSCredential` cmdlet에 의해 생성 된 개체와 같은 개체를 입력 합니다 `Get-Credential` .

이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다. 동일한 명령에서 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 사용할 수 없습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 **프록시** 매개 변수로 지정 된 프록시 서버에 액세스 함을 나타냅니다.

이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다. 동일한 명령에서 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 사용할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Resume

부분 파일 다운로드를 다시 시작 하는 데 가장 적합 한 작업을 수행 합니다. **Resume** 은 **출력** 을 필요로 합니다.

**다시 시작** 은 로컬 파일 및 원격 파일의 크기에 대해서만 작동 하며 로컬 파일과 원격 파일이 동일한 다른 유효성 검사를 수행 하지 않습니다.

로컬 파일 크기가 원격 파일 크기 보다 작은 경우 cmdlet은 파일 다운로드를 다시 시작 하 고 나머지 바이트를 파일의 끝에 추가 하려고 합니다.

로컬 파일 크기가 원격 파일 크기와 같을 경우 아무 작업도 수행 되지 않으며 cmdlet은 다운로드를 이미 완료 한 것으로 가정 합니다.

로컬 파일 크기가 원격 파일 크기 보다 큰 경우 로컬 파일을 덮어쓰고 전체 원격 파일을 다시 다운로드 합니다. 이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.

원격 서버에서 다운로드 다시 시작을 지원 하지 않는 경우 로컬 파일을 덮어쓰고 전체 원격 파일을 다시 다운로드 합니다. 이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.

로컬 파일이 없으면 로컬 파일이 생성 되 고 전체 원격 파일이 다운로드 됩니다. 이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.

이 기능은 PowerShell 6.1.0에서 추가 되었습니다.

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

### -RetryIntervalSec

400과 599 사이의 오류 코드 (포함 또는 304)를 받을 때 연결 다시 시도 간격을 지정 합니다. 다시 시도 횟수를 지정 하는 **MaximumRetryCount** 매개 변수도 참조 하세요.

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

### -SessionVariable

이 cmdlet이 웹 요청 세션을 만들고 값에 저장 하는 데 사용할 변수를 지정 합니다.
달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.

세션 변수를 지정 하면에서 `Invoke-WebRequest` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다. 명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.

원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다. 쿠키, 자격 증명, 최대 리디렉션 값 및 사용자 에이전트 문자열을 포함 하 여 연결 및 요청에 대 한 정보를 포함 하는 개체입니다. 이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.

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

### -SkipCertificateCheck

인증서 유효성 검사를 건너뜁니다. 여기에는 만료, 해지, 신뢰할 수 있는 루트 인증 등의 모든 유효성 검사가 포함 됩니다.

> [!WARNING]
> 이 매개 변수를 사용 하는 것은 안전 하지 않으므로 사용 하지 않는 것이 좋습니다. 이 스위치는 테스트 목적으로 자체 서명 된 인증서를 사용 하는 알려진 호스트에만 사용할 수 있습니다. 사용자의 위험에 따라를 사용 합니다.

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

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

### -SkipHeaderValidation

Cmdlet이 유효성 검사 없이 요청에 헤더를 추가 함을 나타냅니다.

이 스위치는 표준을 준수 하지 않는 헤더 값이 필요한 사이트에 사용 해야 합니다.
이 스위치를 지정 하면 해당 값을 선택 하지 않은 상태로 전달할 수 있도록 유효성 검사가 비활성화 됩니다. 지정 된 경우 모든 헤더는 유효성 검사 없이 추가 됩니다.

이 스위치는 **ContentType**, **Headers** 및 **UserAgent** 매개 변수에 전달 된 값에 대 한 유효성 검사를 사용 하지 않도록 설정 합니다.

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

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

### -SkipHttpErrorCheck

이 매개 변수를 설정 하면 cmdlet이 HTTP 오류 상태를 무시 하 고 응답을 계속 처리 합니다.
오류 응답은 성공 하는 것 처럼 파이프라인에 기록 됩니다.

이 매개 변수는 PowerShell 7에서 도입 되었습니다.

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

### -SslProtocol

웹 요청에 허용 되는 SSL/TLS 프로토콜을 설정 합니다. 기본적으로 시스템에서 지원 되는 SSL/TLS 프로토콜은 모두 허용 됩니다. **Sslprotocol** 은 규정 준수를 위해 특정 프로토콜을 제한할 수 있습니다.

**Sslprotocol** 은 **websslprotocol** 플래그 열거형을 사용 합니다. 플래그 표기법을 사용 하거나 여러 **Websslprotocol** 옵션을 **bor** 와 결합 하 여 둘 이상의 프로토콜을 제공할 수 있지만, 여러 프로토콜을 제공 하는 것은 모든 플랫폼에서 지원 되지 않습니다.

> [!NOTE]
> Windows가 아닌 플랫폼에서는를 제공 `Tls` 하거나 옵션으로 지정할 수 없습니다 `Tls12` .

이 기능은 PowerShell 6.0.0에서 추가 되었습니다.

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

시간이 초과 되기 전에 요청이 보류 될 수 있는 기간을 지정 합니다. 초 단위로 값을 입력 합니다. 기본값 0은 무기한 시간 제한을 지정합니다.

DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 **Timeoutsec** 를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 WebException이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.

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

### -Token

요청에 포함할 OAuth 또는 전달자 토큰입니다. **토큰** 은 특정 **인증** 옵션에 필요 합니다. 독립적으로 사용할 수는 없습니다.

**토큰** 은 토큰을 포함 하는을 사용 `SecureString` 합니다. 토큰을 수동으로 제공 하려면 다음을 사용 합니다.

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Security.SecureString
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

웹 요청이 전송 되는 인터넷 리소스의 URI (Uniform Resource Identifier)를 지정 합니다. URI를 입력합니다. 이 매개 변수는 HTTP 또는 HTTPS만 지원 합니다.

이 매개 변수는 필수입니다. 매개 변수 이름 **Uri** 는 선택 사항입니다.

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

이 매개 변수는 더 이상 사용 되지 않습니다. PowerShell 6.0.0부터 모든 웹 요청은 기본 구문 분석만 사용 합니다. 이 매개 변수는 이전 버전과의 호환성을 위해서만 포함 되며 cmdlet의 작업에는 영향을 주지 않습니다.

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

Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 웹 요청을 보내는 것을 나타냅니다. 이는 **인증** 또는 **자격 증명과** 함께 사용할 수 없으며, 일부 플랫폼에서 지원 되지 않을 수 있습니다.

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

기본 사용자 에이전트는 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 각 운영 체제 및 플랫폼에 대해 약간 변형 된와 비슷합니다.

대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, InternetExplorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 클래스의 속성을 사용 합니다.

예를 들어 다음 명령은 Internet Explorer에 대 한 사용자 에이전트 문자열을 사용 합니다.

```powershell
Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)
```

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

웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다. 매개 변수 값이 웹 요청 세션의 값보다 우선합니다. `Content-Type` **본문** 에 대해 **MultipartFormDataContent** 개체를 제공 하는 경우와 같은 콘텐츠 관련 헤더만 재정의 됩니다.

원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다. 쿠키, 자격 증명, 최대 리디렉션 값 및 사용자 에이전트 문자열을 포함 하 여 연결 및 요청에 대 한 정보를 포함 하는 개체입니다. 이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.

웹 요청 세션을 만들려면 명령의 **Sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-WebRequest` 합니다. `Invoke-WebRequest` 세션을 만들어 변수에 저장 합니다. 후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.

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

웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-WebRequest` .

## 출력

### Microsoft. PowerShell. BasicHtmlWebResponseObject

## 참고

PowerShell 6.0.0 부터는 `Invoke-WebRequest` 기본 구문 분석만 지원 합니다.

자세한 내용은 [Basichtmlwebresponseobject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)를 참조 하세요.

.NET Core 3.1의 변경 내용으로 인해 PowerShell 7.0 이상에서는 [Httpclient. defaultproxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 속성을 사용 하 여 프록시 구성을 확인 합니다.

이 속성의 값은 플랫폼에 따라 결정 됩니다.

- **Windows의 경우**: 환경 변수에서 프록시 구성을 읽습니다. 이러한 변수가 정의 되지 않은 경우 속성은 사용자의 프록시 설정에서 파생 됩니다.
- **MacOS의 경우**: 환경 변수에서 프록시 구성을 읽습니다. 이러한 변수가 정의 되지 않은 경우 속성은 시스템의 프록시 설정에서 파생 됩니다.
- **Linux**: 환경 변수에서 프록시 구성을 읽습니다. 이러한 변수가 정의 되지 않은 경우 속성은 모든 주소를 우회 하는 구성 되지 않은 인스턴스를 초기화 합니다.

`DefaultProxy`Windows 및 Unix 기반 플랫폼에서 초기화 하는 데 사용 되는 환경 변수는 다음과 같습니다.

- ` HTTP_PROXY`: HTTP 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소입니다.
- `HTTPS_PROXY`: HTTPS 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소입니다.
- `ALL_PROXY`: 또는의 경우 HTTP 및 HTTPS 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소를 `HTTP_PROXY` `HTTPS_PROXY` 정의 하지 않습니다.
- `NO_PROXY`: 프록시에서 제외 되어야 하는 쉼표로 구분 된 호스트 이름 목록입니다.

## 관련 링크

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
