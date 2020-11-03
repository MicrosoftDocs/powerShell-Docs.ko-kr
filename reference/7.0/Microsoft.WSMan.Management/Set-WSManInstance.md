---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2547efe8c3784d29fe852288a8442ac17335fe52
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218338"
---
# <span data-ttu-id="ec5da-103">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec5da-103">Set-WSManInstance</span></span>

## <span data-ttu-id="ec5da-104">개요</span><span class="sxs-lookup"><span data-stu-id="ec5da-104">SYNOPSIS</span></span>
<span data-ttu-id="ec5da-105">리소스와 관련된 관리 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-105">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="ec5da-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ec5da-106">SYNTAX</span></span>

### <span data-ttu-id="ec5da-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="ec5da-107">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="ec5da-108">URI</span><span class="sxs-lookup"><span data-stu-id="ec5da-108">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="ec5da-109">설명</span><span class="sxs-lookup"><span data-stu-id="ec5da-109">DESCRIPTION</span></span>

<span data-ttu-id="ec5da-110">Set-WSManInstance cmdlet은 리소스와 관련된 관리 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-110">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="ec5da-111">이 cmdlet은 WinRM 연결/전송 계층을 사용하여 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-111">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="ec5da-112">예제</span><span class="sxs-lookup"><span data-stu-id="ec5da-112">EXAMPLES</span></span>

### <span data-ttu-id="ec5da-113">예제 1: 로컬 컴퓨터에서 수신기를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="ec5da-113">Example 1: Disable a listener on the local computer</span></span>

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

<span data-ttu-id="ec5da-114">이 명령은 로컬 컴퓨터에 https 수신기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-114">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="ec5da-115">중요: *Valueset* 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-115">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="ec5da-116">예를 들어이 명령에서</span><span class="sxs-lookup"><span data-stu-id="ec5da-116">For example, in this command,</span></span>

<span data-ttu-id="ec5da-117">실패: `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="ec5da-117">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="ec5da-118">성공: `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="ec5da-118">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="ec5da-119">예 2: 로컬 컴퓨터의 최대 봉투 크기 설정</span><span class="sxs-lookup"><span data-stu-id="ec5da-119">Example 2: Set the maximum envelope size on the local computer</span></span>

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

<span data-ttu-id="ec5da-120">이 명령은 로컬 컴퓨터에 MaxEnvelopeSizekb 값을 200으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-120">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="ec5da-121">중요: ValueSet 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-121">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="ec5da-122">예를 들어 위의 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-122">For example, using the above command.</span></span>

<span data-ttu-id="ec5da-123">실패:-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="ec5da-123">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="ec5da-124">성공:-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="ec5da-124">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="ec5da-125">예제 3: 원격 컴퓨터에서 수신기 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="ec5da-125">Example 3: Disable a listener on a remote computer</span></span>

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

<span data-ttu-id="ec5da-126">이 명령은 원격 컴퓨터 SERVER02에 https 수신기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-126">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="ec5da-127">중요: ValueSet 매개 변수는 지정 된 속성과 일치 하는 경우 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-127">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="ec5da-128">예를 들어 위의 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-128">For example, using the above command.</span></span>

<span data-ttu-id="ec5da-129">실패:-ValueSet @ {enabled = "False"}</span><span class="sxs-lookup"><span data-stu-id="ec5da-129">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="ec5da-130">성공:-ValueSet @ {Enabled = "False"}</span><span class="sxs-lookup"><span data-stu-id="ec5da-130">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="ec5da-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ec5da-131">PARAMETERS</span></span>

### <span data-ttu-id="ec5da-132">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="ec5da-132">-ApplicationName</span></span>

<span data-ttu-id="ec5da-133">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-133">Specifies the application name in the connection.</span></span>
<span data-ttu-id="ec5da-134">ApplicationName 매개 변수의 기본값은 "WSMAN"입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-134">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="ec5da-135">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-135">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="ec5da-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="ec5da-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="ec5da-137">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="ec5da-137">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="ec5da-138">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-138">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="ec5da-139">"WSMAN"의 이 기본 설정은 대부분의 사용자에게 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-139">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="ec5da-140">이 매개 변수는 많은 컴퓨터에서 Windows PowerShell을 실행하는 한 컴퓨터에 대한 원격 연결을 설정할 때 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-140">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="ec5da-141">이 경우 IIS는 효율성을 위해 WS-Management(관리용 웹 서비스)를 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-141">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="ec5da-142">-인증</span><span class="sxs-lookup"><span data-stu-id="ec5da-142">-Authentication</span></span>

<span data-ttu-id="ec5da-143">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-143">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="ec5da-144">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-144">Possible values are:</span></span>

- <span data-ttu-id="ec5da-145">Basic: Basic은 사용자 이름과 암호가 일반 텍스트로 서버 또는 프록시에 전송 되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-145">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="ec5da-146">기본값: WS-Management 프로토콜에 의해 구현 된 인증 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-146">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="ec5da-147">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-147">This is the default.</span></span>
- <span data-ttu-id="ec5da-148">다이제스트: 다이제스트는 챌린지에 대해 서버 지정 데이터 문자열을 사용 하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-148">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="ec5da-149">Kerberos: 클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용 하 여 상호 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-149">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="ec5da-150">Negotiate: Negotiate는 인증에 사용할 체계를 결정 하기 위해 서버 또는 프록시와 협상 하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-150">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="ec5da-151">예를 들어 이 매개 변수 값을 통해 협상에서 Kerberos 프로토콜이 사용되는지 또는 NTLM이 사용되는지를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-151">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="ec5da-152">CredSSP: 사용자가 자격 증명을 위임할 수 있도록 허용 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-152">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="ec5da-153">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-153">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="ec5da-154">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-154">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="ec5da-155">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-155">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="ec5da-156">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-156">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="ec5da-157">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="ec5da-157">-CertificateThumbprint</span></span>

<span data-ttu-id="ec5da-158">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-158">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ec5da-159">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-159">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="ec5da-160">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-160">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="ec5da-161">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-161">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="ec5da-162">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-162">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="ec5da-163">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ec5da-163">-ComputerName</span></span>

<span data-ttu-id="ec5da-164">관리 작업을 실행하려는 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-164">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="ec5da-165">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-165">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="ec5da-166">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-166">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="ec5da-167">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-167">The local computer is the default.</span></span>
<span data-ttu-id="ec5da-168">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-168">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="ec5da-169">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-169">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="ec5da-170">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="ec5da-170">-ConnectionURI</span></span>

<span data-ttu-id="ec5da-171">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-171">Specifies the connection endpoint.</span></span>
<span data-ttu-id="ec5da-172">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-172">The format of this string is:</span></span>

<span data-ttu-id="ec5da-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="ec5da-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="ec5da-174">다음 문자열은 이 매개 변수의 형식이 올바르게 지정된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-174">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="ec5da-175">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-175">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="ec5da-176">-Credential</span><span class="sxs-lookup"><span data-stu-id="ec5da-176">-Credential</span></span>

<span data-ttu-id="ec5da-177">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-177">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ec5da-178">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-178">The default is the current user.</span></span>
<span data-ttu-id="ec5da-179">사용자 이름 (예: "User01", "Domain01\User01" 또는 "")을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-179">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="ec5da-180">또는 PSCredential 개체(예: Get-Credential cmdlet에서 반환된 개체)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-180">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="ec5da-181">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-181">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="ec5da-182">-언어</span><span class="sxs-lookup"><span data-stu-id="ec5da-182">-Dialect</span></span>

<span data-ttu-id="ec5da-183">필터 조건자에 사용할 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-183">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="ec5da-184">원격 서비스에서 지원되는 모든 언어가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-184">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="ec5da-185">언어 URI에 다음과 같은 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-185">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="ec5da-186">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="ec5da-186">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="ec5da-187">선택기 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="ec5da-187">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="ec5da-188">연결 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="ec5da-188">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

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

### <span data-ttu-id="ec5da-189">-FilePath</span><span class="sxs-lookup"><span data-stu-id="ec5da-189">-FilePath</span></span>

<span data-ttu-id="ec5da-190">관리 리소스를 업데이트하는 데 사용되는 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-190">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="ec5da-191">ResourceURI 매개 변수 및 SelectorSet 매개 변수를 사용하여 관리 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-191">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="ec5da-192">예를 들어 다음 명령은 FilePath 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-192">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="ec5da-193">이 명령은 파일의 입력을 사용하여 스풀러 서비스에 대해 StopService 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-193">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="ec5da-194">Input.xml 파일은 다음 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-194">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="ec5da-195">-조각</span><span class="sxs-lookup"><span data-stu-id="ec5da-195">-Fragment</span></span>

<span data-ttu-id="ec5da-196">지정된 작업을 위해 업데이트하거나 검색할 인스턴스 내의 섹션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-196">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="ec5da-197">예를 들어 스풀러 서비스의 상태를 가져오려면 "-Fragment Status"를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-197">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="ec5da-198">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="ec5da-198">-OptionSet</span></span>

<span data-ttu-id="ec5da-199">요청의 특성을 수정하거나 구체화하기 위해 스위치 집합을 서비스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-199">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="ec5da-200">이는 명령줄 셸에 사용되는 스위치와 유사한데, 서비스에 국한되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-200">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="ec5da-201">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-201">Any number of options can be specified.</span></span>

<span data-ttu-id="ec5da-202">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-202">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="ec5da-203">-OptionSet @{a=1;b=2;c=3}</span><span class="sxs-lookup"><span data-stu-id="ec5da-203">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="ec5da-204">-Port</span><span class="sxs-lookup"><span data-stu-id="ec5da-204">-Port</span></span>

<span data-ttu-id="ec5da-205">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-205">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="ec5da-206">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-206">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="ec5da-207">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-207">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="ec5da-208">전송으로 HTTPS를 사용하는 경우 ComputerName 매개 변수 값이 서버의 인증서 CN(일반 이름)과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-208">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="ec5da-209">그러나 SkipCNCheck 매개 변수가 SessionOption 매개 변수 서버의 일부로 지정된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-209">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="ec5da-210">SkipCNCheck 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-210">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="ec5da-211">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="ec5da-211">-ResourceURI</span></span>

<span data-ttu-id="ec5da-212">리소스 클래스 또는 인스턴스의 URI(Uniform Resource Identifier)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-212">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="ec5da-213">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-213">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="ec5da-214">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-214">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="ec5da-215">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="ec5da-215">For example:</span></span>

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

### <span data-ttu-id="ec5da-216">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="ec5da-216">-SelectorSet</span></span>

<span data-ttu-id="ec5da-217">특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-217">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="ec5da-218">SelectorSet 매개 변수는 리소스의 인스턴스가 둘 이상 존재하는 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-218">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="ec5da-219">SelectorSet 매개 변수 값은 해시 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-219">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="ec5da-220">다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-220">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="ec5da-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span><span class="sxs-lookup"><span data-stu-id="ec5da-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

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

### <span data-ttu-id="ec5da-222">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="ec5da-222">-SessionOption</span></span>

<span data-ttu-id="ec5da-223">WS-Management 세션에 대한 확장된 옵션 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-223">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="ec5da-224">New-WSManSessionOption cmdlet을 사용하여 만든 SessionOption 개체를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-224">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="ec5da-225">사용할 수 있는 옵션에 대한 자세한 내용은 New-WSManSessionOption을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec5da-225">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="ec5da-226">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="ec5da-226">-UseSSL</span></span>

<span data-ttu-id="ec5da-227">원격 컴퓨터에 대한 연결을 설정할 때 SSL(Secure Sockets Layer) 프로토콜이 반드시 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-227">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="ec5da-228">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-228">By default, SSL is not used.</span></span>

<span data-ttu-id="ec5da-229">WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-229">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="ec5da-230">UseSSL 매개 변수를 사용하여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-230">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="ec5da-231">연결에 사용되는 포트에 SSL을 사용할 수 없는 경우에 이 매개 변수를 지정하면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-231">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="ec5da-232">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="ec5da-232">-ValueSet</span></span>

<span data-ttu-id="ec5da-233">관리 리소스를 수정하는 데 도움이 되는 해시 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-233">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="ec5da-234">ResourceURI 매개 변수 및 SelectorSet 매개 변수를 사용하여 관리 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-234">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="ec5da-235">ValueSet 매개 변수 값은 해시 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-235">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="ec5da-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ec5da-236">CommonParameters</span></span>

<span data-ttu-id="ec5da-237">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ec5da-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ec5da-238">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec5da-238">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ec5da-239">입력</span><span class="sxs-lookup"><span data-stu-id="ec5da-239">INPUTS</span></span>

### <span data-ttu-id="ec5da-240">없음</span><span class="sxs-lookup"><span data-stu-id="ec5da-240">None</span></span>

<span data-ttu-id="ec5da-241">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-241">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="ec5da-242">출력</span><span class="sxs-lookup"><span data-stu-id="ec5da-242">OUTPUTS</span></span>

### <span data-ttu-id="ec5da-243">없음</span><span class="sxs-lookup"><span data-stu-id="ec5da-243">None</span></span>

<span data-ttu-id="ec5da-244">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5da-244">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ec5da-245">참고</span><span class="sxs-lookup"><span data-stu-id="ec5da-245">NOTES</span></span>

## <span data-ttu-id="ec5da-246">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ec5da-246">RELATED LINKS</span></span>

[<span data-ttu-id="ec5da-247">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ec5da-247">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="ec5da-248">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ec5da-248">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="ec5da-249">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ec5da-249">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="ec5da-250">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ec5da-250">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="ec5da-251">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ec5da-251">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="ec5da-252">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec5da-252">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="ec5da-253">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="ec5da-253">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="ec5da-254">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec5da-254">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="ec5da-255">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="ec5da-255">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="ec5da-256">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec5da-256">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="ec5da-257">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="ec5da-257">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="ec5da-258">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="ec5da-258">Test-WSMan</span></span>](Test-WSMan.md)
