---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 25da6262e93be3e3749aabaf4950e2fbcd91ff5c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219226"
---
# <span data-ttu-id="531d7-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="531d7-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="531d7-104">개요</span><span class="sxs-lookup"><span data-stu-id="531d7-104">SYNOPSIS</span></span>
<span data-ttu-id="531d7-105">인터넷의 웹 페이지에서 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-105">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="531d7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="531d7-106">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="531d7-107">설명</span><span class="sxs-lookup"><span data-stu-id="531d7-107">DESCRIPTION</span></span>

<span data-ttu-id="531d7-108">`Invoke-WebRequest`Cmdlet은 HTTP, HTTPS, FTP 및 파일 요청을 웹 페이지나 웹 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-108">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="531d7-109">응답을 구문 분석하고 양식, 링크, 이미지 및 기타 중요한 HTML 요소 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-109">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="531d7-110">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="531d7-111">기본적으로 페이지를 구문 분석 하 여 속성을 채우도록 웹 페이지의 스크립트 코드를 실행할 수 있습니다 `ParsedHtml` .</span><span class="sxs-lookup"><span data-stu-id="531d7-111">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="531d7-112">스위치를 사용 `-UseBasicParsing` 하 여이를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-112">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="531d7-113">예제</span><span class="sxs-lookup"><span data-stu-id="531d7-113">EXAMPLES</span></span>

### <span data-ttu-id="531d7-114">예제 1: 웹 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="531d7-114">Example 1: Send a web request</span></span>

<span data-ttu-id="531d7-115">이 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` Bing.com 사이트에 웹 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-115">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="531d7-116">첫 번째 명령은 요청을 실행 하 고 응답을 변수에 저장 합니다 `$R` .</span><span class="sxs-lookup"><span data-stu-id="531d7-116">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="531d7-117">두 번째 명령은 **Allelements** 속성에서 **name** 속성이 "\* Value"와 비슷하며 **tagName** 이 "INPUT" 인 개체를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-117">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="531d7-118">필터링 된 결과를로 파이프 하 여 `Select-Object` **name** 및 **value** 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-118">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="531d7-119">예제 2: 상태 저장 웹 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="531d7-119">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="531d7-120">이 예에서는 `Invoke-WebRequest` Facebook과 같은 상태 저장 웹 서비스에서 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-120">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

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

<span data-ttu-id="531d7-121">첫 번째 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` 로그인 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-121">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="531d7-122">이 명령은 **sessionvariable** 매개 변수 값에 대해 "FB" 값을 지정 하 고 결과를 변수에 저장 합니다 `$R` .</span><span class="sxs-lookup"><span data-stu-id="531d7-122">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="531d7-123">명령이 완료 되 면 변수는 `$R` **Htmlwebresponseobject** 를 포함 하 고 `$FB` 변수는 **webrequestsession** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-123">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="531d7-124">Cmdlet이 facebook에 로그인 한 후 `Invoke-WebRequest` 변수에 있는 웹 응답 개체의 **statusdescription** 속성은 사용자가 `$R` 성공적으로 로그인 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-124">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="531d7-125">예제 3: 웹 페이지에서 링크 가져오기</span><span class="sxs-lookup"><span data-stu-id="531d7-125">Example 3: Get links from a web page</span></span>

<span data-ttu-id="531d7-126">이 명령은 웹 페이지에 있는 링크를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-126">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="531d7-127">`Invoke-WebRequest`Cmdlet은 웹 페이지 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-127">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="531d7-128">그러면 반환 된 **Htmlwebresponseobject** 의 **Links** 속성이 각 링크의 **Href** 속성을 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-128">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="531d7-129">예제 4: Invoke-WebRequest에서 비 성공 메시지 Catch</span><span class="sxs-lookup"><span data-stu-id="531d7-129">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="531d7-130">에서 `Invoke-WebRequest` 비 성공 HTTP 메시지 (404, 500 등)를 발견 하면 출력을 반환 하지 않고 종료 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-130">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="531d7-131">오류를 catch 하 고 **StatusCode** 를 보려면 블록으로 실행을 묶을 수 있습니다 `try/catch` .</span><span class="sxs-lookup"><span data-stu-id="531d7-131">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="531d7-132">다음 예제에서는이를 수행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-132">The following example shows how to accomplish this.</span></span>

```powershell
try
{
    $response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
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

<span data-ttu-id="531d7-133">첫 번째 명령은 `Invoke-WebRequest` 실패 한 요청에 대해 종료 오류를 강제로 throw 하는 **Stop** 의 **erroraction** 을 사용 하 여를 호출 합니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="531d7-133">The first command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="531d7-134">종료 오류는 `catch` **예외** 개체에서 **StatusCode** 를 검색 하는 블록에 의해 catch 됩니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-134">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="531d7-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="531d7-135">PARAMETERS</span></span>

### <span data-ttu-id="531d7-136">-본문</span><span class="sxs-lookup"><span data-stu-id="531d7-136">-Body</span></span>

<span data-ttu-id="531d7-137">요청의 본문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-137">Specifies the body of the request.</span></span>
<span data-ttu-id="531d7-138">본문은 헤더 뒤에 오는 요청 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-138">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="531d7-139">본문 값을로 파이프 할 수도 있습니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="531d7-139">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="531d7-140">**Body** 매개 변수를 사용하여 쿼리 매개 변수 목록을 지정하거나 응답 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-140">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="531d7-141">입력이 GET 요청이 고 본문이 **IDictionary** (일반적으로 해시 테이블) 이면 본문이 쿼리 매개 변수로 URI에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-141">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="531d7-142">다른 GET 요청의 경우 본문은 표준 형식의 요청 본문 값으로 설정 됩니다 `name=value` .</span><span class="sxs-lookup"><span data-stu-id="531d7-142">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="531d7-143">본문이 폼 이거나 호출의 출력 인 경우 `Invoke-WebRequest` PowerShell은 양식 필드에 요청 콘텐츠를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-143">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="531d7-144">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="531d7-144">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="531d7-145">또는</span><span class="sxs-lookup"><span data-stu-id="531d7-145">or -</span></span>

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

### <span data-ttu-id="531d7-146">-인증서</span><span class="sxs-lookup"><span data-stu-id="531d7-146">-Certificate</span></span>

<span data-ttu-id="531d7-147">보안 웹 요청에 사용되는 클라이언트 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-147">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="531d7-148">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-148">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="531d7-149">인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` **인증서** () 드라이브에서 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-149">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="531d7-150">인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-150">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="531d7-151">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="531d7-151">-CertificateThumbprint</span></span>

<span data-ttu-id="531d7-152">요청을 보낼 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-152">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="531d7-153">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-153">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="531d7-154">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-154">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="531d7-155">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-155">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="531d7-156">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-156">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="531d7-157">-ContentType</span><span class="sxs-lookup"><span data-stu-id="531d7-157">-ContentType</span></span>

<span data-ttu-id="531d7-158">웹 요청의 콘텐츠 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-158">Specifies the content type of the web request.</span></span>

<span data-ttu-id="531d7-159">이 매개 변수를 생략 하 고 요청 메서드를 POST로 `Invoke-WebRequest` 설정 하면에서 콘텐츠 형식을 application/x-www-form-urlencoded로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-159">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="531d7-160">그러지 않으면 호출에서 콘텐츠 형식이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-160">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="531d7-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="531d7-161">-Credential</span></span>

<span data-ttu-id="531d7-162">요청을 보낼 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-162">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="531d7-163">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-163">The default is the current user.</span></span>

<span data-ttu-id="531d7-164">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="531d7-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="531d7-165">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="531d7-166">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="531d7-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="531d7-167">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="531d7-167">-DisableKeepAlive</span></span>

<span data-ttu-id="531d7-168">Cmdlet이 HTTP 헤더의 **KeepAlive** 값을 **False** 로 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-168">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="531d7-169">기본적으로 **KeepAlive** 는 **True** 입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-169">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="531d7-170">**KeepAlive** 는 후속 요청의 신속한 처리를 위해 서버에 대한 영구 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-170">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="531d7-171">-헤더</span><span class="sxs-lookup"><span data-stu-id="531d7-171">-Headers</span></span>

<span data-ttu-id="531d7-172">웹 요청의 헤더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-172">Specifies the headers of the web request.</span></span> <span data-ttu-id="531d7-173">해시 테이블 또는 사전을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-173">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="531d7-174">**UserAgent** 헤더를 설정 하려면 **UserAgent** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-174">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="531d7-175">이 매개 변수를 사용 하 여 **UserAgent** 또는 쿠키 헤더를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-175">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="531d7-176">-InFile</span><span class="sxs-lookup"><span data-stu-id="531d7-176">-InFile</span></span>

<span data-ttu-id="531d7-177">파일에서 웹 요청의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-177">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="531d7-178">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-178">Enter a path and file name.</span></span> <span data-ttu-id="531d7-179">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-179">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="531d7-180">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="531d7-180">-MaximumRedirection</span></span>

<span data-ttu-id="531d7-181">연결에 실패 하기 전에 PowerShell이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션하는 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-181">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="531d7-182">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-182">The default value is 5.</span></span> <span data-ttu-id="531d7-183">값 0은 모든 리디렉션을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-183">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="531d7-184">-메서드</span><span class="sxs-lookup"><span data-stu-id="531d7-184">-Method</span></span>

<span data-ttu-id="531d7-185">웹 요청에 사용되는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-185">Specifies the method used for the web request.</span></span> <span data-ttu-id="531d7-186">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="531d7-187">기본값</span><span class="sxs-lookup"><span data-stu-id="531d7-187">Default</span></span>
- <span data-ttu-id="531d7-188">DELETE</span><span class="sxs-lookup"><span data-stu-id="531d7-188">Delete</span></span>
- <span data-ttu-id="531d7-189">가져오기</span><span class="sxs-lookup"><span data-stu-id="531d7-189">Get</span></span>
- <span data-ttu-id="531d7-190">Head</span><span class="sxs-lookup"><span data-stu-id="531d7-190">Head</span></span>
- <span data-ttu-id="531d7-191">병합</span><span class="sxs-lookup"><span data-stu-id="531d7-191">Merge</span></span>
- <span data-ttu-id="531d7-192">옵션</span><span class="sxs-lookup"><span data-stu-id="531d7-192">Options</span></span>
- <span data-ttu-id="531d7-193">패치</span><span class="sxs-lookup"><span data-stu-id="531d7-193">Patch</span></span>
- <span data-ttu-id="531d7-194">게시</span><span class="sxs-lookup"><span data-stu-id="531d7-194">Post</span></span>
- <span data-ttu-id="531d7-195">Put</span><span class="sxs-lookup"><span data-stu-id="531d7-195">Put</span></span>
- <span data-ttu-id="531d7-196">추적</span><span class="sxs-lookup"><span data-stu-id="531d7-196">Trace</span></span>

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

### <span data-ttu-id="531d7-197">-출력</span><span class="sxs-lookup"><span data-stu-id="531d7-197">-OutFile</span></span>

<span data-ttu-id="531d7-198">이 cmdlet이 응답 본문을 저장 하는 출력 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-198">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="531d7-199">경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-199">Enter a path and file name.</span></span>
<span data-ttu-id="531d7-200">경로를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-200">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="531d7-201">기본적으로는 `Invoke-WebRequest` 결과를 파이프라인으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-201">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="531d7-202">결과를 파일과 파이프라인으로 보내려면 **Passthru** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-202">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="531d7-203">-PassThru</span><span class="sxs-lookup"><span data-stu-id="531d7-203">-PassThru</span></span>

<span data-ttu-id="531d7-204">Cmdlet이 결과를 파일에 기록 하는 것 외에도 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-204">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="531d7-205">이 매개 변수는 명령에 **OutFile** 매개 변수도 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-205">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="531d7-206">-프록시</span><span class="sxs-lookup"><span data-stu-id="531d7-206">-Proxy</span></span>

<span data-ttu-id="531d7-207">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-207">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="531d7-208">네트워크 프록시 서버의 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-208">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="531d7-209">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="531d7-209">-ProxyCredential</span></span>

<span data-ttu-id="531d7-210">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-210">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="531d7-211">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-211">The default is the current user.</span></span>

<span data-ttu-id="531d7-212">또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="531d7-212">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="531d7-213">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-213">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="531d7-214">동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-214">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="531d7-215">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="531d7-215">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="531d7-216">Cmdlet이 현재 사용자의 자격 증명을 사용 하 여 **프록시** 매개 변수로 지정 된 프록시 서버에 액세스 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-216">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="531d7-217">이 매개 변수는 **프록시** 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-217">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="531d7-218">동일한 명령에 **ProxyCredential** 및 **ProxyUseDefaultCredentials** 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-218">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="531d7-219">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="531d7-219">-SessionVariable</span></span>

<span data-ttu-id="531d7-220">이 cmdlet이 웹 요청 세션을 만들고 값에 저장 하는 데 사용할 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-220">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="531d7-221">달러 기호 () 기호 없이 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-221">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="531d7-222">세션 변수를 지정 하면에서 `Invoke-WebRequest` 웹 요청 세션 개체를 만들어 PowerShell 세션에서 지정 된 이름의 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-222">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="531d7-223">명령이 완료되면 즉시 세션에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-223">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="531d7-224">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-224">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="531d7-225">쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-225">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="531d7-226">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-226">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="531d7-227">후속 웹 요청에서 웹 요청 세션을 사용하려면 **WebSession** 매개 변수 값에 세션 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-227">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="531d7-228">PowerShell은 새 연결을 설정할 때 웹 요청 세션 개체의 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-228">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="531d7-229">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-229">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="531d7-230">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-230">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="531d7-231">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-231">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="531d7-232">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="531d7-232">-TimeoutSec</span></span>

<span data-ttu-id="531d7-233">시간이 초과 되기 전에 요청이 보류 될 수 있는 기간을 지정 합니다. 초 단위로 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-233">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="531d7-234">기본값 0은 무기한 시간 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-234">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="531d7-235">DNS (도메인 이름 시스템) 쿼리를 반환 하거나 시간이 초과 되는 데 최대 15 초까지 걸릴 수 있습니다. 요청에 확인이 필요한 호스트 이름이 포함 되어 있는 경우 **Timeoutsec** 를 0 보다 큰 값으로 설정 하지만 15 초 보다 작은 값으로 설정 하면 **WebException** 이 throw 되 고 요청 시간이 초과 되기 전에 15 초 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-235">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="531d7-236">-전송자 인코딩</span><span class="sxs-lookup"><span data-stu-id="531d7-236">-TransferEncoding</span></span>

<span data-ttu-id="531d7-237">transfer-encoding HTTP 응답 헤더의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-237">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="531d7-238">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-238">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="531d7-239">청크</span><span class="sxs-lookup"><span data-stu-id="531d7-239">Chunked</span></span>
- <span data-ttu-id="531d7-240">압축</span><span class="sxs-lookup"><span data-stu-id="531d7-240">Compress</span></span>
- <span data-ttu-id="531d7-241">Deflate</span><span class="sxs-lookup"><span data-stu-id="531d7-241">Deflate</span></span>
- <span data-ttu-id="531d7-242">GZip</span><span class="sxs-lookup"><span data-stu-id="531d7-242">GZip</span></span>
- <span data-ttu-id="531d7-243">ID</span><span class="sxs-lookup"><span data-stu-id="531d7-243">Identity</span></span>

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

### <span data-ttu-id="531d7-244">-Uri</span><span class="sxs-lookup"><span data-stu-id="531d7-244">-Uri</span></span>

<span data-ttu-id="531d7-245">웹 요청이 전송되는 인터넷 리소스의 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-245">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="531d7-246">URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-246">Enter a URI.</span></span> <span data-ttu-id="531d7-247">이 매개 변수는 HTTP, HTTPS, FTP 및 FILE 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-247">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="531d7-248">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-248">This parameter is required.</span></span>

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

### <span data-ttu-id="531d7-249">-UseBasicParsing 분석</span><span class="sxs-lookup"><span data-stu-id="531d7-249">-UseBasicParsing</span></span>

<span data-ttu-id="531d7-250">Cmdlet이 DOM (문서 개체 모델) 구문 분석 없이 HTML 콘텐츠에 대 한 응답 개체를 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-250">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="531d7-251">이 매개 변수는 Windows Server 운영 체제의 Server Core 설치와 같이 컴퓨터에 Internet Explorer가 설치되지 않은 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-251">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="531d7-252">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="531d7-252">-UseDefaultCredentials</span></span>

<span data-ttu-id="531d7-253">Cmdet가 현재 사용자의 자격 증명을 사용 하 여 웹 요청을 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-253">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="531d7-254">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="531d7-254">-UserAgent</span></span>

<span data-ttu-id="531d7-255">웹 요청에 대한 사용자 에이전트 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-255">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="531d7-256">기본 사용자 에이전트는 `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` 각 운영 체제 및 플랫폼에 대해 약간 변형 된와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-256">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="531d7-257">대부분의 인터넷 브라우저에서 사용 되는 표준 사용자 에이전트 문자열을 사용 하 여 웹 사이트를 테스트 하려면 Chrome, FireFox, InternetExplorer, Opera 및 Safari와 같은 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 클래스의 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-257">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="531d7-258">예를 들어 다음 명령은 Internet Explorer에 대 한 사용자 에이전트 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-258">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="531d7-259">-WebSession</span><span class="sxs-lookup"><span data-stu-id="531d7-259">-WebSession</span></span>

<span data-ttu-id="531d7-260">웹 요청 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-260">Specifies a web request session.</span></span> <span data-ttu-id="531d7-261">달러 기호 ()를 포함 하 여 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-261">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="531d7-262">웹 요청 세션의 값을 재정의하려면 **UserAgent** 또는 **Credential** 과 같은 cmdlet 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-262">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="531d7-263">매개 변수 값이 웹 요청 세션의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-263">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="531d7-264">원격 세션과 달리 웹 요청 세션은 영구 연결이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-264">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="531d7-265">쿠키, 자격 증명, 최대 리디렉션 횟수 값 및 사용자 에이전트 문자열을 포함하여 연결과 요청에 대한 정보가 포함된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-265">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="531d7-266">이 개체를 사용하여 웹 요청 간에 상태와 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-266">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="531d7-267">웹 요청 세션을 만들려면 명령의 **sessionvariable** 매개 변수 값에 달러 기호 없이 변수 이름을 입력 `Invoke-WebRequest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-267">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="531d7-268">`Invoke-WebRequest` 세션을 만들어 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-268">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="531d7-269">후속 명령에서 변수를 **WebSession** 매개 변수 값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-269">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="531d7-270">동일한 명령에서 **Sessionvariable** 및 **websession** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-270">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="531d7-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="531d7-271">CommonParameters</span></span>

<span data-ttu-id="531d7-272">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="531d7-272">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="531d7-273">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="531d7-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="531d7-274">입력</span><span class="sxs-lookup"><span data-stu-id="531d7-274">INPUTS</span></span>

### <span data-ttu-id="531d7-275">System.Object</span><span class="sxs-lookup"><span data-stu-id="531d7-275">System.Object</span></span>

<span data-ttu-id="531d7-276">웹 요청의 본문을로 파이프 할 수 있습니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="531d7-276">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="531d7-277">출력</span><span class="sxs-lookup"><span data-stu-id="531d7-277">OUTPUTS</span></span>

### <span data-ttu-id="531d7-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="531d7-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="531d7-279">참고</span><span class="sxs-lookup"><span data-stu-id="531d7-279">NOTES</span></span>

## <span data-ttu-id="531d7-280">관련 링크</span><span class="sxs-lookup"><span data-stu-id="531d7-280">RELATED LINKS</span></span>

[<span data-ttu-id="531d7-281">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="531d7-281">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="531d7-282">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="531d7-282">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="531d7-283">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="531d7-283">ConvertTo-Json</span></span>](ConvertTo-Json.md)
