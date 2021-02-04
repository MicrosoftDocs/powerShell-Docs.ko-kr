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
# <span data-ttu-id="bf44c-102">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="bf44c-102">Invoke-WebRequest</span></span>

## <span data-ttu-id="bf44c-103">개요</span><span class="sxs-lookup"><span data-stu-id="bf44c-103">SYNOPSIS</span></span>
<span data-ttu-id="bf44c-104">인터넷의 웹 페이지에서 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-104">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="bf44c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf44c-105">SYNTAX</span></span>

### <span data-ttu-id="bf44c-106">StandardMethod (기본값)</span><span class="sxs-lookup"><span data-stu-id="bf44c-106">StandardMethod (Default)</span></span>

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

### <span data-ttu-id="bf44c-107">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="bf44c-107">StandardMethodNoProxy</span></span>

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

### <span data-ttu-id="bf44c-108">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="bf44c-108">CustomMethod</span></span>

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

### <span data-ttu-id="bf44c-109">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="bf44c-109">CustomMethodNoProxy</span></span>

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

## <span data-ttu-id="bf44c-110">설명</span><span class="sxs-lookup"><span data-stu-id="bf44c-110">DESCRIPTION</span></span>

<span data-ttu-id="bf44c-111">`Invoke-WebRequest`Cmdlet은 HTTP 및 HTTPS 요청을 웹 페이지나 웹 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-111">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="bf44c-112">응답을 구문 분석 하 고 링크, 이미지 및 기타 중요 한 HTML 요소 컬렉션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-112">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="bf44c-113">이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-113">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="bf44c-114">PowerShell 7.0부터는 `Invoke-WebRequest` 환경 변수에 의해 정의 된 프록시 구성을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-114">Beginning in PowerShell 7.0, `Invoke-WebRequest` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="bf44c-115">이 문서의 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf44c-115">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="bf44c-116">예제</span><span class="sxs-lookup"><span data-stu-id="bf44c-116">EXAMPLES</span></span>

### <span data-ttu-id="bf44c-117">예제 1: 웹 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="bf44c-117">Example 1: Send a web request</span></span>

<span data-ttu-id="bf44c-118">이 예제에서는 cmdlet을 사용 하 여 `Invoke-WebRequest` Bing.com 사이트에 웹 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-118">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="bf44c-119">첫 번째 명령은 요청을 실행 하 고 응답을 변수에 저장 합니다 `$Response` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-119">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="bf44c-120">두 번째 명령은 **Name** 속성이 다음과 같은 **inputfield** 를 가져옵니다 `"* Value"` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-120">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="bf44c-121">필터링 된 결과를로 파이프 하 여 `Select-Object` **Name** 및 **Value** 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-121">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="bf44c-122">예제 2: 상태 저장 웹 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="bf44c-122">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="bf44c-123">이 예제에서는 `Invoke-WebRequest` 상태 저장 웹 서비스에서 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-123">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

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

<span data-ttu-id="bf44c-124">에 대 한 첫 번째 호출은 `Invoke-WebRequest` 로그인 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-124">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="bf44c-125">이 명령은 **-sessionvariable** 매개 변수 값에 대해 "Session" 값을 지정 하 고 결과를 변수에 저장 합니다 `$LoginResponse` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-125">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="bf44c-126">명령이 완료 되 면 `$LoginResponse` 변수에가 포함 되 `BasicHtmlWebResponseObject` 고 `$Session` 변수에 `WebRequestSession` 개체가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-126">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="bf44c-127">그러면 사용자가 사이트에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-127">This logs the user into the site.</span></span>

<span data-ttu-id="bf44c-128">에 대 한 호출은 `$Session` `WebRequestSession` 변수의 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-128">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="bf44c-129">두 번째 호출에서는 사용자가 `Invoke-WebRequest` 사이트에 로그인 해야 하는 사용자의 프로필을 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-129">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="bf44c-130">변수에 저장 된 세션 데이터는 `$Session` 로그인 중에 생성 된 사이트에 세션 쿠키를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-130">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="bf44c-131">결과는 변수에 저장 됩니다 `$ProfileResponse` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-131">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="bf44c-132">에 대 한 호출은 `$ProfileResponse` 변수에를 표시 합니다 `BasicHtmlWebResponseObject` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-132">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="bf44c-133">예제 3: 웹 페이지에서 링크 가져오기</span><span class="sxs-lookup"><span data-stu-id="bf44c-133">Example 3: Get links from a web page</span></span>

<span data-ttu-id="bf44c-134">이 예제에서는 웹 페이지의 링크를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-134">This example gets the links in a web page.</span></span> <span data-ttu-id="bf44c-135">Cmdlet을 사용 하 여 `Invoke-WebRequest` 웹 페이지 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-135">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="bf44c-136">그런 다음  `BasicHtmlWebResponseObject` 를 반환 하는의 Links 속성과 `Invoke-WebRequest` 각 링크의 **Href** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-136">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="bf44c-137">예제 4: 요청 된 페이지에 정의 된 인코딩을 사용 하 여 응답 콘텐츠를 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-137">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="bf44c-138">이 예제에서는 cmdlet을 사용 하 여 `Invoke-WebRequest` PowerShell 설명서 페이지의 웹 페이지 콘텐츠를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-138">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

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

<span data-ttu-id="bf44c-139">첫 번째 명령은 페이지를 검색 하 고 응답 개체를 변수에 저장 합니다 `$Response` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-139">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="bf44c-140">두 번째 명령은를 만들어 `StreamWriter` 응답 콘텐츠를 파일에 쓰는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-140">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="bf44c-141">응답 개체의 **encoding** 속성은 파일에 대 한 인코딩을 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-141">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="bf44c-142">마지막 몇 개의 명령은 **콘텐츠** 속성을 파일에 쓴 다음를 삭제 합니다 `StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-142">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="bf44c-143">웹 요청이 텍스트 콘텐츠를 반환 하지 않는 경우 **Encoding** 속성은 null입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-143">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="bf44c-144">예 5: 다중 파트/양식 데이터 파일 제출</span><span class="sxs-lookup"><span data-stu-id="bf44c-144">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="bf44c-145">이 예제에서는 cmdlet을 사용 하 여 `Invoke-WebRequest` 파일을 `multipart/form-data` 제출으로 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-145">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="bf44c-146">이 파일은가 `c:\document.txt` 인 양식 필드로 제출 됩니다 `document` `Content-Type` `text/plain` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-146">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

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

### <span data-ttu-id="bf44c-147">예제 6: 간소화 된 다중 파트/양식 데이터 전송</span><span class="sxs-lookup"><span data-stu-id="bf44c-147">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="bf44c-148">일부 Api는 `multipart/form-data` 파일 및 혼합 콘텐츠를 업로드 하는 데 제출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-148">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="bf44c-149">이 예제에서는 사용자 프로필을 업데이트 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-149">This example demonstrates updating a user profile.</span></span>

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

<span data-ttu-id="bf44c-150">프로필 양식에는,,,, `firstName` `lastName` `email` `avatar` `birthday` 및 `hobbies` 필드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-150">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="bf44c-151">API는 필드에 사용자 프로필 pic를 제공 하기 위한 이미지가 필요 `avatar` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-151">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="bf44c-152">API는 `hobbies` 동일한 형식으로 여러 항목을 전송할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-152">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="bf44c-153">`$Form`해시 테이블을 만들 때 키 이름이 폼 필드 이름으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-153">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="bf44c-154">기본적으로 해시 테이블의 값은 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-154">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="bf44c-155">**System.object** 값이 있으면 파일 내용이 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-155">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="bf44c-156">배열 또는 목록과 같은 컬렉션이 있으면 폼 필드가 여러 번 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-156">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="bf44c-157">`Get-Item`키에서를 사용 하면 `avatar` `FileInfo` 개체가 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-157">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="bf44c-158">그 결과의 이미지 데이터가 `jdoe.png` 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-158">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="bf44c-159">키에 목록을 제공 하면 `hobbies` `hobbies` 필드는 각 목록 항목에 대해 한 번씩 제출에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-159">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="bf44c-160">예 7: Invoke-WebRequest에서 비 성공 메시지 Catch</span><span class="sxs-lookup"><span data-stu-id="bf44c-160">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="bf44c-161">에서 `Invoke-WebRequest` 비 성공 HTTP 메시지 (404, 500 등)를 발견 하면 출력을 반환 하지 않고 종료 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-161">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="bf44c-162">오류를 catch 하 고 **StatusCode** 를 보려면 블록으로 실행을 묶을 수 있습니다 `try/catch` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-162">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

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

<span data-ttu-id="bf44c-163">종료 오류는 `catch` **예외** 개체에서 **StatusCode** 를 검색 하는 블록에 의해 catch 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-163">The terminating error is caught by the `catch` block, which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="bf44c-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf44c-164">PARAMETERS</span></span>

### <span data-ttu-id="bf44c-165">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="bf44c-165">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="bf44c-166">암호화 되지 않은 연결을 통해 자격 증명과 암호를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-166">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="bf44c-167">기본적으로로 시작 하지 않는 **Uri** 를 사용 하 여 **자격 증명** 을 제공 하거나 **인증** 옵션을 제공 하면 `https://` 오류가 발생 하 고 요청은 암호화 되지 않은 연결에 대 한 일반 텍스트의 암호를 실수로 통신 하지 않도록 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-167">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="bf44c-168">사용자의 위험에 따라이 동작을 재정의 하려면 **Allowunencryptedauthentication** 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-168">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="bf44c-169">이 매개 변수를 사용 하는 것은 안전 하지 않으므로 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-169">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="bf44c-170">암호화 된 연결을 제공할 수 없는 레거시 시스템과의 호환성을 위해서만 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-170">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="bf44c-171">사용자의 위험에 따라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-171">Use at your own risk.</span></span>

<span data-ttu-id="bf44c-172">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-172">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-173">-인증</span><span class="sxs-lookup"><span data-stu-id="bf44c-173">-Authentication</span></span>

<span data-ttu-id="bf44c-174">요청에 사용할 명시적 인증 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-174">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="bf44c-175">기본값은 **None**(없음)입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-175">The default is **None**.</span></span>
<span data-ttu-id="bf44c-176">**UseDefaultCredentials** 에는 **인증** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-176">**Authentication** cannot be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="bf44c-177">사용 가능한 인증 옵션:</span><span class="sxs-lookup"><span data-stu-id="bf44c-177">Available Authentication Options:</span></span>

- <span data-ttu-id="bf44c-178">**None**: **인증이** 제공 되지 않은 경우의 기본 옵션입니다. 명시적 인증을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-178">**None**: This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="bf44c-179">**기본**: **자격 증명이** 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-179">**Basic**: Requires **Credential**.</span></span> <span data-ttu-id="bf44c-180">자격 증명은의 형식으로 RFC 7617 기본 인증 헤더에 전송 됩니다 `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-180">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="bf44c-181">**전달자**: **토큰이** 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-181">**Bearer**: Requires **Token**.</span></span> <span data-ttu-id="bf44c-182">`Authorization: Bearer`제공 된 토큰을 사용 하 여 RFC 6750 헤더를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-182">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="bf44c-183">**OAuth** 에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-183">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="bf44c-184">**OAuth**: **토큰이** 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-184">**OAuth**: Requires **Token**.</span></span> <span data-ttu-id="bf44c-185">`Authorization: Bearer`제공 된 토큰을 사용 하 여 RFC 6750 헤더를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-185">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="bf44c-186">**전달자** 에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-186">This is an alias for **Bearer**</span></span>

<span data-ttu-id="bf44c-187">**인증** 을 제공 하면 `Authorization` **헤더** 에 제공 되거나 **websession** 에 포함 된 모든 헤더가 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-187">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="bf44c-188">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-188">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-189">-본문</span><span class="sxs-lookup"><span data-stu-id="bf44c-189">-Body</span></span>

<span data-ttu-id="bf44c-190">요청의 본문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-190">Specifies the body of the request.</span></span> <span data-ttu-id="bf44c-191">본문은 헤더 뒤에 오는 요청 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-191">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="bf44c-192">본문 값을로 파이프 할 수도 있습니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-192">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="bf44c-193">**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-193">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="bf44c-194">입력이 GET 요청이 고 본문이 `IDictionary` (일반적으로 해시 테이블) 이면 본문이 쿼리 매개 변수로 URI에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-194">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="bf44c-195">다른 요청 유형 (예: POST)의 경우 본문은 표준 형식의 요청 본문 값으로 설정 됩니다 `name=value` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-195">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="bf44c-196">**Body** 매개 변수는 개체를 허용할 수도 있습니다 `System.Net.Http.MultipartFormDataContent` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-196">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="bf44c-197">이렇게 하면 `multipart/form-data` 요청을 용이 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-197">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="bf44c-198">**본문** 에 대해 **MultipartFormDataContent** 개체가 제공 되는 경우에는 **ContentType**, **헤더** 또는 **Websession** 매개 변수에 제공 된 모든 콘텐츠 관련 헤더가 **MultipartFormDataContent** 개체의 콘텐츠 헤더에 의해 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-198">When a **MultipartFormDataContent** object is supplied for **Body**, any Content related headers supplied to the **ContentType**, **Headers**, or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="bf44c-199">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-199">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-200">-인증서</span><span class="sxs-lookup"><span data-stu-id="bf44c-200">-Certificate</span></span>

<span data-ttu-id="bf44c-201">보안 웹 요청에 사용 되는 클라이언트 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-201">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="bf44c-202">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-202">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="bf44c-203">인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 () 드라이브에서 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-203">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="bf44c-204">인증서가 유효 하지 않거나 권한이 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-204">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="bf44c-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="bf44c-205">-CertificateThumbprint</span></span>

<span data-ttu-id="bf44c-206">요청을 보낼 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-206">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="bf44c-207">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="bf44c-208">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="bf44c-209">로컬 사용자 계정에만 매핑될 수 있습니다. 도메인 계정에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-209">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="bf44c-210">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-210">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="bf44c-211">이 기능은 현재 Windows OS 플랫폼 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-211">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="bf44c-212">-ContentType</span><span class="sxs-lookup"><span data-stu-id="bf44c-212">-ContentType</span></span>

<span data-ttu-id="bf44c-213">웹 요청의 콘텐츠 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-213">Specifies the content type of the web request.</span></span>

<span data-ttu-id="bf44c-214">이 매개 변수를 생략 하 고 요청 메서드를 POST로 `Invoke-WebRequest` 설정 하면에서 콘텐츠 형식을로 설정 합니다 `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-214">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="bf44c-215">그렇지 않으면 호출에서 콘텐츠 형식이 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-215">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="bf44c-216">**MultipartFormDataContent** 개체가 **본문** 에 제공 되 면 **ContentType** 이 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-216">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="bf44c-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="bf44c-217">-Credential</span></span>

<span data-ttu-id="bf44c-218">요청을 보낼 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-218">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="bf44c-219">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-219">The default is the current user.</span></span>

<span data-ttu-id="bf44c-220">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-220">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="bf44c-221">**자격 증명** 은 단독으로 사용 하거나 특정 **인증** 매개 변수 옵션과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-221">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="bf44c-222">단독으로 사용 하는 경우 원격 서버에서 인증 챌린지 요청을 보내는 경우에만 원격 서버에 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-222">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="bf44c-223">**인증** 옵션과 함께 사용 하는 경우 자격 증명을 명시적으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-223">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="bf44c-224">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-224">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bf44c-225">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="bf44c-225">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="bf44c-226">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="bf44c-226">-CustomMethod</span></span>

<span data-ttu-id="bf44c-227">웹 요청에 사용 되는 사용자 지정 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-227">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="bf44c-228">이는 끝점에 필요한 요청 메서드가 **메서드에서** 사용 가능한 옵션이 아닌 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-228">This can be used if the Request Method required by the endpoint isn't an available option on the **Method**.</span></span> <span data-ttu-id="bf44c-229">**메서드** 및 **custommethod** 는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-229">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="bf44c-230">이 예제에서는 `TEST` API에 대 한 HTTP 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-230">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="bf44c-231">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-231">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-232">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="bf44c-232">-DisableKeepAlive</span></span>

<span data-ttu-id="bf44c-233">Cmdlet이 HTTP 헤더의 **KeepAlive** 값을 **False** 로 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-233">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="bf44c-234">기본적으로 **KeepAlive** 는 **True** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-234">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="bf44c-235">**KeepAlive** 는 후속 요청의 신속한 처리를 위해 서버에 대한 영구 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-235">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="bf44c-236">-폼</span><span class="sxs-lookup"><span data-stu-id="bf44c-236">-Form</span></span>

<span data-ttu-id="bf44c-237">사전을 제출으로 변환 `multipart/form-data` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-237">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="bf44c-238">**폼** 은 **본문과** 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-238">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="bf44c-239">**ContentType** 을 사용 하면 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-239">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="bf44c-240">사전의 키는 양식 필드 이름으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-240">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="bf44c-241">기본적으로 양식 값은 문자열 값으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-241">By default, form values are converted to string values.</span></span>

<span data-ttu-id="bf44c-242">이 값이 **system.object** 이면 이진 파일 내용이 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-242">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="bf44c-243">파일 **이름은 파일 이름 속성으로** 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-243">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="bf44c-244">MIME 형식은로 설정 됩니다 `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-244">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="bf44c-245">`Get-Item` 는 **system.object** 를 제공 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-245">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="bf44c-246">값이 배열 또는 목록과 같은 컬렉션 형식인 경우 for 필드는 여러 번 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-246">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="bf44c-247">목록의 값은 기본적으로 문자열로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-247">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="bf44c-248">이 값이 **system.object** 이면 이진 파일 내용이 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-248">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="bf44c-249">중첩 컬렉션은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-249">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="bf44c-250">위의 예제에서 필드는 `tags` 각, 및에 대해 한 번씩 폼에서 세 번 제공 됩니다 `Vacation` `Italy` `2017` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-250">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="bf44c-251">`pictures`또한이 필드는 폴더의 각 파일에 대해 한 번씩 제출 됩니다 `2017-Italy` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-251">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="bf44c-252">해당 폴더에 있는 파일의 이진 내용이 값으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-252">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="bf44c-253">이 기능은 PowerShell 6.1.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-253">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="bf44c-254">-헤더</span><span class="sxs-lookup"><span data-stu-id="bf44c-254">-Headers</span></span>

<span data-ttu-id="bf44c-255">웹 요청의 헤더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-255">Specifies the headers of the web request.</span></span> <span data-ttu-id="bf44c-256">해시 테이블 또는 사전을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-256">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="bf44c-257">UserAgent 헤더를 설정하려면 **UserAgent** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-257">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="bf44c-258">이 매개 변수를 사용 하 여 **사용자 에이전트** 또는 쿠키 헤더를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-258">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="bf44c-259">`Content-Type` **본문** 에 대해 **MultipartFormDataContent** 개체를 제공 하면와 같은 콘텐츠 관련 헤더가 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-259">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="bf44c-260">-InFile</span><span class="sxs-lookup"><span data-stu-id="bf44c-260">-InFile</span></span>

<span data-ttu-id="bf44c-261">파일에서 웹 요청의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-261">Gets the content of the web request from a file.</span></span> <span data-ttu-id="bf44c-262">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-262">Enter a path and file name.</span></span> <span data-ttu-id="bf44c-263">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-263">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="bf44c-264">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="bf44c-264">-MaximumRedirection</span></span>

<span data-ttu-id="bf44c-265">연결에 실패 하기 전에 PowerShell이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션하는 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-265">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="bf44c-266">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-266">The default value is 5.</span></span> <span data-ttu-id="bf44c-267">값 0은 모든 리디렉션을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-267">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="bf44c-268">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="bf44c-268">-MaximumRetryCount</span></span>

<span data-ttu-id="bf44c-269">400과 599 사이의 오류 코드를 수신 하는 경우 PowerShell에서 연결을 다시 시도 하는 횟수 304를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-269">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="bf44c-270">다시 시도 횟수를 지정 하는 **RetryIntervalSec** 매개 변수도 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf44c-270">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="bf44c-271">-메서드</span><span class="sxs-lookup"><span data-stu-id="bf44c-271">-Method</span></span>

<span data-ttu-id="bf44c-272">웹 요청에 사용되는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-272">Specifies the method used for the web request.</span></span> <span data-ttu-id="bf44c-273">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-273">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bf44c-274">기본값</span><span class="sxs-lookup"><span data-stu-id="bf44c-274">Default</span></span>
- <span data-ttu-id="bf44c-275">DELETE</span><span class="sxs-lookup"><span data-stu-id="bf44c-275">Delete</span></span>
- <span data-ttu-id="bf44c-276">가져오기</span><span class="sxs-lookup"><span data-stu-id="bf44c-276">Get</span></span>
- <span data-ttu-id="bf44c-277">Head</span><span class="sxs-lookup"><span data-stu-id="bf44c-277">Head</span></span>
- <span data-ttu-id="bf44c-278">Merge</span><span class="sxs-lookup"><span data-stu-id="bf44c-278">Merge</span></span>
- <span data-ttu-id="bf44c-279">옵션</span><span class="sxs-lookup"><span data-stu-id="bf44c-279">Options</span></span>
- <span data-ttu-id="bf44c-280">패치</span><span class="sxs-lookup"><span data-stu-id="bf44c-280">Patch</span></span>
- <span data-ttu-id="bf44c-281">게시</span><span class="sxs-lookup"><span data-stu-id="bf44c-281">Post</span></span>
- <span data-ttu-id="bf44c-282">Put</span><span class="sxs-lookup"><span data-stu-id="bf44c-282">Put</span></span>
- <span data-ttu-id="bf44c-283">추적</span><span class="sxs-lookup"><span data-stu-id="bf44c-283">Trace</span></span>

<span data-ttu-id="bf44c-284">**Custommethod** 매개 변수는 위에 나열 되지 않은 요청 메서드에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-284">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="bf44c-285">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="bf44c-285">-NoProxy</span></span>

<span data-ttu-id="bf44c-286">Cmdlet이 대상에 연결 하는 데 프록시를 사용 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-286">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="bf44c-287">환경에 구성 된 프록시를 무시 해야 하는 경우이 스위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-287">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="bf44c-288">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-288">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-289">-출력</span><span class="sxs-lookup"><span data-stu-id="bf44c-289">-OutFile</span></span>

<span data-ttu-id="bf44c-290">이 cmdlet이 응답 본문을 저장 하는 출력 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-290">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="bf44c-291">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-291">Enter a path and file name.</span></span>
<span data-ttu-id="bf44c-292">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-292">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="bf44c-293">기본적으로는 `Invoke-WebRequest` 결과를 파이프라인으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-293">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="bf44c-294">결과를 파일과 파이프라인으로 보내려면 **Passthru** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-294">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="bf44c-295">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bf44c-295">-PassThru</span></span>

<span data-ttu-id="bf44c-296">Cmdlet이 결과를 파일에 기록 하는 것 외에도 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-296">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="bf44c-297">이 매개 변수는 명령에 **OutFile** 매개 변수도 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-297">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="bf44c-298">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="bf44c-298">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="bf44c-299">Cmdlet이 `Authorization` 리디렉션 전체에 헤더 (있는 경우)를 유지 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-299">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="bf44c-300">기본적으로이 cmdlet은 `Authorization` 리디렉션하기 전에 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-300">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="bf44c-301">이 매개 변수를 지정 하면 헤더를 리디렉션 위치로 전송 해야 하는 경우에이 논리가 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-301">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="bf44c-302">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-302">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-303">-프록시</span><span class="sxs-lookup"><span data-stu-id="bf44c-303">-Proxy</span></span>

<span data-ttu-id="bf44c-304">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-304">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="bf44c-305">네트워크 프록시 서버의 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-305">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="bf44c-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="bf44c-306">-ProxyCredential</span></span>

<span data-ttu-id="bf44c-307">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="bf44c-308">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-308">The default is the current user.</span></span>

<span data-ttu-id="bf44c-309">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 **User@Domain.Com** 하거나 `PSCredential` cmdlet에 의해 생성 된 개체와 같은 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-309">Type a user name, such as **User01** or **Domain01\User01**, **User@Domain.Com**, or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="bf44c-310">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="bf44c-311">동일한 명령에서 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf44c-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="bf44c-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="bf44c-313">Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 **프록시** 매개 변수로 지정 된 프록시 서버에 액세스 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="bf44c-314">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="bf44c-315">동일한 명령에서 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf44c-316">-Resume</span><span class="sxs-lookup"><span data-stu-id="bf44c-316">-Resume</span></span>

<span data-ttu-id="bf44c-317">부분 파일 다운로드를 다시 시작 하는 데 가장 적합 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-317">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="bf44c-318">**Resume** 은 **출력** 을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-318">**Resume** requires **OutFile**.</span></span>

<span data-ttu-id="bf44c-319">**다시 시작** 은 로컬 파일 및 원격 파일의 크기에 대해서만 작동 하며 로컬 파일과 원격 파일이 동일한 다른 유효성 검사를 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-319">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="bf44c-320">로컬 파일 크기가 원격 파일 크기 보다 작은 경우 cmdlet은 파일 다운로드를 다시 시작 하 고 나머지 바이트를 파일의 끝에 추가 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-320">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="bf44c-321">로컬 파일 크기가 원격 파일 크기와 같을 경우 아무 작업도 수행 되지 않으며 cmdlet은 다운로드를 이미 완료 한 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-321">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="bf44c-322">로컬 파일 크기가 원격 파일 크기 보다 큰 경우 로컬 파일을 덮어쓰고 전체 원격 파일을 다시 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-322">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="bf44c-323">이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-323">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="bf44c-324">원격 서버에서 다운로드 다시 시작을 지원 하지 않는 경우 로컬 파일을 덮어쓰고 전체 원격 파일을 다시 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-324">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="bf44c-325">이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-325">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="bf44c-326">로컬 파일이 없으면 로컬 파일이 생성 되 고 전체 원격 파일이 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-326">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="bf44c-327">이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-327">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="bf44c-328">이 기능은 PowerShell 6.1.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-328">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="bf44c-329">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="bf44c-329">-RetryIntervalSec</span></span>

<span data-ttu-id="bf44c-330">400과 599 사이의 오류 코드 (포함 또는 304)를 받을 때 연결 다시 시도 간격을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-330">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="bf44c-331">다시 시도 횟수를 지정 하는 **MaximumRetryCount** 매개 변수도 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf44c-331">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="bf44c-332">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="bf44c-332">-SessionVariable</span></span>

<span data-ttu-id="bf44c-333">이 cmdlet이 웹 요청 세션을 만들고 값에 저장 하는 데 사용할 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-333">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="bf44c-334">달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-334">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="bf44c-335">세션 변수를 지정 하면에서 `Invoke-WebRequest` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-335">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="bf44c-336">명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-336">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="bf44c-337">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-337">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="bf44c-338">쿠키, 자격 증명, 최대 리디렉션 값 및 사용자 에이전트 문자열을 포함 하 여 연결 및 요청에 대 한 정보를 포함 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-338">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="bf44c-339">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-339">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="bf44c-340">후속 웹 요청에서 웹 요청 세션을 사용하려면 **WebSession** 매개 변수 값에 세션 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-340">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="bf44c-341">PowerShell은 새 연결을 설정할 때 웹 요청 세션 개체의 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-341">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="bf44c-342">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-342">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="bf44c-343">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-343">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="bf44c-344">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-344">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf44c-345">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="bf44c-345">-SkipCertificateCheck</span></span>

<span data-ttu-id="bf44c-346">인증서 유효성 검사를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-346">Skips certificate validation checks.</span></span> <span data-ttu-id="bf44c-347">여기에는 만료, 해지, 신뢰할 수 있는 루트 인증 등의 모든 유효성 검사가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-347">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="bf44c-348">이 매개 변수를 사용 하는 것은 안전 하지 않으므로 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-348">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="bf44c-349">이 스위치는 테스트 목적으로 자체 서명 된 인증서를 사용 하는 알려진 호스트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-349">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="bf44c-350">사용자의 위험에 따라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-350">Use at your own risk.</span></span>

<span data-ttu-id="bf44c-351">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-351">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-352">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="bf44c-352">-SkipHeaderValidation</span></span>

<span data-ttu-id="bf44c-353">Cmdlet이 유효성 검사 없이 요청에 헤더를 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-353">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="bf44c-354">이 스위치는 표준을 준수 하지 않는 헤더 값이 필요한 사이트에 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-354">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="bf44c-355">이 스위치를 지정 하면 해당 값을 선택 하지 않은 상태로 전달할 수 있도록 유효성 검사가 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-355">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="bf44c-356">지정 된 경우 모든 헤더는 유효성 검사 없이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-356">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="bf44c-357">이 스위치는 **ContentType**, **Headers** 및 **UserAgent** 매개 변수에 전달 된 값에 대 한 유효성 검사를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-357">This switch disables validation for values passed to the **ContentType**, **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="bf44c-358">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-358">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-359">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="bf44c-359">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="bf44c-360">이 매개 변수를 설정 하면 cmdlet이 HTTP 오류 상태를 무시 하 고 응답을 계속 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-360">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="bf44c-361">오류 응답은 성공 하는 것 처럼 파이프라인에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-361">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="bf44c-362">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-362">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="bf44c-363">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="bf44c-363">-SslProtocol</span></span>

<span data-ttu-id="bf44c-364">웹 요청에 허용 되는 SSL/TLS 프로토콜을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-364">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="bf44c-365">기본적으로 시스템에서 지원 되는 SSL/TLS 프로토콜은 모두 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-365">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="bf44c-366">**Sslprotocol** 은 규정 준수를 위해 특정 프로토콜을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-366">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="bf44c-367">**Sslprotocol** 은 **websslprotocol** 플래그 열거형을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-367">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="bf44c-368">플래그 표기법을 사용 하거나 여러 **Websslprotocol** 옵션을 **bor** 와 결합 하 여 둘 이상의 프로토콜을 제공할 수 있지만, 여러 프로토콜을 제공 하는 것은 모든 플랫폼에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-368">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor**, however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="bf44c-369">Windows가 아닌 플랫폼에서는를 제공 `Tls` 하거나 옵션으로 지정할 수 없습니다 `Tls12` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-369">On non-Windows platforms it may not be possible to supply `Tls` or `Tls12` as an option.</span></span>

<span data-ttu-id="bf44c-370">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-370">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="bf44c-371">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="bf44c-371">-TimeoutSec</span></span>

<span data-ttu-id="bf44c-372">시간이 초과 되기 전에 요청이 보류 될 수 있는 기간을 지정 합니다. 초 단위로 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-372">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="bf44c-373">기본값 0은 무기한 시간 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-373">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="bf44c-374">DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 **Timeoutsec** 를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 WebException이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-374">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="bf44c-375">-Token</span><span class="sxs-lookup"><span data-stu-id="bf44c-375">-Token</span></span>

<span data-ttu-id="bf44c-376">요청에 포함할 OAuth 또는 전달자 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-376">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="bf44c-377">**토큰** 은 특정 **인증** 옵션에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-377">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="bf44c-378">독립적으로 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-378">It cannot be used independently.</span></span>

<span data-ttu-id="bf44c-379">**토큰** 은 토큰을 포함 하는을 사용 `SecureString` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-379">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="bf44c-380">토큰을 수동으로 제공 하려면 다음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-380">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="bf44c-381">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-381">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="bf44c-382">-전송자 인코딩</span><span class="sxs-lookup"><span data-stu-id="bf44c-382">-TransferEncoding</span></span>

<span data-ttu-id="bf44c-383">transfer-encoding HTTP 응답 헤더의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-383">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="bf44c-384">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-384">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bf44c-385">청크</span><span class="sxs-lookup"><span data-stu-id="bf44c-385">Chunked</span></span>
- <span data-ttu-id="bf44c-386">압축</span><span class="sxs-lookup"><span data-stu-id="bf44c-386">Compress</span></span>
- <span data-ttu-id="bf44c-387">Deflate</span><span class="sxs-lookup"><span data-stu-id="bf44c-387">Deflate</span></span>
- <span data-ttu-id="bf44c-388">GZip</span><span class="sxs-lookup"><span data-stu-id="bf44c-388">GZip</span></span>
- <span data-ttu-id="bf44c-389">ID</span><span class="sxs-lookup"><span data-stu-id="bf44c-389">Identity</span></span>

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

### <span data-ttu-id="bf44c-390">-Uri</span><span class="sxs-lookup"><span data-stu-id="bf44c-390">-Uri</span></span>

<span data-ttu-id="bf44c-391">웹 요청이 전송 되는 인터넷 리소스의 URI (Uniform Resource Identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-391">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="bf44c-392">URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-392">Enter a URI.</span></span> <span data-ttu-id="bf44c-393">이 매개 변수는 HTTP 또는 HTTPS만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-393">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="bf44c-394">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-394">This parameter is required.</span></span> <span data-ttu-id="bf44c-395">매개 변수 이름 **Uri** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-395">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="bf44c-396">-UseBasicParsing 분석</span><span class="sxs-lookup"><span data-stu-id="bf44c-396">-UseBasicParsing</span></span>

<span data-ttu-id="bf44c-397">이 매개 변수는 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-397">This parameter has been deprecated.</span></span> <span data-ttu-id="bf44c-398">PowerShell 6.0.0부터 모든 웹 요청은 기본 구문 분석만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-398">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="bf44c-399">이 매개 변수는 이전 버전과의 호환성을 위해서만 포함 되며 cmdlet의 작업에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-399">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="bf44c-400">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="bf44c-400">-UseDefaultCredentials</span></span>

<span data-ttu-id="bf44c-401">Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 웹 요청을 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-401">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="bf44c-402">이는 **인증** 또는 **자격 증명과** 함께 사용할 수 없으며, 일부 플랫폼에서 지원 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-402">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="bf44c-403">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="bf44c-403">-UserAgent</span></span>

<span data-ttu-id="bf44c-404">웹 요청에 대한 사용자 에이전트 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-404">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="bf44c-405">기본 사용자 에이전트는 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 각 운영 체제 및 플랫폼에 대해 약간 변형 된와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-405">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="bf44c-406">대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, InternetExplorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 클래스의 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-406">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="bf44c-407">예를 들어 다음 명령은 Internet Explorer에 대 한 사용자 에이전트 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-407">For example, the following command uses the user agent string for Internet Explorer:</span></span>

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

### <span data-ttu-id="bf44c-408">-WebSession</span><span class="sxs-lookup"><span data-stu-id="bf44c-408">-WebSession</span></span>

<span data-ttu-id="bf44c-409">웹 요청 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-409">Specifies a web request session.</span></span> <span data-ttu-id="bf44c-410">달러 기호 ()를 포함 하 여 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-410">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="bf44c-411">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-411">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="bf44c-412">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-412">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="bf44c-413">`Content-Type` **본문** 에 대해 **MultipartFormDataContent** 개체를 제공 하는 경우와 같은 콘텐츠 관련 헤더만 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-413">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="bf44c-414">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-414">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="bf44c-415">쿠키, 자격 증명, 최대 리디렉션 값 및 사용자 에이전트 문자열을 포함 하 여 연결 및 요청에 대 한 정보를 포함 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-415">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="bf44c-416">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-416">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="bf44c-417">웹 요청 세션을 만들려면 명령의 **Sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-WebRequest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-417">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="bf44c-418">`Invoke-WebRequest` 세션을 만들어 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-418">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="bf44c-419">후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-419">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="bf44c-420">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-420">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf44c-421">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf44c-421">CommonParameters</span></span>

<span data-ttu-id="bf44c-422">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bf44c-422">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf44c-423">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf44c-423">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf44c-424">입력</span><span class="sxs-lookup"><span data-stu-id="bf44c-424">INPUTS</span></span>

### <span data-ttu-id="bf44c-425">System.Object</span><span class="sxs-lookup"><span data-stu-id="bf44c-425">System.Object</span></span>

<span data-ttu-id="bf44c-426">웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="bf44c-426">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="bf44c-427">출력</span><span class="sxs-lookup"><span data-stu-id="bf44c-427">OUTPUTS</span></span>

### <span data-ttu-id="bf44c-428">Microsoft. PowerShell. BasicHtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="bf44c-428">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="bf44c-429">참고</span><span class="sxs-lookup"><span data-stu-id="bf44c-429">NOTES</span></span>

<span data-ttu-id="bf44c-430">PowerShell 6.0.0 부터는 `Invoke-WebRequest` 기본 구문 분석만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-430">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="bf44c-431">자세한 내용은 [Basichtmlwebresponseobject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf44c-431">For more information, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="bf44c-432">.NET Core 3.1의 변경 내용으로 인해 PowerShell 7.0 이상에서는 [Httpclient. defaultproxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 속성을 사용 하 여 프록시 구성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-432">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) Property to determine the proxy configuration.</span></span>

<span data-ttu-id="bf44c-433">이 속성의 값은 플랫폼에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-433">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="bf44c-434">**Windows의 경우**: 환경 변수에서 프록시 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-434">**For Windows**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="bf44c-435">이러한 변수가 정의 되지 않은 경우 속성은 사용자의 프록시 설정에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-435">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="bf44c-436">**MacOS의 경우**: 환경 변수에서 프록시 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-436">**For macOS**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="bf44c-437">이러한 변수가 정의 되지 않은 경우 속성은 시스템의 프록시 설정에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-437">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="bf44c-438">**Linux**: 환경 변수에서 프록시 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-438">**For Linux**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="bf44c-439">이러한 변수가 정의 되지 않은 경우 속성은 모든 주소를 우회 하는 구성 되지 않은 인스턴스를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-439">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="bf44c-440">`DefaultProxy`Windows 및 Unix 기반 플랫폼에서 초기화 하는 데 사용 되는 환경 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-440">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="bf44c-441">` HTTP_PROXY`: HTTP 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-441">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="bf44c-442">`HTTPS_PROXY`: HTTPS 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-442">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="bf44c-443">`ALL_PROXY`: 또는의 경우 HTTP 및 HTTPS 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소를 `HTTP_PROXY` `HTTPS_PROXY` 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-443">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="bf44c-444">`NO_PROXY`: 프록시에서 제외 되어야 하는 쉼표로 구분 된 호스트 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="bf44c-444">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="bf44c-445">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bf44c-445">RELATED LINKS</span></span>

[<span data-ttu-id="bf44c-446">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="bf44c-446">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="bf44c-447">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="bf44c-447">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="bf44c-448">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="bf44c-448">ConvertTo-Json</span></span>](ConvertTo-Json.md)
