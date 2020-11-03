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
# <span data-ttu-id="e6c6f-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="e6c6f-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="e6c6f-104">개요</span><span class="sxs-lookup"><span data-stu-id="e6c6f-104">Synopsis</span></span>
<span data-ttu-id="e6c6f-105">HTTP 또는 HTTPS 요청을 RESTful 웹 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="e6c6f-106">구문</span><span class="sxs-lookup"><span data-stu-id="e6c6f-106">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="e6c6f-107">Description</span><span class="sxs-lookup"><span data-stu-id="e6c6f-107">Description</span></span>

<span data-ttu-id="e6c6f-108">Cmdlet은 다양 `Invoke-RestMethod` 한 구조화 된 데이터를 반환 하는 REST (Representational State Transfer) 웹 서비스로 HTTP 및 HTTPS 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-108">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data.</span></span>

<span data-ttu-id="e6c6f-109">Windows PowerShell은 데이터 형식에 따라 응답 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-109">Windows PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="e6c6f-110">RSS 또는 ATOM 피드의 경우 Windows PowerShell에서 항목 또는 항목 XML 노드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-110">For an RSS or ATOM feed, Windows PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="e6c6f-111">JSON(JavaScript Object Notation) 또는 XML의 경우 Windows PowerShell에서 내용을 개체로 변환(또는 역직렬화)합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-111">For JavaScript Object Notation (JSON) or XML, Windows PowerShell converts (or deserializes) the content into objects.</span></span>

<span data-ttu-id="e6c6f-112">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-112">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="e6c6f-113">기본적으로 페이지를 구문 분석 하 여 속성을 채우도록 웹 페이지의 스크립트 코드를 실행할 수 있습니다 `ParsedHtml` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-113">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="e6c6f-114">**Usebasicparsing 분석** 스위치를 사용 하 여이를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-114">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="e6c6f-115">예</span><span class="sxs-lookup"><span data-stu-id="e6c6f-115">Examples</span></span>

### <span data-ttu-id="e6c6f-116">예제 1: PowerShell RSS 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="e6c6f-116">Example 1: Get the PowerShell RSS feed</span></span>

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

<span data-ttu-id="e6c6f-117">이 명령은 cmdlet을 사용 하 여 `Invoke-RestMethod` PowerShell 블로그 RSS 피드에서 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-117">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="e6c6f-118">이 명령은 cmdlet을 사용 하 여 `Format-Table` 각 블로그의 **Title** 및 **pubDate** 속성 값을 테이블에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-118">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="e6c6f-119">예제 2</span><span class="sxs-lookup"><span data-stu-id="e6c6f-119">Example 2</span></span>

<span data-ttu-id="e6c6f-120">다음 예제에서는 사용자가 `Invoke-RestMethod` 를 실행 하 여 사용자 조직의 인트라넷 웹 사이트에서 POST 요청을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-120">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

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

### <span data-ttu-id="e6c6f-121">예제 3: 여러 헤더 전달</span><span class="sxs-lookup"><span data-stu-id="e6c6f-121">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="e6c6f-122">이 예제에서는에서 여러 헤더를 REST API에 전달 하는 방법을 보여 줍니다 `hash-table` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-122">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="e6c6f-123">Api는 인증, 유효성 검사 등을 위해 헤더를 전달 해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-123">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="e6c6f-124">예제 3: 양식 데이터 전송</span><span class="sxs-lookup"><span data-stu-id="e6c6f-124">Example 3: Submitting form data</span></span>

<span data-ttu-id="e6c6f-125">본문이 폼 이거나 다른 호출의 출력 인 경우 `Invoke-WebRequest` PowerShell은 양식 필드에 요청 콘텐츠를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-125">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="e6c6f-126">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="e6c6f-126">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## <span data-ttu-id="e6c6f-127">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6c6f-127">Parameters</span></span>

### <span data-ttu-id="e6c6f-128">-본문</span><span class="sxs-lookup"><span data-stu-id="e6c6f-128">-Body</span></span>

<span data-ttu-id="e6c6f-129">요청의 본문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-129">Specifies the body of the request.</span></span> <span data-ttu-id="e6c6f-130">본문은 헤더 뒤에 오는 요청 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-130">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="e6c6f-131">본문 값을로 파이프 할 수도 있습니다 `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-131">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="e6c6f-132">**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-132">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="e6c6f-133">입력이 GET 요청이고 본문이 IDictionary(일반적으로 해시 테이블)이면 본문이 쿼리 매개 변수로 URI에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-133">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="e6c6f-134">다른 요청 유형(예: POST)의 경우 본문이 표준 이름=값 형식의 요청 본문 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-134">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="e6c6f-135">`with -1-byte payload`본문의 크기가 모두 알려지고 HTTP 헤더에 전송 되더라도 게시 본문의 자세한 정보 출력은로 종료 됩니다 `Content-Length` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-135">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

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

### <span data-ttu-id="e6c6f-136">-인증서</span><span class="sxs-lookup"><span data-stu-id="e6c6f-136">-Certificate</span></span>

<span data-ttu-id="e6c6f-137">보안 웹 요청에 사용되는 클라이언트 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-137">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="e6c6f-138">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-138">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="e6c6f-139">인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 () 드라이브에서 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-139">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="e6c6f-140">인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-140">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="e6c6f-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="e6c6f-141">-CertificateThumbprint</span></span>

<span data-ttu-id="e6c6f-142">요청을 보낼 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-142">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="e6c6f-143">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="e6c6f-144">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="e6c6f-145">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="e6c6f-146">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` Windows PowerShell () 드라이브에서 또는 명령을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="e6c6f-147">-ContentType</span><span class="sxs-lookup"><span data-stu-id="e6c6f-147">-ContentType</span></span>

<span data-ttu-id="e6c6f-148">웹 요청의 콘텐츠 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-148">Specifies the content type of the web request.</span></span>

<span data-ttu-id="e6c6f-149">이 매개 변수를 생략 하 고 요청 메서드가 POST 이면 `Invoke-RestMethod` 내용 유형을 "application/x-www-form-urlencoded"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-149">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="e6c6f-150">그러지 않으면 호출에서 콘텐츠 형식이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-150">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="e6c6f-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="e6c6f-151">-Credential</span></span>

<span data-ttu-id="e6c6f-152">요청을 보낼 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-152">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="e6c6f-153">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-153">The default is the current user.</span></span>

<span data-ttu-id="e6c6f-154">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="e6c6f-155">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-155">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="e6c6f-156">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="e6c6f-156">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="e6c6f-157">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="e6c6f-157">-DisableKeepAlive</span></span>

<span data-ttu-id="e6c6f-158">HTTP 헤더의 **KeepAlive** 값을 False로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-158">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="e6c6f-159">기본적으로 **KeepAlive** 는 True입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-159">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="e6c6f-160">**KeepAlive** 는 후속 요청의 신속한 처리를 위해 서버에 대한 영구 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-160">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="e6c6f-161">-헤더</span><span class="sxs-lookup"><span data-stu-id="e6c6f-161">-Headers</span></span>

<span data-ttu-id="e6c6f-162">웹 요청의 헤더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-162">Specifies the headers of the web request.</span></span> <span data-ttu-id="e6c6f-163">해시 테이블 또는 사전을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-163">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="e6c6f-164">UserAgent 헤더를 설정하려면 **UserAgent** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-164">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="e6c6f-165">이 매개 변수를 사용하여 UserAgent 또는 쿠키 헤더를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-165">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

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

### <span data-ttu-id="e6c6f-166">-InFile</span><span class="sxs-lookup"><span data-stu-id="e6c6f-166">-InFile</span></span>

<span data-ttu-id="e6c6f-167">파일에서 웹 요청의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-167">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="e6c6f-168">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-168">Enter a path and file name.</span></span> <span data-ttu-id="e6c6f-169">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-169">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="e6c6f-170">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="e6c6f-170">-MaximumRedirection</span></span>

<span data-ttu-id="e6c6f-171">연결이 실패하기 전에 Windows PowerShell에서 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션하는 횟수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-171">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="e6c6f-172">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-172">The default value is 5.</span></span> <span data-ttu-id="e6c6f-173">값 0은 모든 리디렉션을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-173">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="e6c6f-174">-메서드</span><span class="sxs-lookup"><span data-stu-id="e6c6f-174">-Method</span></span>

<span data-ttu-id="e6c6f-175">웹 요청에 사용되는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-175">Specifies the method used for the web request.</span></span> <span data-ttu-id="e6c6f-176">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-176">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e6c6f-177">기본값</span><span class="sxs-lookup"><span data-stu-id="e6c6f-177">Default</span></span>
- <span data-ttu-id="e6c6f-178">DELETE</span><span class="sxs-lookup"><span data-stu-id="e6c6f-178">Delete</span></span>
- <span data-ttu-id="e6c6f-179">가져오기</span><span class="sxs-lookup"><span data-stu-id="e6c6f-179">Get</span></span>
- <span data-ttu-id="e6c6f-180">Head</span><span class="sxs-lookup"><span data-stu-id="e6c6f-180">Head</span></span>
- <span data-ttu-id="e6c6f-181">병합</span><span class="sxs-lookup"><span data-stu-id="e6c6f-181">Merge</span></span>
- <span data-ttu-id="e6c6f-182">옵션</span><span class="sxs-lookup"><span data-stu-id="e6c6f-182">Options</span></span>
- <span data-ttu-id="e6c6f-183">패치</span><span class="sxs-lookup"><span data-stu-id="e6c6f-183">Patch</span></span>
- <span data-ttu-id="e6c6f-184">게시</span><span class="sxs-lookup"><span data-stu-id="e6c6f-184">Post</span></span>
- <span data-ttu-id="e6c6f-185">Put</span><span class="sxs-lookup"><span data-stu-id="e6c6f-185">Put</span></span>
- <span data-ttu-id="e6c6f-186">추적</span><span class="sxs-lookup"><span data-stu-id="e6c6f-186">Trace</span></span>

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

### <span data-ttu-id="e6c6f-187">-출력</span><span class="sxs-lookup"><span data-stu-id="e6c6f-187">-OutFile</span></span>

<span data-ttu-id="e6c6f-188">응답 본문을 지정한 출력 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-188">Saves the response body in the specified output file.</span></span> <span data-ttu-id="e6c6f-189">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-189">Enter a path and file name.</span></span> <span data-ttu-id="e6c6f-190">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-190">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="e6c6f-191">기본적으로는 `Invoke-RestMethod` 결과를 파이프라인으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-191">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="e6c6f-192">결과를 파일과 파이프라인으로 보내려면 **Passthru** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-192">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="e6c6f-193">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e6c6f-193">-PassThru</span></span>

<span data-ttu-id="e6c6f-194">결과를 반환하고 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-194">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="e6c6f-195">이 매개 변수는 명령에 **OutFile** 매개 변수도 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-195">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="e6c6f-196">-프록시</span><span class="sxs-lookup"><span data-stu-id="e6c6f-196">-Proxy</span></span>

<span data-ttu-id="e6c6f-197">인터넷 리소스에 직접 연결하는 대신 요청에 프록시 서버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-197">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="e6c6f-198">네트워크 프록시 서버의 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-198">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="e6c6f-199">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e6c6f-199">-ProxyCredential</span></span>

<span data-ttu-id="e6c6f-200">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-200">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="e6c6f-201">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-201">The default is the current user.</span></span>

<span data-ttu-id="e6c6f-202">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-202">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="e6c6f-203">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-203">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="e6c6f-204">동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-204">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="e6c6f-205">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="e6c6f-205">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="e6c6f-206">현재 사용자의 자격 증명을 사용하여 **Proxy** 매개 변수에 지정된 프록시 서버에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-206">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="e6c6f-207">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-207">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="e6c6f-208">동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-208">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="e6c6f-209">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="e6c6f-209">-SessionVariable</span></span>

<span data-ttu-id="e6c6f-210">웹 요청 세션을 만들어 지정한 변수 값에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-210">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="e6c6f-211">달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-211">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="e6c6f-212">세션 변수를 지정 하면에서 `Invoke-RestMethod` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-212">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="e6c6f-213">명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-213">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="e6c6f-214">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-214">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="e6c6f-215">쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-215">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="e6c6f-216">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-216">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="e6c6f-217">후속 웹 요청에서 웹 요청 세션을 사용하려면 **WebSession** 매개 변수 값에 세션 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-217">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="e6c6f-218">Windows PowerShell은 새 연결을 설정할 때 웹 요청 세션 개체의 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-218">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="e6c6f-219">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-219">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="e6c6f-220">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-220">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="e6c6f-221">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-221">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="e6c6f-222">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="e6c6f-222">-TimeoutSec</span></span>

<span data-ttu-id="e6c6f-223">시간이 초과 되기 전에 요청이 보류 될 수 있는 기간을 지정 합니다. 초 단위로 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-223">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="e6c6f-224">기본값 0은 무기한 시간 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-224">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="e6c6f-225">DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 TimeoutSec를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 WebException이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-225">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="e6c6f-226">-전송자 인코딩</span><span class="sxs-lookup"><span data-stu-id="e6c6f-226">-TransferEncoding</span></span>

<span data-ttu-id="e6c6f-227">transfer-encoding HTTP 응답 헤더의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-227">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="e6c6f-228">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-228">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e6c6f-229">청크</span><span class="sxs-lookup"><span data-stu-id="e6c6f-229">Chunked</span></span>
- <span data-ttu-id="e6c6f-230">압축</span><span class="sxs-lookup"><span data-stu-id="e6c6f-230">Compress</span></span>
- <span data-ttu-id="e6c6f-231">Deflate</span><span class="sxs-lookup"><span data-stu-id="e6c6f-231">Deflate</span></span>
- <span data-ttu-id="e6c6f-232">GZip</span><span class="sxs-lookup"><span data-stu-id="e6c6f-232">GZip</span></span>
- <span data-ttu-id="e6c6f-233">ID</span><span class="sxs-lookup"><span data-stu-id="e6c6f-233">Identity</span></span>

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

### <span data-ttu-id="e6c6f-234">-Uri</span><span class="sxs-lookup"><span data-stu-id="e6c6f-234">-Uri</span></span>

<span data-ttu-id="e6c6f-235">웹 요청이 전송되는 인터넷 리소스의 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-235">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="e6c6f-236">이 매개 변수는 HTTP, HTTPS, FTP 및 FILE 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-236">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="e6c6f-237">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-237">This parameter is required.</span></span> <span data-ttu-id="e6c6f-238">매개 변수 이름 ( **Uri** )은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-238">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="e6c6f-239">-UseBasicParsing 분석</span><span class="sxs-lookup"><span data-stu-id="e6c6f-239">-UseBasicParsing</span></span>

<span data-ttu-id="e6c6f-240">Cmdlet에서 기본 구문 분석을 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-240">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="e6c6f-241">Cmdlet은 **문자열** 개체의 원시 HTML을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-241">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="e6c6f-242">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="e6c6f-242">-UseDefaultCredentials</span></span>

<span data-ttu-id="e6c6f-243">현재 사용자의 자격 증명을 사용하여 웹 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-243">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="e6c6f-244">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="e6c6f-244">-UserAgent</span></span>

<span data-ttu-id="e6c6f-245">웹 요청에 대한 사용자 에이전트 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-245">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="e6c6f-246">기본 사용자 에이전트는 각 운영 체제와 플랫폼마다 약간 변형되지만 "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0"과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-246">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="e6c6f-247">대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, Internet Explorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands) 클래스의 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-247">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="e6c6f-248">-WebSession</span><span class="sxs-lookup"><span data-stu-id="e6c6f-248">-WebSession</span></span>

<span data-ttu-id="e6c6f-249">웹 요청 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-249">Specifies a web request session.</span></span> <span data-ttu-id="e6c6f-250">달러 기호 ()를 포함 하 여 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-250">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="e6c6f-251">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-251">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="e6c6f-252">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-252">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="e6c6f-253">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-253">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="e6c6f-254">쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-254">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="e6c6f-255">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-255">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="e6c6f-256">웹 요청 세션을 만들려면 명령의 **sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-RestMethod` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-256">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="e6c6f-257">`Invoke-RestMethod` 세션을 만들어 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-257">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="e6c6f-258">후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-258">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="e6c6f-259">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-259">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="e6c6f-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e6c6f-260">CommonParameters</span></span>

<span data-ttu-id="e6c6f-261">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e6c6f-262">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e6c6f-263">입력</span><span class="sxs-lookup"><span data-stu-id="e6c6f-263">Inputs</span></span>

### <span data-ttu-id="e6c6f-264">System.Object</span><span class="sxs-lookup"><span data-stu-id="e6c6f-264">System.Object</span></span>

<span data-ttu-id="e6c6f-265">웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="e6c6f-265">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="e6c6f-266">outputs</span><span class="sxs-lookup"><span data-stu-id="e6c6f-266">Outputs</span></span>

### <span data-ttu-id="e6c6f-267">System.Xml.Xml문서, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.string</span><span class="sxs-lookup"><span data-stu-id="e6c6f-267">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="e6c6f-268">cmdlet의 출력은 검색된 콘텐츠의 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-268">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="e6c6f-269">PSObject</span><span class="sxs-lookup"><span data-stu-id="e6c6f-269">PSObject</span></span>

<span data-ttu-id="e6c6f-270">요청에서 JSON 문자열을 반환 하는 경우는 `Invoke-RestMethod` 문자열을 나타내는 PSObject를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c6f-270">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="e6c6f-271">메모</span><span class="sxs-lookup"><span data-stu-id="e6c6f-271">Notes</span></span>

## <span data-ttu-id="e6c6f-272">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e6c6f-272">Related Links</span></span>

[<span data-ttu-id="e6c6f-273">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="e6c6f-273">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="e6c6f-274">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="e6c6f-274">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="e6c6f-275">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="e6c6f-275">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
