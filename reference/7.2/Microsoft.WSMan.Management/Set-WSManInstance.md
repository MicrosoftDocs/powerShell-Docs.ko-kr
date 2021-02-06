---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2e5d68c2a75ea3040fd3998d2dc469200c054e58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605255"
---
# <span data-ttu-id="adefc-102">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="adefc-102">Set-WSManInstance</span></span>

## <span data-ttu-id="adefc-103">개요</span><span class="sxs-lookup"><span data-stu-id="adefc-103">SYNOPSIS</span></span>
<span data-ttu-id="adefc-104">리소스와 관련된 관리 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-104">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="adefc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="adefc-105">SYNTAX</span></span>

### <span data-ttu-id="adefc-106">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="adefc-106">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="adefc-107">URI</span><span class="sxs-lookup"><span data-stu-id="adefc-107">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="adefc-108">설명</span><span class="sxs-lookup"><span data-stu-id="adefc-108">DESCRIPTION</span></span>

<span data-ttu-id="adefc-109">Set-WSManInstance cmdlet은 리소스와 관련된 관리 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-109">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="adefc-110">이 cmdlet은 WinRM 연결/전송 계층을 사용하여 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-110">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="adefc-111">예제</span><span class="sxs-lookup"><span data-stu-id="adefc-111">EXAMPLES</span></span>

### <span data-ttu-id="adefc-112">예제 1: 로컬 컴퓨터에서 수신기를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="adefc-112">Example 1: Disable a listener on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

<span data-ttu-id="adefc-113">이 명령은 로컬 컴퓨터에 https 수신기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-113">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="adefc-114">중요: *Valueset* 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-114">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="adefc-115">예를 들어이 명령에서</span><span class="sxs-lookup"><span data-stu-id="adefc-115">For example, in this command,</span></span>

<span data-ttu-id="adefc-116">실패: `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="adefc-116">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="adefc-117">성공: `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="adefc-117">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="adefc-118">예 2: 로컬 컴퓨터의 최대 봉투 크기 설정</span><span class="sxs-lookup"><span data-stu-id="adefc-118">Example 2: Set the maximum envelope size on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

<span data-ttu-id="adefc-119">이 명령은 로컬 컴퓨터에 MaxEnvelopeSizekb 값을 200으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-119">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="adefc-120">중요: ValueSet 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-120">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="adefc-121">예를 들어 위의 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-121">For example, using the above command.</span></span>

<span data-ttu-id="adefc-122">실패:-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="adefc-122">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="adefc-123">성공:-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="adefc-123">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="adefc-124">예제 3: 원격 컴퓨터에서 수신기 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="adefc-124">Example 3: Disable a listener on a remote computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

<span data-ttu-id="adefc-125">이 명령은 원격 컴퓨터 SERVER02에 https 수신기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-125">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="adefc-126">중요: ValueSet 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-126">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="adefc-127">예를 들어 위의 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-127">For example, using the above command.</span></span>

<span data-ttu-id="adefc-128">실패:-ValueSet @ {enabled = "False"}</span><span class="sxs-lookup"><span data-stu-id="adefc-128">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="adefc-129">성공:-ValueSet @ {Enabled = "False"}</span><span class="sxs-lookup"><span data-stu-id="adefc-129">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="adefc-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="adefc-130">PARAMETERS</span></span>

### <span data-ttu-id="adefc-131">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="adefc-131">-ApplicationName</span></span>

<span data-ttu-id="adefc-132">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-132">Specifies the application name in the connection.</span></span>
<span data-ttu-id="adefc-133">ApplicationName 매개 변수의 기본값은 "WSMAN"입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-133">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="adefc-134">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-134">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="adefc-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="adefc-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="adefc-136">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="adefc-136">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="adefc-137">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-137">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="adefc-138">"WSMAN"의 이 기본 설정은 대부분의 사용자에게 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-138">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="adefc-139">이 매개 변수는 많은 컴퓨터에서 Windows PowerShell을 실행하는 한 컴퓨터에 대한 원격 연결을 설정할 때 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-139">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="adefc-140">이 경우 IIS는 효율성을 위해 WS-Management(관리용 웹 서비스)를 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-140">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="adefc-141">-인증</span><span class="sxs-lookup"><span data-stu-id="adefc-141">-Authentication</span></span>

<span data-ttu-id="adefc-142">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-142">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="adefc-143">가능한 값은</span><span class="sxs-lookup"><span data-stu-id="adefc-143">Possible values are:</span></span>

- <span data-ttu-id="adefc-144">Basic: Basic은 사용자 이름과 암호가 일반 텍스트로 서버 또는 프록시에 전송 되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-144">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="adefc-145">기본값: WS-Management 프로토콜에 의해 구현 된 인증 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-145">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="adefc-146">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-146">This is the default.</span></span>
- <span data-ttu-id="adefc-147">다이제스트: 다이제스트는 챌린지에 대해 서버 지정 데이터 문자열을 사용 하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-147">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="adefc-148">Kerberos: 클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용 하 여 상호 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-148">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="adefc-149">Negotiate: Negotiate는 인증에 사용할 체계를 결정 하기 위해 서버 또는 프록시와 협상 하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-149">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="adefc-150">예를 들어 이 매개 변수 값을 통해 협상에서 Kerberos 프로토콜이 사용되는지 또는 NTLM이 사용되는지를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-150">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="adefc-151">CredSSP: 사용자가 자격 증명을 위임할 수 있도록 허용 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-151">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="adefc-152">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-152">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="adefc-153">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-153">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="adefc-154">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-154">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="adefc-155">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-155">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adefc-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="adefc-156">-CertificateThumbprint</span></span>

<span data-ttu-id="adefc-157">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="adefc-158">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="adefc-159">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="adefc-160">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="adefc-161">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="adefc-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="adefc-162">-ComputerName</span></span>

<span data-ttu-id="adefc-163">관리 작업을 실행하려는 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-163">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="adefc-164">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="adefc-165">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="adefc-166">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-166">The local computer is the default.</span></span>
<span data-ttu-id="adefc-167">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="adefc-168">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-168">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="adefc-169">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="adefc-169">-ConnectionURI</span></span>

<span data-ttu-id="adefc-170">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-170">Specifies the connection endpoint.</span></span>
<span data-ttu-id="adefc-171">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-171">The format of this string is:</span></span>

<span data-ttu-id="adefc-172">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="adefc-172">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="adefc-173">다음 문자열은 이 매개 변수의 형식이 올바르게 지정된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-173">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="adefc-174">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-174">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="adefc-175">-Credential</span><span class="sxs-lookup"><span data-stu-id="adefc-175">-Credential</span></span>

<span data-ttu-id="adefc-176">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-176">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="adefc-177">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-177">The default is the current user.</span></span>
<span data-ttu-id="adefc-178">사용자 이름 (예: "User01", "Domain01\User01" 또는 "")을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-178">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="adefc-179">또는 PSCredential 개체(예: Get-Credential cmdlet에서 반환된 개체)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-179">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="adefc-180">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-180">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="adefc-181">-언어</span><span class="sxs-lookup"><span data-stu-id="adefc-181">-Dialect</span></span>

<span data-ttu-id="adefc-182">필터 조건자에 사용할 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-182">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="adefc-183">원격 서비스에서 지원되는 모든 언어가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-183">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="adefc-184">언어 URI에 다음과 같은 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-184">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="adefc-185">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="adefc-185">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="adefc-186">선택기 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="adefc-186">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="adefc-187">연결 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="adefc-187">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adefc-188">-FilePath</span><span class="sxs-lookup"><span data-stu-id="adefc-188">-FilePath</span></span>

<span data-ttu-id="adefc-189">관리 리소스를 업데이트하는 데 사용되는 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-189">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="adefc-190">ResourceURI 매개 변수 및 SelectorSet 매개 변수를 사용하여 관리 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-190">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="adefc-191">예를 들어 다음 명령은 FilePath 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-191">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="adefc-192">이 명령은 파일의 입력을 사용하여 스풀러 서비스에 대해 StopService 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-192">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="adefc-193">Input.xml 파일은 다음 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-193">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="adefc-194">-조각</span><span class="sxs-lookup"><span data-stu-id="adefc-194">-Fragment</span></span>

<span data-ttu-id="adefc-195">지정된 작업을 위해 업데이트하거나 검색할 인스턴스 내의 섹션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-195">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="adefc-196">예를 들어 스풀러 서비스의 상태를 가져오려면 "-Fragment Status"를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-196">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="adefc-197">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="adefc-197">-OptionSet</span></span>

<span data-ttu-id="adefc-198">요청의 특성을 수정하거나 구체화하기 위해 스위치 집합을 서비스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-198">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="adefc-199">이는 명령줄 셸에 사용되는 스위치와 유사한데, 서비스에 국한되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-199">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="adefc-200">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-200">Any number of options can be specified.</span></span>

<span data-ttu-id="adefc-201">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-201">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="adefc-202">-OptionSet @{a=1;b=2;c=3}</span><span class="sxs-lookup"><span data-stu-id="adefc-202">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="adefc-203">-Port</span><span class="sxs-lookup"><span data-stu-id="adefc-203">-Port</span></span>

<span data-ttu-id="adefc-204">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-204">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="adefc-205">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-205">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="adefc-206">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-206">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="adefc-207">전송으로 HTTPS를 사용하는 경우 ComputerName 매개 변수 값이 서버의 인증서 CN(일반 이름)과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-207">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="adefc-208">그러나 SkipCNCheck 매개 변수가 SessionOption 매개 변수 서버의 일부로 지정된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-208">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="adefc-209">SkipCNCheck 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-209">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="adefc-210">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="adefc-210">-ResourceURI</span></span>

<span data-ttu-id="adefc-211">리소스 클래스 또는 인스턴스의 URI(Uniform Resource Identifier)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-211">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="adefc-212">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-212">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="adefc-213">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-213">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="adefc-214">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="adefc-214">For example:</span></span>

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

### <span data-ttu-id="adefc-215">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="adefc-215">-SelectorSet</span></span>

<span data-ttu-id="adefc-216">특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-216">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="adefc-217">SelectorSet 매개 변수는 리소스의 인스턴스가 둘 이상 존재하는 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-217">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="adefc-218">SelectorSet 매개 변수 값은 해시 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-218">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="adefc-219">다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-219">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="adefc-220">-SelectorSet @{Name="WinRM";ID="yyy"}</span><span class="sxs-lookup"><span data-stu-id="adefc-220">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="adefc-221">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="adefc-221">-SessionOption</span></span>

<span data-ttu-id="adefc-222">WS-Management 세션에 대한 확장된 옵션 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-222">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="adefc-223">New-WSManSessionOption cmdlet을 사용하여 만든 SessionOption 개체를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-223">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="adefc-224">사용할 수 있는 옵션에 대한 자세한 내용은 New-WSManSessionOption을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adefc-224">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="adefc-225">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="adefc-225">-UseSSL</span></span>

<span data-ttu-id="adefc-226">원격 컴퓨터에 대한 연결을 설정할 때 SSL(Secure Sockets Layer) 프로토콜이 반드시 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-226">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="adefc-227">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-227">By default, SSL is not used.</span></span>

<span data-ttu-id="adefc-228">WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-228">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="adefc-229">UseSSL 매개 변수를 사용하여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-229">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="adefc-230">연결에 사용되는 포트에 SSL을 사용할 수 없는 경우에 이 매개 변수를 지정하면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-230">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="adefc-231">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="adefc-231">-ValueSet</span></span>

<span data-ttu-id="adefc-232">관리 리소스를 수정하는 데 도움이 되는 해시 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-232">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="adefc-233">ResourceURI 매개 변수 및 SelectorSet 매개 변수를 사용하여 관리 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-233">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="adefc-234">ValueSet 매개 변수 값은 해시 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-234">The value of the ValueSet parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="adefc-235">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="adefc-235">CommonParameters</span></span>

<span data-ttu-id="adefc-236">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="adefc-236">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="adefc-237">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adefc-237">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="adefc-238">입력</span><span class="sxs-lookup"><span data-stu-id="adefc-238">INPUTS</span></span>

### <span data-ttu-id="adefc-239">없음</span><span class="sxs-lookup"><span data-stu-id="adefc-239">None</span></span>

<span data-ttu-id="adefc-240">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-240">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="adefc-241">출력</span><span class="sxs-lookup"><span data-stu-id="adefc-241">OUTPUTS</span></span>

### <span data-ttu-id="adefc-242">없음</span><span class="sxs-lookup"><span data-stu-id="adefc-242">None</span></span>

<span data-ttu-id="adefc-243">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="adefc-243">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="adefc-244">참고</span><span class="sxs-lookup"><span data-stu-id="adefc-244">NOTES</span></span>

## <span data-ttu-id="adefc-245">관련 링크</span><span class="sxs-lookup"><span data-stu-id="adefc-245">RELATED LINKS</span></span>

[<span data-ttu-id="adefc-246">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="adefc-246">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="adefc-247">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="adefc-247">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="adefc-248">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="adefc-248">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="adefc-249">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="adefc-249">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="adefc-250">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="adefc-250">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="adefc-251">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="adefc-251">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="adefc-252">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="adefc-252">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="adefc-253">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="adefc-253">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="adefc-254">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="adefc-254">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="adefc-255">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="adefc-255">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="adefc-256">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="adefc-256">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="adefc-257">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="adefc-257">Test-WSMan</span></span>](Test-WSMan.md)

