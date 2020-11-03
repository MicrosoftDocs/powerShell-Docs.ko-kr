---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: 696bce9c1a578b054e5f9a7877f2195273ab8e8b
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218721"
---
# <span data-ttu-id="7d204-103">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7d204-103">New-WSManInstance</span></span>

## <span data-ttu-id="7d204-104">개요</span><span class="sxs-lookup"><span data-stu-id="7d204-104">SYNOPSIS</span></span>
<span data-ttu-id="7d204-105">관리 리소스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-105">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="7d204-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7d204-106">SYNTAX</span></span>

### <span data-ttu-id="7d204-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="7d204-107">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="7d204-108">URI</span><span class="sxs-lookup"><span data-stu-id="7d204-108">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="7d204-109">설명</span><span class="sxs-lookup"><span data-stu-id="7d204-109">DESCRIPTION</span></span>

<span data-ttu-id="7d204-110">`New-WSManInstance`Cmdlet은 관리 리소스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-110">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="7d204-111">이 cmdlet은 리소스 URI 및 값 집합 또는 입력 파일을 사용하여 관리 리소스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-111">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="7d204-112">이 cmdlet은 WinRM 연결/전송 계층을 사용하여 관리 리소스 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-112">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="7d204-113">예제</span><span class="sxs-lookup"><span data-stu-id="7d204-113">EXAMPLES</span></span>

### <span data-ttu-id="7d204-114">예제 1: HTTPS 수신기 만들기</span><span class="sxs-lookup"><span data-stu-id="7d204-114">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="7d204-115">이 명령은 모든 IP 주소에서 WS-Management HTTPS 수신기의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-115">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="7d204-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7d204-116">PARAMETERS</span></span>

### <span data-ttu-id="7d204-117">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="7d204-117">-ApplicationName</span></span>

<span data-ttu-id="7d204-118">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-118">Specifies the application name in the connection.</span></span> <span data-ttu-id="7d204-119">**ApplicationName** 매개 변수의 기본값은 **WSMAN** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-119">The default value of the **ApplicationName** parameter is **WSMAN**.</span></span> <span data-ttu-id="7d204-120">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-120">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="7d204-121">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="7d204-121">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="7d204-122">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="7d204-123">이러한 기본 **WSMAN** 설정은 대부분의 용도에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-123">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="7d204-124">이 매개 변수는 많은 컴퓨터에서 Windows PowerShell을 실행하는 한 컴퓨터에 대한 원격 연결을 설정할 때 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-124">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="7d204-125">이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="7d204-126">-인증</span><span class="sxs-lookup"><span data-stu-id="7d204-126">-Authentication</span></span>

<span data-ttu-id="7d204-127">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-127">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="7d204-128">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-128">Possible values are:</span></span>

- <span data-ttu-id="7d204-129">Basic: Basic은 사용자 이름과 암호가 일반 텍스트로 서버 또는 프록시에 전송 되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-129">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="7d204-130">기본값: WS-Management 프로토콜에 의해 구현 된 인증 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-130">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="7d204-131">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-131">This is the default.</span></span>
- <span data-ttu-id="7d204-132">다이제스트: 다이제스트는 챌린지에 대해 서버 지정 데이터 문자열을 사용 하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-132">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="7d204-133">Kerberos: 클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용 하 여 상호 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-133">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="7d204-134">Negotiate: Negotiate는 인증에 사용할 체계를 결정 하기 위해 서버 또는 프록시와 협상 하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-134">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="7d204-135">예를 들어 이 매개 변수 값을 통해 협상에서 Kerberos 프로토콜이 사용되는지 또는 NTLM이 사용되는지를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-135">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="7d204-136">CredSSP: 사용자가 자격 증명을 위임할 수 있도록 허용 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-136">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="7d204-137">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-137">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="7d204-138">CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-138">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="7d204-139">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-139">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="7d204-140">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-140">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="7d204-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="7d204-141">-CertificateThumbprint</span></span>

<span data-ttu-id="7d204-142">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-142">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="7d204-143">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="7d204-144">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="7d204-145">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="7d204-146">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="7d204-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7d204-147">-ComputerName</span></span>

<span data-ttu-id="7d204-148">관리 작업을 실행하려는 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-148">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="7d204-149">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-149">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="7d204-150">로컬 컴퓨터 이름, localhost 또는 점 ()을 사용 `.` 하 여 로컬 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-150">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="7d204-151">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-151">The local computer is the default.</span></span> <span data-ttu-id="7d204-152">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-152">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="7d204-153">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-153">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="7d204-154">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="7d204-154">-ConnectionURI</span></span>

<span data-ttu-id="7d204-155">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-155">Specifies the connection endpoint.</span></span>
<span data-ttu-id="7d204-156">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-156">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="7d204-157">다음 문자열은 이 매개 변수의 형식이 올바르게 지정된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-157">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="7d204-158">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-158">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d204-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="7d204-159">-Credential</span></span>

<span data-ttu-id="7d204-160">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-160">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="7d204-161">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-161">The default is the current user.</span></span> <span data-ttu-id="7d204-162">사용자 이름 (예: "User01", "Domain01\User01" 또는 "")을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-162">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="7d204-163">또는 cmdlet에서 반환 된 개체와 같은 PSCredential 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="7d204-163">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7d204-164">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-164">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="7d204-165">-FilePath</span><span class="sxs-lookup"><span data-stu-id="7d204-165">-FilePath</span></span>

<span data-ttu-id="7d204-166">관리 리소스를 만드는 데 사용되는 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-166">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="7d204-167">**ResourceURI** 매개 변수 및 **SelectorSet** 매개 변수를 사용 하 여 관리 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-167">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="7d204-168">예를 들어 다음 명령은 **File** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-168">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="7d204-169">이 명령은 파일의 입력을 사용 하 여 스풀러 서비스에 대해 **StopService** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-169">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="7d204-170">파일에 `Input.xml` 는 다음과 같은 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-170">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d204-171">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="7d204-171">-OptionSet</span></span>

<span data-ttu-id="7d204-172">요청의 특성을 수정하거나 구체화하기 위해 스위치 집합을 서비스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-172">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="7d204-173">이는 명령줄 셸에 사용되는 스위치와 유사한데, 서비스에 국한되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-173">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="7d204-174">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-174">Any number of options can be specified.</span></span>

<span data-ttu-id="7d204-175">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="7d204-176">-Port</span><span class="sxs-lookup"><span data-stu-id="7d204-176">-Port</span></span>

<span data-ttu-id="7d204-177">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-177">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="7d204-178">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-178">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="7d204-179">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="7d204-180">전송으로 HTTPS를 사용 하는 경우 **ComputerName** 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-180">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="7d204-181">그러나 **Skipcncheck** 매개 변수가 **sessionoption** 매개 변수의 일부로 지정 된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-181">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="7d204-182">**Skipcncheck** 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-182">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="7d204-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="7d204-183">-ResourceURI</span></span>

<span data-ttu-id="7d204-184">리소스 클래스 또는 인스턴스의 URI(Uniform Resource Identifier)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-184">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="7d204-185">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="7d204-186">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-186">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="7d204-187">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="7d204-187">For example:</span></span>

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

### <span data-ttu-id="7d204-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="7d204-188">-SelectorSet</span></span>

<span data-ttu-id="7d204-189">특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="7d204-190">**SelectorSet** 매개 변수는 리소스의 인스턴스가 둘 이상 있을 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-190">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="7d204-191">**SelectorSet** 매개 변수 값은 해시 테이블 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-191">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="7d204-192">다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7d204-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="7d204-193">-SessionOption</span></span>

<span data-ttu-id="7d204-194">WS-Management 세션에 대한 확장된 옵션 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-194">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="7d204-195">Cmdlet을 사용 하 여 만든 **Sessionoption** 개체를 입력 합니다 `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="7d204-195">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="7d204-196">사용할 수 있는 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="7d204-196">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="7d204-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="7d204-197">-UseSSL</span></span>

<span data-ttu-id="7d204-198">원격 컴퓨터에 대한 연결을 설정할 때 SSL(Secure Sockets Layer) 프로토콜이 반드시 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-198">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="7d204-199">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-199">By default, SSL is not used.</span></span>

<span data-ttu-id="7d204-200">WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-200">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="7d204-201">**UseSSL** 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-201">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="7d204-202">연결에 사용되는 포트에 SSL을 사용할 수 없는 경우에 이 매개 변수를 지정하면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-202">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="7d204-203">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="7d204-203">-ValueSet</span></span>

<span data-ttu-id="7d204-204">관리 리소스를 수정하는 데 도움이 되는 해시 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-204">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="7d204-205">**ResourceURI** 매개 변수 및 **SelectorSet** 매개 변수를 사용 하 여 관리 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-205">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="7d204-206">**Valueset** 매개 변수 값은 해시 테이블 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-206">The value of the **ValueSet** parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d204-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7d204-207">CommonParameters</span></span>

<span data-ttu-id="7d204-208">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7d204-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7d204-209">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d204-209">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7d204-210">입력</span><span class="sxs-lookup"><span data-stu-id="7d204-210">INPUTS</span></span>

### <span data-ttu-id="7d204-211">없음</span><span class="sxs-lookup"><span data-stu-id="7d204-211">None</span></span>

<span data-ttu-id="7d204-212">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-212">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="7d204-213">출력</span><span class="sxs-lookup"><span data-stu-id="7d204-213">OUTPUTS</span></span>

### <span data-ttu-id="7d204-214">없음</span><span class="sxs-lookup"><span data-stu-id="7d204-214">None</span></span>

<span data-ttu-id="7d204-215">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-215">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7d204-216">참고</span><span class="sxs-lookup"><span data-stu-id="7d204-216">NOTES</span></span>

<span data-ttu-id="7d204-217">`Set-WmiInstance`Cmdlet 인 WMI(Windows Management Instrumentation) (WMI) cmdlet은 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-217">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="7d204-218">`Set-WmiInstance` DCOM 연결/전송 계층을 사용 하 여 WMI 인스턴스를 만들거나 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d204-218">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="7d204-219">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7d204-219">RELATED LINKS</span></span>

[<span data-ttu-id="7d204-220">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="7d204-220">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="7d204-221">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7d204-221">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="7d204-222">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="7d204-222">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="7d204-223">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7d204-223">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="7d204-224">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7d204-224">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="7d204-225">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7d204-225">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="7d204-226">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="7d204-226">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="7d204-227">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="7d204-227">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="7d204-228">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7d204-228">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="7d204-229">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7d204-229">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="7d204-230">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="7d204-230">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="7d204-231">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="7d204-231">Test-WSMan</span></span>](Test-WSMan.md)

