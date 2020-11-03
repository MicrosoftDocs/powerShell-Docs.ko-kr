---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: aab7ae73d223f349fc0c103332331710a3eb2efe
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210018"
---
# <span data-ttu-id="38f25-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="38f25-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="38f25-104">개요</span><span class="sxs-lookup"><span data-stu-id="38f25-104">SYNOPSIS</span></span>
<span data-ttu-id="38f25-105">HTTP 또는 HTTPS 요청을 RESTful 웹 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="38f25-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="38f25-106">SYNTAX</span></span>

### <span data-ttu-id="38f25-107">StandardMethod (기본값)</span><span class="sxs-lookup"><span data-stu-id="38f25-107">StandardMethod (Default)</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="38f25-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="38f25-108">StandardMethodNoProxy</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="38f25-109">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="38f25-109">CustomMethodNoProxy</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="38f25-110">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="38f25-110">CustomMethod</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="38f25-111">Description</span><span class="sxs-lookup"><span data-stu-id="38f25-111">Description</span></span>

<span data-ttu-id="38f25-112">Cmdlet은 다양 `Invoke-RestMethod` 한 구조화 된 데이터를 반환 하는 REST (Representational State Transfer) 웹 서비스로 HTTP 및 HTTPS 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-112">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="38f25-113">PowerShell은 데이터 형식에 따라 응답의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-113">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="38f25-114">RSS 또는 ATOM 피드의 경우 PowerShell에서 항목 또는 항목 XML 노드를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-114">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="38f25-115">JSON (JavaScript Object Notation) 또는 XML의 경우 PowerShell은 콘텐츠를 개체로 변환 하거나 deserialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-115">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into objects.</span></span>

<span data-ttu-id="38f25-116">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-116">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="38f25-117">PowerShell 7.0부터는 `Invoke-RestMethod` 환경 변수에 의해 정의 된 프록시 구성을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-117">Beginning in PowerShell 7.0, `Invoke-RestMethod` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="38f25-118">이 문서의 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f25-118">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="38f25-119">예제</span><span class="sxs-lookup"><span data-stu-id="38f25-119">EXAMPLES</span></span>

### <span data-ttu-id="38f25-120">예제 1: PowerShell RSS 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="38f25-120">Example 1: Get the PowerShell RSS feed</span></span>

<span data-ttu-id="38f25-121">이 예제에서는 cmdlet을 사용 하 여 `Invoke-RestMethod` PowerShell 블로그 RSS 피드에서 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-121">This example uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="38f25-122">이 명령은 cmdlet을 사용 하 여 `Format-Table` 각 블로그의 **Title** 및 **pubDate** 속성 값을 테이블에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-122">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

```powershell
Invoke-RestMethod -Uri https://blogs.msdn.microsoft.com/powershell/feed/ |
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

### <span data-ttu-id="38f25-123">예제 2: POST 요청 실행</span><span class="sxs-lookup"><span data-stu-id="38f25-123">Example 2: Run a POST request</span></span>

<span data-ttu-id="38f25-124">이 예제에서는 사용자가를 실행 `Invoke-RestMethod` 하 여 사용자 조직의 인트라넷 웹 사이트에서 POST 요청을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-124">In this example, a user runs `Invoke-RestMethod` to do a POST request on an intranet website in the user's organization.</span></span>

```powershell
$Cred = Get-Credential
$Url = "https://server.contoso.com:8089/services/search/jobs/export"
$Body = @{
    search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}
Invoke-RestMethod -Method 'Post' -Uri $url -Credential $Cred -Body $body -OutFile output.csv
```

<span data-ttu-id="38f25-125">자격 증명을 입력 하 라는 메시지가 표시 된 다음에 저장 `$Cred` 되 고 액세스 되는 URL이에 정의 됩니다 `$Url` .</span><span class="sxs-lookup"><span data-stu-id="38f25-125">The credentials are prompted for and then stored in `$Cred` and the URL that will be access is defined in `$Url`.</span></span>

<span data-ttu-id="38f25-126">`$Body`변수는 검색 조건을 설명 하 고, CSV를 출력 모드로 지정 하 고, 반환 된 데이터에 대 한 기간을 지정 하 여 2 일 전에 시작 하 고 하루 전 종료 합니다</span><span class="sxs-lookup"><span data-stu-id="38f25-126">The `$Body` variable describes the search criteria, specifies CSV as the output mode, and specifies a time period for returned data that starts two days ago and ends one day ago.</span></span> <span data-ttu-id="38f25-127">Body 변수는와 관련 된 특정 REST API에 적용 되는 매개 변수의 값을 지정 합니다 `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="38f25-127">The body variable specifies values for parameters that apply to the particular REST API with which `Invoke-RestMethod` is communicating.</span></span>

<span data-ttu-id="38f25-128">`Invoke-RestMethod`명령은 결과 CSV 출력 파일의 경로와 파일 이름을 지정 하 여 모든 변수를 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-128">The `Invoke-RestMethod` command is run with all variables in place, specifying a path and file name for the resulting CSV output file.</span></span>

### <span data-ttu-id="38f25-129">예제 3: 관계 링크 따르기</span><span class="sxs-lookup"><span data-stu-id="38f25-129">Example 3: Follow relation links</span></span>

<span data-ttu-id="38f25-130">일부 REST Api는 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)별 관계 링크를 통해 페이지 매김을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-130">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="38f25-131">헤더를 구문 분석 하 여 다음 페이지에 대 한 URL을 가져오는 대신 cmdlet을 통해이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-131">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="38f25-132">이 예에서는 PowerShell GitHub 리포지토리에서 처음 두 개의 문제 페이지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-132">This example returns the first two pages of issues from the PowerShell GitHub repository.</span></span>

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### <span data-ttu-id="38f25-133">예제 4: 간소화 된 다중 파트/양식 데이터 전송</span><span class="sxs-lookup"><span data-stu-id="38f25-133">Example 4: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="38f25-134">일부 Api는 `multipart/form-data` 파일 및 혼합 콘텐츠를 업로드 하는 데 제출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-134">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="38f25-135">이 예제에서는 사용자의 프로필을 업데이트 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-135">This example demonstrates how to update a user's profile.</span></span>

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
$Result = Invoke-RestMethod -Uri $Uri -Method Post -Form $Form
```

<span data-ttu-id="38f25-136">프로필 양식에는,,,, `firstName` `lastName` `email` `avatar` `birthday` 및 `hobbies` 필드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-136">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="38f25-137">API는 필드에 사용자 프로필 pic를 제공 하기 위한 이미지가 필요 `avatar` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-137">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="38f25-138">또한 API는 `hobbies` 동일한 형식으로 제출할 여러 항목을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-138">The API will also accept multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="38f25-139">`$Form`해시 테이블을 만들 때 키 이름이 폼 필드 이름으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-139">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="38f25-140">기본적으로 해시 테이블의 값은 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-140">By default, the values of the HashTable will be converted to strings.</span></span> <span data-ttu-id="38f25-141">`System.IO.FileInfo`값이 있으면 파일 내용이 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-141">If a `System.IO.FileInfo` value is present, the file contents will be submitted.</span></span> <span data-ttu-id="38f25-142">배열 또는 목록과 같은 컬렉션이 있으면 폼 필드가 여러 번 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-142">If a collection such as arrays or lists are present, the form field will be submitted multiple times.</span></span>

<span data-ttu-id="38f25-143">`Get-Item`키에서를 사용 하면 `avatar` `FileInfo` 개체가 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-143">By using `Get-Item` on the `avatar` key, the `FileInfo` object will be set as the value.</span></span> <span data-ttu-id="38f25-144">그 결과의 이미지 데이터가 `jdoe.png` 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-144">The result is that the image data for `jdoe.png` will be submitted.</span></span>

<span data-ttu-id="38f25-145">키에 목록을 제공 하면 `hobbies` `hobbies` 필드는 각 목록 항목에 대해 한 번씩 제출에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-145">By supplying a list to the `hobbies` key, the `hobbies` field will be present in the submissions once for each list item.</span></span>

### <span data-ttu-id="38f25-146">예 5: 여러 헤더 전달</span><span class="sxs-lookup"><span data-stu-id="38f25-146">Example 5: Pass multiple headers</span></span>

<span data-ttu-id="38f25-147">Api는 인증 또는 유효성 검사를 위해 헤더를 전달 해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-147">APIs often require passed headers for authentication or validation.</span></span> <span data-ttu-id="38f25-148">이 예제에서는에서 REST API 여러 헤더를 전달 하는 방법을 보여 줍니다 `hash-table` .</span><span class="sxs-lookup"><span data-stu-id="38f25-148">This example demonstrates, how to pass multiple headers from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## <span data-ttu-id="38f25-149">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38f25-149">Parameters</span></span>

### <span data-ttu-id="38f25-150">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="38f25-150">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="38f25-151">암호화 되지 않은 연결을 통해 자격 증명과 암호를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-151">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="38f25-152">기본적으로로 시작 하지 않는 **Uri** 를 사용 하 여 **자격 증명** 을 제공 하거나 **인증** 옵션을 제공 하면 `https://` 오류가 발생 하 고 암호화 되지 않은 연결을 통해 암호가 일반 텍스트로 전달 되지 않도록 요청이 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-152">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` will result in an error and the request will abort to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="38f25-153">사용자의 위험에 따라이 동작을 재정의 하려면 **Allowunencryptedauthentication** 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-153">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="38f25-154">이 매개 변수를 사용 하는 것은 안전 하지 않으므로 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-154">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="38f25-155">암호화 된 연결을 제공할 수 없는 레거시 시스템과의 호환성을 위해서만 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-155">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="38f25-156">사용자의 위험에 따라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-156">Use at your own risk.</span></span>

<span data-ttu-id="38f25-157">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-157">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-158">-인증</span><span class="sxs-lookup"><span data-stu-id="38f25-158">-Authentication</span></span>

<span data-ttu-id="38f25-159">요청에 사용할 명시적 인증 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-159">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="38f25-160">기본값은 **None** (없음)입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-160">The default is **None** .</span></span>
<span data-ttu-id="38f25-161">**인증은** **UseDefaultCredentials** 와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-161">**Authentication** can't be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="38f25-162">사용 가능한 인증 옵션:</span><span class="sxs-lookup"><span data-stu-id="38f25-162">Available Authentication Options:</span></span>

- <span data-ttu-id="38f25-163">**None** : **인증이** 제공 되지 않은 경우의 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-163">**None** : This is the default option when **Authentication** is not supplied.</span></span> <span data-ttu-id="38f25-164">명시적 인증을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-164">No explicit authentication will be used.</span></span>
- <span data-ttu-id="38f25-165">**기본** : **자격 증명이** 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-165">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="38f25-166">자격 증명은 RFC 7617 기본 인증 헤더를 형식으로 전송 하는 데 사용 됩니다 `Authorization: Basic` `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="38f25-166">The credentials will be used to send an RFC 7617 Basic Authentication `Authorization: Basic` header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="38f25-167">**전달자** : **토큰이** 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-167">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="38f25-168">는 제공 된 토큰과 함께 및 RFC 6750 헤더를 전송 `Authorization: Bearer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-168">Will send and RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="38f25-169">**OAuth** 에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-169">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="38f25-170">**OAuth** : **토큰이** 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-170">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="38f25-171">는 `Authorization: Bearer` 제공 된 토큰을 사용 하 여 RFC 6750 헤더를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-171">Will send an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="38f25-172">**전달자** 에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-172">This is an alias for **Bearer**</span></span>

<span data-ttu-id="38f25-173">**인증** 을 제공 하면 `Authorization` **헤더** 에 제공 되거나 **websession** 에 포함 된 모든 헤더가 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-173">Supplying **Authentication** will override any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="38f25-174">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-175">-본문</span><span class="sxs-lookup"><span data-stu-id="38f25-175">-Body</span></span>

<span data-ttu-id="38f25-176">요청의 본문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-176">Specifies the body of the request.</span></span> <span data-ttu-id="38f25-177">본문은 헤더 뒤에 오는 요청 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-177">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="38f25-178">본문 값을로 파이프 할 수도 있습니다 `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="38f25-178">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="38f25-179">**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-179">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="38f25-180">입력이 GET 요청이 고 본문이 `IDictionary` (일반적으로 해시 테이블) 이면 본문이 쿼리 매개 변수로 URI (Uniform Resource Identifier)에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-180">When the input is a GET request, and the body is an `IDictionary` (typically, a hash table), the body is added to the Uniform Resource Identifier (URI) as query parameters.</span></span> <span data-ttu-id="38f25-181">다른 요청 유형(예: POST)의 경우 본문이 표준 이름=값 형식의 요청 본문 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-181">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

<span data-ttu-id="38f25-182">본문이 폼 이거나 다른 호출의 출력 인 경우 `Invoke-WebRequest` PowerShell은 양식 필드에 요청 콘텐츠를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-182">When the body is a form, or it's the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="38f25-183">**Body** 매개 변수는 **시스템 MultipartFormDataContent** 개체를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-183">The **Body** parameter may also accept a **System.Net.Http.MultipartFormDataContent** object.</span></span> <span data-ttu-id="38f25-184">그러면 요청을 쉽게 수행할 수 `multipart/form-data` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-184">This will facilitate `multipart/form-data` requests.</span></span> <span data-ttu-id="38f25-185">**본문** 에 대해 **MultipartFormDataContent** 개체가 제공 되 면 **ContentType** , **헤더** 또는 **websession** 매개 변수에 제공 된 콘텐츠 관련 헤더가 개체의 콘텐츠 헤더로 재정의 됩니다 `MultipartFormDataContent` .</span><span class="sxs-lookup"><span data-stu-id="38f25-185">When a **MultipartFormDataContent** object is supplied for **Body** , any content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters will be overridden by the content headers of the `MultipartFormDataContent` object.</span></span> <span data-ttu-id="38f25-186">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-186">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-187">-인증서</span><span class="sxs-lookup"><span data-stu-id="38f25-187">-Certificate</span></span>

<span data-ttu-id="38f25-188">보안 웹 요청에 사용되는 클라이언트 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-188">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="38f25-189">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-189">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="38f25-190">인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 () 드라이브에서 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-190">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="38f25-191">인증서가 유효 하지 않거나 권한이 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-191">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="38f25-192">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="38f25-192">-CertificateThumbprint</span></span>

<span data-ttu-id="38f25-193">요청을 보낼 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-193">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="38f25-194">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-194">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="38f25-195">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-195">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="38f25-196">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-196">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="38f25-197">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-197">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="38f25-198">이 기능은 현재 Windows OS 플랫폼 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-198">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="38f25-199">-ContentType</span><span class="sxs-lookup"><span data-stu-id="38f25-199">-ContentType</span></span>

<span data-ttu-id="38f25-200">웹 요청의 콘텐츠 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-200">Specifies the content type of the web request.</span></span>

<span data-ttu-id="38f25-201">이 매개 변수를 생략 하 고 요청 메서드를 POST로 `Invoke-RestMethod` 설정 하면에서 콘텐츠 형식을로 설정 합니다 `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="38f25-201">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="38f25-202">그렇지 않으면 호출에서 콘텐츠 형식이 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-202">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="38f25-203">**ContentType** `MultipartFormDataContent` 개체를 **본문** 에 제공 하면 ContentType이 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-203">**ContentType** will be overridden when a `MultipartFormDataContent` object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="38f25-204">-Credential</span><span class="sxs-lookup"><span data-stu-id="38f25-204">-Credential</span></span>

<span data-ttu-id="38f25-205">요청을 보낼 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-205">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="38f25-206">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-206">The default is the current user.</span></span>

<span data-ttu-id="38f25-207">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="38f25-207">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="38f25-208">**자격 증명** 은 단독으로 사용 하거나 특정 **인증** 매개 변수 옵션과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-208">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="38f25-209">단독으로 사용 하는 경우 원격 서버에서 인증 챌린지 요청을 보내는 경우에만 원격 서버에 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-209">When used alone, it will only supply credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="38f25-210">**인증** 옵션과 함께 사용 하는 경우 자격 증명이 명시적으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-210">When used with **Authentication** options, the credentials will be explicitly sent.</span></span>

<span data-ttu-id="38f25-211">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-211">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="38f25-212">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="38f25-212">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="38f25-213">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="38f25-213">-CustomMethod</span></span>

<span data-ttu-id="38f25-214">웹 요청에 사용 되는 사용자 지정 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-214">Specifies custom method used for the web request.</span></span> <span data-ttu-id="38f25-215">이 **메서드** 는 끝점에 필요한 요청 메서드와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-215">This can be used with the Request Method required by the endpoint is not an available option on the **Method** .</span></span> <span data-ttu-id="38f25-216">**메서드** 및 **custommethod** 는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-216">**Method** and **CustomMethod** cannot be used together.</span></span>

<span data-ttu-id="38f25-217">예제:</span><span class="sxs-lookup"><span data-stu-id="38f25-217">Example:</span></span>

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="38f25-218">그러면 `TEST` API에 대 한 HTTP 요청이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-218">This makes a `TEST` HTTP request to the API.</span></span>

<span data-ttu-id="38f25-219">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-219">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-220">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="38f25-220">-DisableKeepAlive</span></span>

<span data-ttu-id="38f25-221">Cmdlet이 HTTP 헤더의 **KeepAlive** 값을 False로 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-221">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="38f25-222">기본적으로 **KeepAlive** 는 True입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-222">By default, **KeepAlive** is True.</span></span> <span data-ttu-id="38f25-223">**KeepAlive** 는 후속 요청의 신속한 처리를 위해 서버에 대한 영구 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-223">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="38f25-224">-양방향 링크</span><span class="sxs-lookup"><span data-stu-id="38f25-224">-FollowRelLink</span></span>

<span data-ttu-id="38f25-225">Cmdlet이 관계 링크를 따르도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-225">Indicates the cmdlet should follow relation links.</span></span>

<span data-ttu-id="38f25-226">일부 REST Api는 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)별 관계 링크를 통해 페이지 매김을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-226">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="38f25-227">헤더를 구문 분석 하 여 다음 페이지에 대 한 URL을 가져오는 대신 cmdlet을 통해이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-227">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="38f25-228">관계 링크를 수행할 횟수를 설정 하려면 **maximum휴먼 추가 링크** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-228">To set how many times to follow relation links, use the **MaximumFollowRelLink** parameter.</span></span>

<span data-ttu-id="38f25-229">이 스위치를 사용 하는 경우 cmdlet은 결과 페이지의 컬렉션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-229">When using this switch, the cmdlet returns a collection of pages of results.</span></span> <span data-ttu-id="38f25-230">결과의 각 페이지에는 여러 결과 항목이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-230">Each page of results may contain multiple result items.</span></span>

<span data-ttu-id="38f25-231">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-231">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: FL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38f25-232">-폼</span><span class="sxs-lookup"><span data-stu-id="38f25-232">-Form</span></span>

<span data-ttu-id="38f25-233">사전을 제출으로 변환 `multipart/form-data` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-233">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="38f25-234">**폼** 은 **본문과** 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-234">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="38f25-235">**ContentType** 이 무시 되 면입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-235">If **ContentType** will be ignored.</span></span>

<span data-ttu-id="38f25-236">사전의 키는 양식 필드 이름으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-236">The keys of the dictionary will be used as the form field names.</span></span> <span data-ttu-id="38f25-237">기본적으로 양식 값은 문자열 값으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-237">By default, form values will be converted to string values.</span></span>

<span data-ttu-id="38f25-238">값이 **system.object** 이면 이진 파일 내용이 전송 됩니다 .이 개체는입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-238">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span>
<span data-ttu-id="38f25-239">파일의 이름은로 제출 됩니다 `filename` .</span><span class="sxs-lookup"><span data-stu-id="38f25-239">The name of the file will be submitted as the `filename`.</span></span> <span data-ttu-id="38f25-240">MIME은로 설정 됩니다 `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="38f25-240">The MIME will be set as `application/octet-stream`.</span></span> <span data-ttu-id="38f25-241">`Get-Item` 는 **system.object** 를 제공 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-241">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="38f25-242">값이 배열 또는 목록과 같은 컬렉션 형식인 경우 for 필드는 여러 번 제출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-242">If the value is a collection type, such as an Array or List, the for field will be submitted multiple times.</span></span> <span data-ttu-id="38f25-243">목록의 값은 기본적으로 문자열로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-243">The values of the list will be treated as strings by default.</span></span> <span data-ttu-id="38f25-244">값이 **system.object** 이면 이진 파일 내용이 전송 됩니다 .이 개체는입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-244">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span> <span data-ttu-id="38f25-245">중첩 컬렉션은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-245">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="38f25-246">위의 예제에서 `tags` 필드는 각, 및에 대해 한 번씩 폼에서 세 번 제공 됩니다 `Vacation` `Italy` `2017` .</span><span class="sxs-lookup"><span data-stu-id="38f25-246">In the above example, the `tags` field will be supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="38f25-247">`pictures`또한이 필드는 폴더의 각 파일에 대해 한 번씩 제출 됩니다 `2017-Italy` .</span><span class="sxs-lookup"><span data-stu-id="38f25-247">The `pictures` field will also be submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="38f25-248">해당 폴더에 있는 파일의 이진 내용이 값으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-248">The binary contents of the files in that folder will be submitted as the values.</span></span>

<span data-ttu-id="38f25-249">이 기능은 PowerShell 6.1.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-249">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="38f25-250">-헤더</span><span class="sxs-lookup"><span data-stu-id="38f25-250">-Headers</span></span>

<span data-ttu-id="38f25-251">웹 요청의 헤더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-251">Specifies the headers of the web request.</span></span> <span data-ttu-id="38f25-252">해시 테이블 또는 사전을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-252">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="38f25-253">UserAgent 헤더를 설정하려면 **UserAgent** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-253">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="38f25-254">이 매개 변수를 사용 하 여 `User-Agent` 또는 쿠키 헤더를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-254">You cannot use this parameter to specify `User-Agent` or cookie headers.</span></span>

<span data-ttu-id="38f25-255">`Content-Type` `MultipartFormDataContent` 개체를 **본문** 에 제공 하면와 같은 콘텐츠 관련 헤더가 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-255">Content related headers, such as `Content-Type` will be overridden when a `MultipartFormDataContent` object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="38f25-256">-InFile</span><span class="sxs-lookup"><span data-stu-id="38f25-256">-InFile</span></span>

<span data-ttu-id="38f25-257">파일에서 웹 요청의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-257">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="38f25-258">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-258">Enter a path and file name.</span></span> <span data-ttu-id="38f25-259">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-259">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="38f25-260">-Maximum 링크</span><span class="sxs-lookup"><span data-stu-id="38f25-260">-MaximumFollowRelLink</span></span>

<span data-ttu-id="38f25-261">다음 **링크** 를 사용 하는 경우 관계 링크를 수행할 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-261">Specifies how many times to follow relation links if **FollowRelLink** is used.</span></span> <span data-ttu-id="38f25-262">REST api가 너무 많은 요청으로 인해 제한 하는 경우에는 더 작은 값이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-262">A smaller value may be needed if the REST api throttles due to too many requests.</span></span> <span data-ttu-id="38f25-263">기본값은 `[Int32]::MaxValue`입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-263">The default value is `[Int32]::MaxValue`.</span></span> <span data-ttu-id="38f25-264">값이 0 이면 다음 관계 링크를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-264">A value of 0 (zero) prevents following relation links.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ML

Required: False
Position: Named
Default value: Int32.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38f25-265">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="38f25-265">-MaximumRedirection</span></span>

<span data-ttu-id="38f25-266">연결에 실패 하기 전에 PowerShell이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션하는 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-266">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="38f25-267">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-267">The default value is 5.</span></span> <span data-ttu-id="38f25-268">값 0은 모든 리디렉션을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-268">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="38f25-269">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="38f25-269">-MaximumRetryCount</span></span>

<span data-ttu-id="38f25-270">400과 599 사이의 오류 코드를 수신 하는 경우 PowerShell에서 연결을 다시 시도 하는 횟수 304를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-270">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="38f25-271">다시 시도 횟수를 지정 하는 **RetryIntervalSec** 매개 변수도 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f25-271">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="38f25-272">-메서드</span><span class="sxs-lookup"><span data-stu-id="38f25-272">-Method</span></span>

<span data-ttu-id="38f25-273">웹 요청에 사용되는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-273">Specifies the method used for the web request.</span></span> <span data-ttu-id="38f25-274">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-274">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="38f25-275">기본값</span><span class="sxs-lookup"><span data-stu-id="38f25-275">Default</span></span>
- <span data-ttu-id="38f25-276">DELETE</span><span class="sxs-lookup"><span data-stu-id="38f25-276">Delete</span></span>
- <span data-ttu-id="38f25-277">가져오기</span><span class="sxs-lookup"><span data-stu-id="38f25-277">Get</span></span>
- <span data-ttu-id="38f25-278">Head</span><span class="sxs-lookup"><span data-stu-id="38f25-278">Head</span></span>
- <span data-ttu-id="38f25-279">병합</span><span class="sxs-lookup"><span data-stu-id="38f25-279">Merge</span></span>
- <span data-ttu-id="38f25-280">옵션</span><span class="sxs-lookup"><span data-stu-id="38f25-280">Options</span></span>
- <span data-ttu-id="38f25-281">패치</span><span class="sxs-lookup"><span data-stu-id="38f25-281">Patch</span></span>
- <span data-ttu-id="38f25-282">게시</span><span class="sxs-lookup"><span data-stu-id="38f25-282">Post</span></span>
- <span data-ttu-id="38f25-283">Put</span><span class="sxs-lookup"><span data-stu-id="38f25-283">Put</span></span>
- <span data-ttu-id="38f25-284">추적</span><span class="sxs-lookup"><span data-stu-id="38f25-284">Trace</span></span>

<span data-ttu-id="38f25-285">**Custommethod** 매개 변수는 위에 나열 되지 않은 요청 메서드에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-285">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="38f25-286">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="38f25-286">-NoProxy</span></span>

<span data-ttu-id="38f25-287">Cmdlet이 대상에 연결 하는 데 프록시를 사용 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-287">Indicates that the cmdlet will not use a proxy to reach the destination.</span></span>

<span data-ttu-id="38f25-288">Internet Explorer에서 구성 된 프록시를 사용 하지 않거나 환경에 지정 된 프록시를 사용 하지 않으려면이 스위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-288">When you need to bypass the proxy configured in Internet Explorer, or a proxy specified in the environment, use this switch.</span></span>

<span data-ttu-id="38f25-289">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-289">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="38f25-290">-출력</span><span class="sxs-lookup"><span data-stu-id="38f25-290">-OutFile</span></span>

<span data-ttu-id="38f25-291">응답 본문을 지정한 출력 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-291">Saves the response body in the specified output file.</span></span> <span data-ttu-id="38f25-292">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-292">Enter a path and file name.</span></span> <span data-ttu-id="38f25-293">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-293">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="38f25-294">기본적으로는 `Invoke-RestMethod` 결과를 파이프라인으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-294">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="38f25-295">결과를 파일과 파이프라인으로 보내려면 **Passthru** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-295">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="38f25-296">-PassThru</span><span class="sxs-lookup"><span data-stu-id="38f25-296">-PassThru</span></span>

<span data-ttu-id="38f25-297">결과를 반환하고 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-297">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="38f25-298">이 매개 변수는 명령에 **OutFile** 매개 변수도 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-298">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="38f25-299">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="38f25-299">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="38f25-300">Cmdlet이 `Authorization` 리디렉션 전체에 헤더 (있는 경우)를 유지 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-300">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="38f25-301">기본적으로이 cmdlet은 `Authorization` 리디렉션하기 전에 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-301">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="38f25-302">이 매개 변수를 지정 하면 헤더를 리디렉션 위치로 전송 해야 하는 경우에이 논리가 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-302">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="38f25-303">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-303">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-304">-프록시</span><span class="sxs-lookup"><span data-stu-id="38f25-304">-Proxy</span></span>

<span data-ttu-id="38f25-305">인터넷 리소스에 직접 연결 하는 대신 요청에 프록시 서버를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-305">Uses a proxy server for the request, rather than connecting directly to the internet resource.</span></span> <span data-ttu-id="38f25-306">네트워크 프록시 서버의 URI (Uniform Resource Identifier)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-306">Enter the Uniform Resource Identifier (URI) of a network proxy server.</span></span>

<span data-ttu-id="38f25-307">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-307">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-308">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="38f25-308">-ProxyCredential</span></span>

<span data-ttu-id="38f25-309">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-309">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="38f25-310">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-310">The default is the current user.</span></span>

<span data-ttu-id="38f25-311">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 **User@Domain.Com** 하거나 `PSCredential` cmdlet에 의해 생성 된 개체와 같은 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="38f25-311">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="38f25-312">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-312">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="38f25-313">동일한 명령에서 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-313">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38f25-314">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="38f25-314">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="38f25-315">Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 **프록시** 매개 변수로 지정 된 프록시 서버에 액세스 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-315">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="38f25-316">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-316">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="38f25-317">동일한 명령에서 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-317">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="38f25-318">-ResponseHeadersVariable</span><span class="sxs-lookup"><span data-stu-id="38f25-318">-ResponseHeadersVariable</span></span>

<span data-ttu-id="38f25-319">응답 헤더 사전을 만들어 지정 된 변수의 값에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-319">Creates a Response Headers Dictionary and saves it in the value of the specified variable.</span></span> <span data-ttu-id="38f25-320">사전의 키에는 웹 서버에서 반환 하는 응답 헤더의 필드 이름이 포함 되 고 값은 해당 필드 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-320">The keys of the dictionary will contain the field names of the Response Header returned by the web server and the values will be the respective field values.</span></span>

<span data-ttu-id="38f25-321">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-321">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RHV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38f25-322">-Resume</span><span class="sxs-lookup"><span data-stu-id="38f25-322">-Resume</span></span>

<span data-ttu-id="38f25-323">부분 파일 다운로드를 다시 시작 하는 데 가장 적합 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-323">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="38f25-324">**Resume** 매개 변수에는 **출력** 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-324">The **Resume** parameter requires the **OutFile** parameter.</span></span>

<span data-ttu-id="38f25-325">**다시 시작** 은 로컬 파일 및 원격 파일의 크기에 대해서만 작동 하며 로컬 파일과 원격 파일이 동일한 다른 유효성 검사를 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-325">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="38f25-326">로컬 파일 크기가 원격 파일 크기 보다 작은 경우 cmdlet은 파일 다운로드를 다시 시작 하 고 나머지 바이트를 파일의 끝에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-326">If the local file size is smaller than the remote file size, then the cmdlet will attempt to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="38f25-327">로컬 파일 크기가 원격 파일 크기와 같을 경우 아무 작업도 수행 되지 않으며 cmdlet은 다운로드를 이미 완료 한 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-327">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already completed.</span></span>

<span data-ttu-id="38f25-328">로컬 파일 크기가 원격 파일 크기 보다 큰 경우 로컬 파일을 덮어쓰고 전체 원격 파일이 완전히 다시 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-328">If the local file size is larger than the remote file size, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="38f25-329">이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-329">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="38f25-330">원격 서버에서 다운로드 다시 시작을 지원 하지 않는 경우 로컬 파일을 덮어쓰고 전체 원격 파일이 완전히 다시 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-330">If the remote server does not support download resuming, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="38f25-331">이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-331">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="38f25-332">로컬 파일이 없으면 로컬 파일이 생성 되 고 전체 원격 파일이 완전히 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-332">If the local file doesn't exist, then the local file will be created and the entire remote file will be completely downloaded.</span></span> <span data-ttu-id="38f25-333">이 동작은 **다시 시작** 없이 **출력** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-333">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="38f25-334">이 기능은 PowerShell 6.1.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-334">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="38f25-335">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="38f25-335">-RetryIntervalSec</span></span>

<span data-ttu-id="38f25-336">400과 599 사이의 오류 코드 (포함 또는 304)를 받을 때 연결 다시 시도 간격을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-336">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="38f25-337">다시 시도 횟수를 지정 하는 **MaximumRetryCount** 매개 변수도 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f25-337">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="38f25-338">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="38f25-338">-SessionVariable</span></span>

<span data-ttu-id="38f25-339">이 cmdlet이 웹 요청 세션을 만들고 값에 저장 하는 데 사용할 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-339">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="38f25-340">달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-340">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="38f25-341">세션 변수를 지정 하면에서 `Invoke-RestMethod` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-341">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="38f25-342">명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-342">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="38f25-343">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-343">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="38f25-344">쿠키, 자격 증명, 최대 리디렉션 값 및 사용자 에이전트 문자열을 포함 하 여 연결 및 요청에 대 한 정보를 포함 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-344">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="38f25-345">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-345">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="38f25-346">후속 웹 요청에서 웹 요청 세션을 사용하려면 **WebSession** 매개 변수 값에 세션 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-346">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="38f25-347">PowerShell은 새 연결을 설정할 때 웹 요청 세션 개체의 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-347">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="38f25-348">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-348">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="38f25-349">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-349">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="38f25-350">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-350">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="38f25-351">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="38f25-351">-SkipCertificateCheck</span></span>

<span data-ttu-id="38f25-352">만료, 해지, 신뢰할 수 있는 루트 인증 기관 등의 모든 유효성 검사를 포함 하는 인증서 유효성 검사를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-352">Skips certificate validation checks that include all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="38f25-353">이 매개 변수를 사용 하는 것은 안전 하지 않으므로 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-353">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="38f25-354">이 스위치는 테스트 목적으로 자체 서명 된 인증서를 사용 하는 알려진 호스트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-354">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="38f25-355">사용자의 위험에 따라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-355">Use at your own risk.</span></span>

<span data-ttu-id="38f25-356">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-356">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-357">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="38f25-357">-SkipHeaderValidation</span></span>

<span data-ttu-id="38f25-358">Cmdlet이 유효성 검사 없이 요청에 헤더를 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-358">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="38f25-359">이 스위치는 표준을 준수 하지 않는 헤더 값이 필요한 사이트에 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-359">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="38f25-360">이 스위치를 지정 하면 해당 값을 선택 하지 않은 상태로 전달할 수 있도록 유효성 검사가 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-360">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="38f25-361">지정 된 경우 모든 헤더는 유효성 검사 없이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-361">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="38f25-362">이렇게 하면 **ContentType** , **Headers** 및 **UserAgent** 매개 변수에 전달 된 값에 대 한 유효성 검사가 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-362">This will disable validation for values passed to the **ContentType** , **Headers** , and **UserAgent** parameters.</span></span>

<span data-ttu-id="38f25-363">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-363">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-364">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="38f25-364">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="38f25-365">이 매개 변수를 설정 하면 cmdlet이 HTTP 오류 상태를 무시 하 고 응답을 계속 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-365">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="38f25-366">오류 응답은 성공 하는 것 처럼 파이프라인에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-366">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="38f25-367">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-367">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="38f25-368">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="38f25-368">-SslProtocol</span></span>

<span data-ttu-id="38f25-369">웹 요청에 허용 되는 SSL/TLS 프로토콜을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-369">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="38f25-370">기본적으로 시스템에서 지원 되는 SSL/TLS 프로토콜은 모두 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-370">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="38f25-371">**Sslprotocol** 은 규정 준수를 위해 특정 프로토콜을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-371">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="38f25-372">**Sslprotocol** 은 플래그 열거형을 사용 합니다 `WebSslProtocol` .</span><span class="sxs-lookup"><span data-stu-id="38f25-372">**SslProtocol** uses the `WebSslProtocol` Flag Enum.</span></span> <span data-ttu-id="38f25-373">플래그 표기법을 사용 하거나 여러 옵션을와 결합 하 여 둘 이상의 프로토콜을 제공할 수 있지만 `WebSslProtocol` `-bor` , 여러 프로토콜을 제공 하는 것은 모든 플랫폼에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-373">It is possible to supply more than one protocol using flag notation or combining multiple `WebSslProtocol` options with `-bor`, however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="38f25-374">Windows가 아닌 플랫폼에서는 옵션으로 제공 하지 못할 수 있습니다 `'Tls, Tls12'` .</span><span class="sxs-lookup"><span data-stu-id="38f25-374">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="38f25-375">이 기능은 PowerShell 6.0.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-375">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="38f25-376">-StatusCodeVariable</span><span class="sxs-lookup"><span data-stu-id="38f25-376">-StatusCodeVariable</span></span>

<span data-ttu-id="38f25-377">이 매개 변수는 상태 코드의 정수 값이 할당 된 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-377">This parameter specifies a variable that's assigned a status code's integer value.</span></span> <span data-ttu-id="38f25-378">매개 변수는 **SkipHttpErrorCheck** 매개 변수와 함께 사용할 경우 성공 메시지 또는 오류 메시지를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-378">The parameter can identify success messages or failure messages when used with the **SkipHttpErrorCheck** parameter.</span></span>

<span data-ttu-id="38f25-379">매개 변수의 변수 이름을와 같은 문자열로 입력 합니다 `-StatusCodeVariable "scv"` .</span><span class="sxs-lookup"><span data-stu-id="38f25-379">Input the parameter's variable name as a string such as `-StatusCodeVariable "scv"`.</span></span>

<span data-ttu-id="38f25-380">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-380">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38f25-381">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="38f25-381">-TimeoutSec</span></span>

<span data-ttu-id="38f25-382">시간이 초과 되기 전에 요청이 보류 될 수 있는 기간을 지정 합니다. 초 단위로 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-382">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="38f25-383">기본값 0은 무기한 시간 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-383">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="38f25-384">DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 **Timeoutsec** 를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 WebException이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-384">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="38f25-385">-Token</span><span class="sxs-lookup"><span data-stu-id="38f25-385">-Token</span></span>

<span data-ttu-id="38f25-386">요청에 포함할 OAuth 또는 전달자 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-386">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="38f25-387">**토큰** 은 특정 **인증** 옵션에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-387">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="38f25-388">독립적으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-388">It can't be used independently.</span></span>

<span data-ttu-id="38f25-389">**토큰** `SecureString` 은 토큰이 포함 된를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-389">**Token** takes a `SecureString` that contains the token.</span></span> <span data-ttu-id="38f25-390">토큰을 제공 하려면 다음을 수동으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-390">To supply the token, manually use the following:</span></span>

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="38f25-391">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-391">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="38f25-392">-전송자 인코딩</span><span class="sxs-lookup"><span data-stu-id="38f25-392">-TransferEncoding</span></span>

<span data-ttu-id="38f25-393">transfer-encoding HTTP 응답 헤더의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-393">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="38f25-394">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-394">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="38f25-395">청크</span><span class="sxs-lookup"><span data-stu-id="38f25-395">Chunked</span></span>
- <span data-ttu-id="38f25-396">압축</span><span class="sxs-lookup"><span data-stu-id="38f25-396">Compress</span></span>
- <span data-ttu-id="38f25-397">Deflate</span><span class="sxs-lookup"><span data-stu-id="38f25-397">Deflate</span></span>
- <span data-ttu-id="38f25-398">GZip</span><span class="sxs-lookup"><span data-stu-id="38f25-398">GZip</span></span>
- <span data-ttu-id="38f25-399">ID</span><span class="sxs-lookup"><span data-stu-id="38f25-399">Identity</span></span>

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

### <span data-ttu-id="38f25-400">-Uri</span><span class="sxs-lookup"><span data-stu-id="38f25-400">-Uri</span></span>

<span data-ttu-id="38f25-401">웹 요청이 전송 되는 인터넷 리소스의 URI (Uniform Resource Identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-401">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="38f25-402">이 매개 변수는 HTTP, HTTPS, FTP 및 FILE 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-402">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="38f25-403">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-403">This parameter is required.</span></span> <span data-ttu-id="38f25-404">매개 변수 이름 ( **Uri** )은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-404">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="38f25-405">-UseBasicParsing 분석</span><span class="sxs-lookup"><span data-stu-id="38f25-405">-UseBasicParsing</span></span>

<span data-ttu-id="38f25-406">이 매개 변수는 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-406">This parameter has been deprecated.</span></span> <span data-ttu-id="38f25-407">PowerShell 6.0.0부터 모든 웹 요청은 기본 구문 분석만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-407">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="38f25-408">이 매개 변수는 이전 버전과의 호환성을 위해서만 포함 되며 cmdlet의 작업에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-408">This parameter is included for backwards compatibility only and any use of it will have no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="38f25-409">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="38f25-409">-UseDefaultCredentials</span></span>

<span data-ttu-id="38f25-410">Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 웹 요청을 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-410">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="38f25-411">이는 **인증** 또는 **자격 증명과** 함께 사용할 수 없으며, 일부 플랫폼에서 지원 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-411">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="38f25-412">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="38f25-412">-UserAgent</span></span>

<span data-ttu-id="38f25-413">웹 요청에 대한 사용자 에이전트 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-413">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="38f25-414">기본 사용자 에이전트는 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 각 운영 체제 및 플랫폼에 대해 약간 변형 된와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-414">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="38f25-415">대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, InternetExplorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 클래스의 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-415">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="38f25-416">-WebSession</span><span class="sxs-lookup"><span data-stu-id="38f25-416">-WebSession</span></span>

<span data-ttu-id="38f25-417">웹 요청 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-417">Specifies a web request session.</span></span> <span data-ttu-id="38f25-418">달러 기호 ()를 포함 하 여 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-418">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="38f25-419">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-419">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="38f25-420">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-420">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="38f25-421">`Content-Type` **본문** 에 대해 **MultipartFormDataContent** 개체를 제공 하는 경우와 같은 콘텐츠 관련 헤더만 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-421">Content related headers, such as `Content-Type`, will be also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="38f25-422">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-422">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="38f25-423">쿠키, 자격 증명, 최대 리디렉션 값 및 사용자 에이전트 문자열을 포함 하 여 연결 및 요청에 대 한 정보를 포함 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-423">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="38f25-424">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-424">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="38f25-425">웹 요청 세션을 만들려면 명령의 **Sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-RestMethod` 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-425">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="38f25-426">`Invoke-RestMethod` 세션을 만들어 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-426">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="38f25-427">후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-427">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="38f25-428">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-428">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="38f25-429">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38f25-429">CommonParameters</span></span>

<span data-ttu-id="38f25-430">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38f25-430">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38f25-431">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38f25-431">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38f25-432">입력</span><span class="sxs-lookup"><span data-stu-id="38f25-432">INPUTS</span></span>

### <span data-ttu-id="38f25-433">System.Object</span><span class="sxs-lookup"><span data-stu-id="38f25-433">System.Object</span></span>

<span data-ttu-id="38f25-434">웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="38f25-434">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="38f25-435">출력</span><span class="sxs-lookup"><span data-stu-id="38f25-435">OUTPUTS</span></span>

### <span data-ttu-id="38f25-436">System.object, System.string, System.Xml.Xml문서</span><span class="sxs-lookup"><span data-stu-id="38f25-436">System.Int64, System.String, System.Xml.XmlDocument</span></span>

<span data-ttu-id="38f25-437">cmdlet의 출력은 검색된 콘텐츠의 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-437">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="38f25-438">PSObject</span><span class="sxs-lookup"><span data-stu-id="38f25-438">PSObject</span></span>

<span data-ttu-id="38f25-439">요청에서 JSON 문자열을 반환 하는 경우는 `Invoke-RestMethod` 문자열을 나타내는 **PSObject** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-439">If the request returns JSON strings, `Invoke-RestMethod` returns a **PSObject** that represents the strings.</span></span>

## <span data-ttu-id="38f25-440">참고</span><span class="sxs-lookup"><span data-stu-id="38f25-440">NOTES</span></span>

<span data-ttu-id="38f25-441">일부 플랫폼에서는 일부 기능을 사용 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-441">Some features may not be available on all platforms.</span></span>

<span data-ttu-id="38f25-442">.NET Core 3.1의 변경 내용으로 인해 PowerShell 7.0 이상에서는 [Httpclient. defaultproxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 속성을 사용 하 여 프록시 구성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-442">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) property to determine the proxy configuration.</span></span>

<span data-ttu-id="38f25-443">이 속성의 값은 플랫폼에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-443">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="38f25-444">**Windows의 경우** : 환경 변수에서 프록시 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-444">**For Windows** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="38f25-445">이러한 변수가 정의 되지 않은 경우 속성은 사용자의 프록시 설정에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-445">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="38f25-446">**MacOS의 경우** : 환경 변수에서 프록시 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-446">**For macOS** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="38f25-447">이러한 변수가 정의 되지 않은 경우 속성은 시스템의 프록시 설정에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-447">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="38f25-448">**Linux** : 환경 변수에서 프록시 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-448">**For Linux** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="38f25-449">이러한 변수가 정의 되지 않은 경우 속성은 모든 주소를 우회 하는 구성 되지 않은 인스턴스를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-449">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="38f25-450">`DefaultProxy`Windows 및 Unix 기반 플랫폼에서 초기화 하는 데 사용 되는 환경 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-450">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="38f25-451">` HTTP_PROXY`: HTTP 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-451">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="38f25-452">`HTTPS_PROXY`: HTTPS 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-452">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="38f25-453">`ALL_PROXY`: 또는의 경우 HTTP 및 HTTPS 요청에 사용 되는 프록시 서버의 호스트 이름 또는 IP 주소를 `HTTP_PROXY` `HTTPS_PROXY` 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-453">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="38f25-454">`NO_PROXY`: 프록시에서 제외 되어야 하는 쉼표로 구분 된 호스트 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="38f25-454">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="38f25-455">관련 링크</span><span class="sxs-lookup"><span data-stu-id="38f25-455">RELATED LINKS</span></span>

[<span data-ttu-id="38f25-456">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="38f25-456">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="38f25-457">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="38f25-457">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="38f25-458">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="38f25-458">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
