---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: a29a9ef1e35f0c0f802952b99d853c617614a97b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602039"
---
# <span data-ttu-id="929fb-102">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="929fb-102">Test-WSMan</span></span>

## <span data-ttu-id="929fb-103">개요</span><span class="sxs-lookup"><span data-stu-id="929fb-103">SYNOPSIS</span></span>
<span data-ttu-id="929fb-104">WinRM 서비스가 로컬 컴퓨터에서 실행되고 있는지 또는 원격 컴퓨터에서 실행되고 있는지를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-104">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="929fb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="929fb-105">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="929fb-106">설명</span><span class="sxs-lookup"><span data-stu-id="929fb-106">DESCRIPTION</span></span>

<span data-ttu-id="929fb-107">**WSMan** Cmdlet은 WinRM 서비스가 로컬 컴퓨터에서 실행 되 고 있는지 또는 원격 컴퓨터에서 실행 되 고 있는지를 확인 하는 식별 요청을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-107">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="929fb-108">테스트된 컴퓨터가 이 서비스를 실행하고 있는 경우 이 cmdlet은 테스트된 서비스의 WS-Management ID 스키마, 프로토콜 버전, 제품 공급업체 및 제품 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-108">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="929fb-109">예제</span><span class="sxs-lookup"><span data-stu-id="929fb-109">EXAMPLES</span></span>

### <span data-ttu-id="929fb-110">예 1: WinRM 서비스의 상태 확인</span><span class="sxs-lookup"><span data-stu-id="929fb-110">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="929fb-111">이 명령은 WinRM 서비스가 로컬 컴퓨터에서 실행되고 있는지 또는 원격 컴퓨터에서 실행되고 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-111">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="929fb-112">예 2: 원격 컴퓨터의 WinRM 서비스 상태 확인</span><span class="sxs-lookup"><span data-stu-id="929fb-112">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="929fb-113">이 명령은 WinRM 서비스가 server01 컴퓨터에서 실행 되 고 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-113">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="929fb-114">예 3: WinRM 서비스 및 운영 체제 버전의 상태 확인</span><span class="sxs-lookup"><span data-stu-id="929fb-114">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="929fb-115">이 명령은 인증 매개 변수를 사용 하 여 WS-Management (WinRM) 서비스가 로컬 컴퓨터에서 실행 되 고 있는지를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-115">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="929fb-116">Authentication 매개 변수를 사용 하면 **테스트-WSMan** 에서 운영 체제 버전을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-116">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="929fb-117">예 4: 원격 컴퓨터의 WinRM 서비스 및 운영 체제 버전 상태 확인</span><span class="sxs-lookup"><span data-stu-id="929fb-117">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="929fb-118">이 명령은 인증 매개 변수를 사용 하 여 WS-Management (WinRM) 서비스가 server01 이라는 컴퓨터에서 실행 되 고 있는지를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-118">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="929fb-119">Authentication 매개 변수를 사용 하면 **테스트-WSMan** 에서 운영 체제 버전을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-119">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="929fb-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="929fb-120">PARAMETERS</span></span>

### <span data-ttu-id="929fb-121">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="929fb-121">-ApplicationName</span></span>

<span data-ttu-id="929fb-122">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-122">Specifies the application name in the connection.</span></span>
<span data-ttu-id="929fb-123">*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-123">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="929fb-124">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-124">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="929fb-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="929fb-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="929fb-126">예: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="929fb-126">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="929fb-127">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-127">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="929fb-128">이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-128">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="929fb-129">이 매개 변수는 많은 컴퓨터에서 PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-129">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="929fb-130">이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-130">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="929fb-131">-인증</span><span class="sxs-lookup"><span data-stu-id="929fb-131">-Authentication</span></span>

<span data-ttu-id="929fb-132">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-132">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="929fb-133">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="929fb-134">기본.</span><span class="sxs-lookup"><span data-stu-id="929fb-134">Basic.</span></span>
<span data-ttu-id="929fb-135">Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-135">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="929fb-136">기본값</span><span class="sxs-lookup"><span data-stu-id="929fb-136">Default.</span></span>
<span data-ttu-id="929fb-137">WS-Management 프로토콜로 구현된 인증 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-137">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="929fb-138">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-138">This is the default.</span></span>
- <span data-ttu-id="929fb-139">다이제스트.</span><span class="sxs-lookup"><span data-stu-id="929fb-139">Digest.</span></span>
<span data-ttu-id="929fb-140">Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-140">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="929fb-141">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="929fb-141">Kerberos.</span></span>
<span data-ttu-id="929fb-142">클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용하여 상호 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-142">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="929fb-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="929fb-143">Negotiate.</span></span>
<span data-ttu-id="929fb-144">Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-144">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="929fb-145">예를 들어이 매개 변수 값은 협상을 통해 Kerberos 프로토콜 또는 NTLM이 사용 되는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-145">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="929fb-146">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="929fb-146">CredSSP.</span></span>
<span data-ttu-id="929fb-147">사용자가 자격 증명을 위임할 수 있도록 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-147">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="929fb-148">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-148">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="929fb-149">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-149">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="929fb-150">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-150">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="929fb-151">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-151">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="929fb-152">중요: *인증* 매개 변수를 지정 하지 않으면 인증을 사용 하지 않고 **테스트 WSMan** 요청이 익명으로 원격 컴퓨터로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-152">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="929fb-153">요청을 익명으로 만든 경우에는 운영 체제 버전과 관련 된 정보를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-153">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="929fb-154">대신이 cmdlet은 운영 체제 버전 및 Service Pack 수준 (OS: 0.0.0 SP: 0.0)에 대 한 null 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-154">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="929fb-155">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="929fb-155">-CertificateThumbprint</span></span>

<span data-ttu-id="929fb-156">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-156">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="929fb-157">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-157">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="929fb-158">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-158">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="929fb-159">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-159">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="929fb-160">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-160">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="929fb-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="929fb-161">-ComputerName</span></span>

<span data-ttu-id="929fb-162">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-162">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="929fb-163">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-163">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="929fb-164">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-164">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="929fb-165">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-165">The local computer is the default.</span></span>
<span data-ttu-id="929fb-166">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-166">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="929fb-167">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-167">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="929fb-168">-Credential</span><span class="sxs-lookup"><span data-stu-id="929fb-168">-Credential</span></span>

<span data-ttu-id="929fb-169">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-169">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="929fb-170">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-170">The default is the current user.</span></span>
<span data-ttu-id="929fb-171">User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-171">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="929fb-172">또는 Get-Credential cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-172">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="929fb-173">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-173">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="929fb-174">-Port</span><span class="sxs-lookup"><span data-stu-id="929fb-174">-Port</span></span>

<span data-ttu-id="929fb-175">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-175">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="929fb-176">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-176">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="929fb-177">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-177">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="929fb-178">전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-178">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="929fb-179">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="929fb-179">-UseSSL</span></span>

<span data-ttu-id="929fb-180">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-180">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="929fb-181">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-181">By default, SSL is not used.</span></span>

<span data-ttu-id="929fb-182">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-182">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="929fb-183">*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-183">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="929fb-184">연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-184">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="929fb-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="929fb-185">CommonParameters</span></span>

<span data-ttu-id="929fb-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="929fb-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="929fb-187">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="929fb-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="929fb-188">입력</span><span class="sxs-lookup"><span data-stu-id="929fb-188">INPUTS</span></span>

### <span data-ttu-id="929fb-189">없음</span><span class="sxs-lookup"><span data-stu-id="929fb-189">None</span></span>

<span data-ttu-id="929fb-190">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-190">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="929fb-191">출력</span><span class="sxs-lookup"><span data-stu-id="929fb-191">OUTPUTS</span></span>

### <span data-ttu-id="929fb-192">없음</span><span class="sxs-lookup"><span data-stu-id="929fb-192">None</span></span>

<span data-ttu-id="929fb-193">이 cmdlet은 어떠한 출력 개체도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-193">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="929fb-194">참고</span><span class="sxs-lookup"><span data-stu-id="929fb-194">NOTES</span></span>

* <span data-ttu-id="929fb-195">기본적으로 **테스트-WSMan** cmdlet은 인증을 사용 하지 않고 WinRM 서비스를 쿼리 하며 운영 체제 버전과 관련 된 정보를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-195">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="929fb-196">대신, 운영 체제 버전 및 Service Pack 수준 (OS: 0.0.0 SP: 0.0)에 대 한 null 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="929fb-196">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

*

## <span data-ttu-id="929fb-197">관련 링크</span><span class="sxs-lookup"><span data-stu-id="929fb-197">RELATED LINKS</span></span>

[<span data-ttu-id="929fb-198">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="929fb-198">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="929fb-199">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="929fb-199">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="929fb-200">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="929fb-200">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="929fb-201">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="929fb-201">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="929fb-202">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="929fb-202">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="929fb-203">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="929fb-203">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="929fb-204">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="929fb-204">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="929fb-205">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="929fb-205">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="929fb-206">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="929fb-206">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="929fb-207">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="929fb-207">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="929fb-208">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="929fb-208">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="929fb-209">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="929fb-209">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

