---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 4d1273fe1ed643f8d45b627db9863b75212b6b24
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99604992"
---
# <span data-ttu-id="2e547-102">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e547-102">Remove-WSManInstance</span></span>

## <span data-ttu-id="2e547-103">개요</span><span class="sxs-lookup"><span data-stu-id="2e547-103">SYNOPSIS</span></span>
<span data-ttu-id="2e547-104">관리 리소스 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-104">Deletes a management resource instance.</span></span>

## <span data-ttu-id="2e547-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e547-105">SYNTAX</span></span>

### <span data-ttu-id="2e547-106">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="2e547-106">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="2e547-107">URI</span><span class="sxs-lookup"><span data-stu-id="2e547-107">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="2e547-108">설명</span><span class="sxs-lookup"><span data-stu-id="2e547-108">DESCRIPTION</span></span>

<span data-ttu-id="2e547-109">**Remove-WSManInstance** Cmdlet은 *ResourceURI* 및 *SelectorSet* 매개 변수에 지정 된 관리 리소스의 인스턴스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-109">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="2e547-110">이 cmdlet은 WinRM 연결/전송 계층을 사용하여 관리 리소스 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-110">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="2e547-111">예제</span><span class="sxs-lookup"><span data-stu-id="2e547-111">EXAMPLES</span></span>

### <span data-ttu-id="2e547-112">예제 1: 수신기 삭제</span><span class="sxs-lookup"><span data-stu-id="2e547-112">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="2e547-113">이 명령은 컴퓨터의 WS-Management HTTP 수신기를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-113">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="2e547-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e547-114">PARAMETERS</span></span>

### <span data-ttu-id="2e547-115">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="2e547-115">-ApplicationName</span></span>

<span data-ttu-id="2e547-116">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-116">Specifies the application name in the connection.</span></span>
<span data-ttu-id="2e547-117">*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-117">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="2e547-118">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-118">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="2e547-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="2e547-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="2e547-120">예: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="2e547-120">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="2e547-121">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="2e547-122">이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-122">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="2e547-123">이 매개 변수는 많은 컴퓨터에서 PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-123">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="2e547-124">이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e547-125">-인증</span><span class="sxs-lookup"><span data-stu-id="2e547-125">-Authentication</span></span>

<span data-ttu-id="2e547-126">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-126">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="2e547-127">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-127">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2e547-128">기본.</span><span class="sxs-lookup"><span data-stu-id="2e547-128">Basic.</span></span>
<span data-ttu-id="2e547-129">Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-129">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="2e547-130">기본값</span><span class="sxs-lookup"><span data-stu-id="2e547-130">Default.</span></span>
<span data-ttu-id="2e547-131">WS-Management 프로토콜로 구현된 인증 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-131">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="2e547-132">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-132">This is the default.</span></span>
- <span data-ttu-id="2e547-133">다이제스트.</span><span class="sxs-lookup"><span data-stu-id="2e547-133">Digest.</span></span>
<span data-ttu-id="2e547-134">Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-134">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="2e547-135">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="2e547-135">Kerberos.</span></span>
<span data-ttu-id="2e547-136">클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용하여 상호 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-136">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="2e547-137">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2e547-137">Negotiate.</span></span>
<span data-ttu-id="2e547-138">Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-138">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="2e547-139">예를 들어이 매개 변수 값은 협상을 통해 Kerberos 프로토콜 또는 NTLM이 사용 되는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-139">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="2e547-140">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="2e547-140">CredSSP.</span></span>
<span data-ttu-id="2e547-141">사용자가 자격 증명을 위임할 수 있도록 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-141">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="2e547-142">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-142">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="2e547-143">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-143">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="2e547-144">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-144">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="2e547-145">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-145">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="2e547-146">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="2e547-146">-CertificateThumbprint</span></span>

<span data-ttu-id="2e547-147">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-147">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="2e547-148">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-148">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="2e547-149">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-149">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="2e547-150">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-150">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="2e547-151">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-151">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="2e547-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2e547-152">-ComputerName</span></span>

<span data-ttu-id="2e547-153">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-153">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="2e547-154">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-154">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="2e547-155">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-155">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="2e547-156">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-156">The local computer is the default.</span></span>
<span data-ttu-id="2e547-157">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-157">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="2e547-158">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-158">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e547-159">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="2e547-159">-ConnectionURI</span></span>

<span data-ttu-id="2e547-160">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-160">Specifies the connection endpoint.</span></span>
<span data-ttu-id="2e547-161">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-161">The format of this string is as follows:</span></span>

<span data-ttu-id="2e547-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="2e547-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="2e547-163">다음 문자열은이 매개 변수의 형식이 올바르게 지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-163">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="2e547-164">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-164">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e547-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="2e547-165">-Credential</span></span>

<span data-ttu-id="2e547-166">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-166">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="2e547-167">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-167">The default is the current user.</span></span>
<span data-ttu-id="2e547-168">User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="2e547-169">또는 Get-Credential cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-169">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="2e547-170">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-170">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="2e547-171">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="2e547-171">-OptionSet</span></span>

<span data-ttu-id="2e547-172">요청의 특성을 수정 하거나 구체화 하기 위해 서비스에 대 한 스위치 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-172">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="2e547-173">이러한 스위치는 서비스 마다 다르기 때문에 명령줄 셸에 사용 되는 스위치와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-173">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="2e547-174">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-174">Any number of options can be specified.</span></span>

<span data-ttu-id="2e547-175">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="2e547-176">-Port</span><span class="sxs-lookup"><span data-stu-id="2e547-176">-Port</span></span>

<span data-ttu-id="2e547-177">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-177">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="2e547-178">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-178">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="2e547-179">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="2e547-180">전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-180">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="2e547-181">그러나 *Skipcncheck* 매개 변수가 *sessionoption* 매개 변수의 일부로 지정 된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-181">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="2e547-182">*Skipcncheck* 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-182">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="2e547-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="2e547-183">-ResourceURI</span></span>

<span data-ttu-id="2e547-184">리소스 클래스 또는 인스턴스의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-184">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="2e547-185">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="2e547-186">URI는 접두사와 리소스 경로로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-186">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="2e547-187">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="2e547-187">For example:</span></span>

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

### <span data-ttu-id="2e547-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="2e547-188">-SelectorSet</span></span>

<span data-ttu-id="2e547-189">특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="2e547-190">*SelectorSet* 매개 변수는 리소스의 인스턴스가 둘 이상 있을 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-190">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="2e547-191">*SelectorSet* 의 값은 해시 테이블 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-191">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="2e547-192">다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2e547-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="2e547-193">-SessionOption</span></span>

<span data-ttu-id="2e547-194">WS-Management 세션에 대 한 확장 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-194">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="2e547-195">New-WSManSessionOption cmdlet을 사용 하 여 만든 **Sessionoption** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-195">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="2e547-196">사용할 수 있는 옵션에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="2e547-196">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="2e547-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="2e547-197">-UseSSL</span></span>

<span data-ttu-id="2e547-198">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-198">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="2e547-199">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-199">By default, SSL is not used.</span></span>

<span data-ttu-id="2e547-200">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-200">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="2e547-201">*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-201">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="2e547-202">연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-202">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e547-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e547-203">CommonParameters</span></span>

<span data-ttu-id="2e547-204">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e547-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e547-205">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e547-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e547-206">입력</span><span class="sxs-lookup"><span data-stu-id="2e547-206">INPUTS</span></span>

### <span data-ttu-id="2e547-207">없음</span><span class="sxs-lookup"><span data-stu-id="2e547-207">None</span></span>

<span data-ttu-id="2e547-208">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-208">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="2e547-209">출력</span><span class="sxs-lookup"><span data-stu-id="2e547-209">OUTPUTS</span></span>

### <span data-ttu-id="2e547-210">없음</span><span class="sxs-lookup"><span data-stu-id="2e547-210">None</span></span>

<span data-ttu-id="2e547-211">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-211">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2e547-212">참고</span><span class="sxs-lookup"><span data-stu-id="2e547-212">NOTES</span></span>

* <span data-ttu-id="2e547-213">WMI(Windows Management Instrumentation) cmdlet인 Remove-WmiObject cmdlet은 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-213">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="2e547-214">**Get-wmiobject** 은 DCOM 연결/전송 계층을 사용 하 여 WMI 인스턴스를 만들거나 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e547-214">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="2e547-215">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2e547-215">RELATED LINKS</span></span>

[<span data-ttu-id="2e547-216">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="2e547-216">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="2e547-217">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2e547-217">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="2e547-218">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="2e547-218">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="2e547-219">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2e547-219">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="2e547-220">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2e547-220">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="2e547-221">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e547-221">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="2e547-222">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="2e547-222">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="2e547-223">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e547-223">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="2e547-224">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="2e547-224">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="2e547-225">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e547-225">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="2e547-226">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="2e547-226">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="2e547-227">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="2e547-227">Test-WSMan</span></span>](Test-WSMan.md)
