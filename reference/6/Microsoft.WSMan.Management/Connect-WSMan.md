---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: d06ede0e27713b1a309aa2ed265f02881d34124e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217089"
---
# <span data-ttu-id="e32ac-103">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e32ac-103">Connect-WSMan</span></span>

## <span data-ttu-id="e32ac-104">개요</span><span class="sxs-lookup"><span data-stu-id="e32ac-104">SYNOPSIS</span></span>
<span data-ttu-id="e32ac-105">원격 컴퓨터의 WinRM 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-105">Connects to the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="e32ac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e32ac-106">SYNTAX</span></span>

### <span data-ttu-id="e32ac-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="e32ac-107">ComputerName (Default)</span></span>

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="e32ac-108">URI</span><span class="sxs-lookup"><span data-stu-id="e32ac-108">URI</span></span>

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="e32ac-109">설명</span><span class="sxs-lookup"><span data-stu-id="e32ac-109">DESCRIPTION</span></span>
<span data-ttu-id="e32ac-110">**연결-WSMan** cmdlet은 원격 컴퓨터의 WinRM 서비스에 연결 하 고 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-110">The **Connect-WSMan** cmdlet connects to the WinRM service on a remote computer, and it establishes a persistent connection to the remote computer.</span></span>
<span data-ttu-id="e32ac-111">WSMan 공급자의 컨텍스트에서이 cmdlet을 사용 하 여 원격 컴퓨터의 WinRM 서비스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-111">You can use this cmdlet in the context of the WSMan provider to connect to the WinRM service on a remote computer.</span></span>
<span data-ttu-id="e32ac-112">그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-112">However, you can also use this cmdlet to connect to the WinRM service on a remote computer before you change to the WSMan provider.</span></span>
<span data-ttu-id="e32ac-113">원격 컴퓨터는 WSMan 공급자의 루트 디렉터리에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-113">The remote computer appears in the root directory of the WSMan provider.</span></span>

<span data-ttu-id="e32ac-114">클라이언트 컴퓨터와 서버 컴퓨터가 서로 다른 도메인 또는 작업 그룹에 있는 경우에는 명시적 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-114">Explicit credentials are required when the client and server computers are in different domains or workgroups.</span></span>

<span data-ttu-id="e32ac-115">원격 컴퓨터의 WinRM 서비스에서 연결을 끊는 방법에 대 한 자세한 내용은 Disconnect-WSMan cmdlet을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e32ac-115">For information about how to disconnect from the WinRM service on a remote computer, see the Disconnect-WSMan cmdlet.</span></span>

## <span data-ttu-id="e32ac-116">예제</span><span class="sxs-lookup"><span data-stu-id="e32ac-116">EXAMPLES</span></span>

### <span data-ttu-id="e32ac-117">예 1: 원격 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="e32ac-117">Example 1: Connect to a remote computer</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="e32ac-118">이 명령은 원격 server01 컴퓨터에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-118">This command creates a connection to the remote server01 computer.</span></span>

<span data-ttu-id="e32ac-119">**연결-wsman** cmdlet은 일반적으로 원격 컴퓨터 (이 경우 server01 컴퓨터)에 연결 하기 위해 wsman 공급자의 컨텍스트에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-119">The **Connect-WSMan** cmdlet is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="e32ac-120">그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터에 대한 연결을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="e32ac-121">이러한 연결은 **ComputerName** 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-121">Those connections appear in the **ComputerName** list.</span></span>

### <span data-ttu-id="e32ac-122">예 2: 관리자 자격 증명을 사용 하 여 원격 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="e32ac-122">Example 2: Connect to a remote computer by using Administrator credentials</span></span>

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="e32ac-123">이 명령은 관리자 계정 자격 증명을 사용하여 원격 시스템 server01에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-123">This command creates a connection to the remote system server01 using the Administrator account credentials.</span></span>

<span data-ttu-id="e32ac-124">첫 번째 명령은 Get-Credential cmdlet을 사용하여 관리자 자격 증명을 가져온 후 $cred 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-124">The first command uses the Get-Credential cmdlet to get the Administrator credentials and then stores them in the $cred variable.</span></span>
<span data-ttu-id="e32ac-125">**Get 자격 증명** 은 대화 상자를 통해 사용자 이름 및 암호를 묻는 메시지를 표시 하 고, 시스템 레지스트리 설정에 따라 명령줄에서 암호를 입력 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-125">**Get-Credential** prompts you for a password of username and password through a dialog box or at the command line, depending on system registry settings.</span></span>

<span data-ttu-id="e32ac-126">두 번째 명령은 *Credential* 매개 변수를 사용 하 여 $cred에 저장 된 자격 증명을 **연결-WSMan** 에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-126">The second command uses the *Credential* parameter to pass the credentials stored in $cred to **Connect-WSMan**.</span></span>
<span data-ttu-id="e32ac-127">**연결-WSMan** 은 관리자 자격 증명을 사용 하 여 원격 시스템 server01에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-127">**Connect-WSMan** then connects to the remote system server01 by using the Administrator credentials.</span></span>

### <span data-ttu-id="e32ac-128">예 3: 지정 된 포트를 통해 원격 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="e32ac-128">Example 3: Connect to a remote computer over a specified port</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="e32ac-129">이 명령은 포트 80을 통해 원격 server01 컴퓨터에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-129">This command creates a connection to the remote server01 computer over port 80.</span></span>

### <span data-ttu-id="e32ac-130">예 4: 연결 옵션을 사용 하 여 원격 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="e32ac-130">Example 4: Connect to a remote computer by using connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="e32ac-131">이 예에서는 **New-WSManSessionOption** 명령에 정의 된 연결 옵션을 사용 하 여 원격 server01 컴퓨터에 대 한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-131">This example creates a connection to the remote server01 computer by using the connection options that are defined in the **New-WSManSessionOption** command.</span></span>

<span data-ttu-id="e32ac-132">첫 번째 명령은 **New-WSManSessionOption** 을 사용 하 여 $a 변수에 연결 설정 옵션 집합을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-132">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="e32ac-133">이 경우 세션 옵션은 연결 시간 제한을 30초(30,000밀리초)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-133">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="e32ac-134">두 번째 명령은 *Sessionoption* 매개 변수를 사용 하 여 $a 변수에 저장 된 자격 증명을 **연결-WSMan** 에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-134">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="e32ac-135">그런 다음, **연결-WSMan** 은 지정 된 세션 옵션을 사용 하 여 원격 server01 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-135">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

## <span data-ttu-id="e32ac-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e32ac-136">PARAMETERS</span></span>

### <span data-ttu-id="e32ac-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="e32ac-137">-ApplicationName</span></span>
<span data-ttu-id="e32ac-138">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="e32ac-139">*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-139">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="e32ac-140">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="e32ac-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="e32ac-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="e32ac-142">`http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="e32ac-142">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="e32ac-143">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="e32ac-144">이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-144">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="e32ac-145">이 매개 변수는 많은 컴퓨터에서 PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-145">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="e32ac-146">이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="e32ac-147">-인증</span><span class="sxs-lookup"><span data-stu-id="e32ac-147">-Authentication</span></span>
<span data-ttu-id="e32ac-148">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="e32ac-149">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-149">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e32ac-150">기본.</span><span class="sxs-lookup"><span data-stu-id="e32ac-150">Basic.</span></span>
<span data-ttu-id="e32ac-151">Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-151">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="e32ac-152">기본.</span><span class="sxs-lookup"><span data-stu-id="e32ac-152">Default.</span></span>
<span data-ttu-id="e32ac-153">WS-Management 프로토콜로 구현된 인증 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-153">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="e32ac-154">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-154">This is the default.</span></span>
- <span data-ttu-id="e32ac-155">다이제스트.</span><span class="sxs-lookup"><span data-stu-id="e32ac-155">Digest.</span></span>
<span data-ttu-id="e32ac-156">Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-156">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="e32ac-157">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="e32ac-157">Kerberos.</span></span>
<span data-ttu-id="e32ac-158">클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용하여 상호 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-158">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="e32ac-159">Negotiate</span><span class="sxs-lookup"><span data-stu-id="e32ac-159">Negotiate.</span></span>
<span data-ttu-id="e32ac-160">Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-160">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="e32ac-161">예를 들어이 매개 변수 값은 협상을 통해 Kerberos 프로토콜 또는 NTLM이 사용 되는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-161">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="e32ac-162">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="e32ac-162">CredSSP.</span></span>
<span data-ttu-id="e32ac-163">사용자가 자격 증명을 위임할 수 있도록 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-163">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="e32ac-164">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-164">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="e32ac-165">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-165">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="e32ac-166">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-166">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="e32ac-167">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-167">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="e32ac-168">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="e32ac-168">-CertificateThumbprint</span></span>
<span data-ttu-id="e32ac-169">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-169">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="e32ac-170">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-170">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="e32ac-171">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-171">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="e32ac-172">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-172">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="e32ac-173">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-173">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="e32ac-174">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e32ac-174">-ComputerName</span></span>
<span data-ttu-id="e32ac-175">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-175">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="e32ac-176">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-176">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="e32ac-177">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-177">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="e32ac-178">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-178">The local computer is the default.</span></span>
<span data-ttu-id="e32ac-179">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-179">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="e32ac-180">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-180">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e32ac-181">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="e32ac-181">-ConnectionURI</span></span>
<span data-ttu-id="e32ac-182">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-182">Specifies the connection endpoint.</span></span>
<span data-ttu-id="e32ac-183">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-183">The format of this string is as follows:</span></span>

<span data-ttu-id="e32ac-184">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="e32ac-184">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="e32ac-185">다음 문자열은이 매개 변수의 형식이 올바르게 지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-185">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="e32ac-186">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-186">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="e32ac-187">-Credential</span><span class="sxs-lookup"><span data-stu-id="e32ac-187">-Credential</span></span>
<span data-ttu-id="e32ac-188">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-188">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="e32ac-189">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-189">The default is the current user.</span></span>
<span data-ttu-id="e32ac-190">User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-190">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="e32ac-191">또는 Get-Credential cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-191">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="e32ac-192">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-192">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="e32ac-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="e32ac-193">-OptionSet</span></span>
<span data-ttu-id="e32ac-194">요청의 특성을 수정 하거나 구체화 하기 위해 서비스에 대 한 스위치 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-194">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="e32ac-195">이러한 스위치는 서비스 마다 다르기 때문에 명령줄 셸에 사용 되는 스위치와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-195">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="e32ac-196">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-196">Any number of options can be specified.</span></span>

<span data-ttu-id="e32ac-197">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="e32ac-198">-Port</span><span class="sxs-lookup"><span data-stu-id="e32ac-198">-Port</span></span>
<span data-ttu-id="e32ac-199">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="e32ac-200">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="e32ac-201">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-201">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="e32ac-202">전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-202">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="e32ac-203">그러나 *Skipcncheck* 매개 변수가 *sessionoption* 매개 변수의 일부로 지정 된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-203">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="e32ac-204">*Skipcncheck* 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-204">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="e32ac-205">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="e32ac-205">-SessionOption</span></span>
<span data-ttu-id="e32ac-206">WS-Management 세션에 대 한 확장 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-206">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="e32ac-207">New-WSManSessionOption cmdlet을 사용 하 여 만든 **Sessionoption** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-207">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="e32ac-208">사용할 수 있는 옵션에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="e32ac-208">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="e32ac-209">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="e32ac-209">-UseSSL</span></span>
<span data-ttu-id="e32ac-210">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-210">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="e32ac-211">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-211">By default, SSL is not used.</span></span>

<span data-ttu-id="e32ac-212">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-212">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="e32ac-213">*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-213">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="e32ac-214">연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-214">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="e32ac-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e32ac-215">CommonParameters</span></span>
<span data-ttu-id="e32ac-216">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e32ac-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e32ac-217">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e32ac-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e32ac-218">입력</span><span class="sxs-lookup"><span data-stu-id="e32ac-218">INPUTS</span></span>

### <span data-ttu-id="e32ac-219">없음</span><span class="sxs-lookup"><span data-stu-id="e32ac-219">None</span></span>
<span data-ttu-id="e32ac-220">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-220">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="e32ac-221">출력</span><span class="sxs-lookup"><span data-stu-id="e32ac-221">OUTPUTS</span></span>

### <span data-ttu-id="e32ac-222">없음</span><span class="sxs-lookup"><span data-stu-id="e32ac-222">None</span></span>
<span data-ttu-id="e32ac-223">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-223">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e32ac-224">참고</span><span class="sxs-lookup"><span data-stu-id="e32ac-224">NOTES</span></span>

* <span data-ttu-id="e32ac-225">WS-Management 세션을 만들지 않고도 원격 컴퓨터에서 관리 명령 또는 쿼리 관리 데이터를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-225">You can run management commands or query management data on a remote computer without creating a WS-Management session.</span></span> <span data-ttu-id="e32ac-226">Invoke-WSManAction의 *ComputerName* 매개 변수와 Get-wsmaninstance를 사용 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-226">You can do this by using the *ComputerName* parameters of Invoke-WSManAction and Get-WSManInstance.</span></span> <span data-ttu-id="e32ac-227">*ComputerName* 매개 변수를 사용 하는 경우 PowerShell은 단일 명령에 사용 되는 임시 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-227">When you use the *ComputerName* parameter, PowerShell creates a temporary connection that is used for the single command.</span></span> <span data-ttu-id="e32ac-228">명령이 실행된 후 연결이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="e32ac-228">After the command runs, the connection is closed.</span></span>

*

## <span data-ttu-id="e32ac-229">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e32ac-229">RELATED LINKS</span></span>

[<span data-ttu-id="e32ac-230">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e32ac-230">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="e32ac-231">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e32ac-231">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="e32ac-232">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e32ac-232">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="e32ac-233">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e32ac-233">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="e32ac-234">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e32ac-234">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="e32ac-235">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="e32ac-235">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="e32ac-236">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e32ac-236">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="e32ac-237">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="e32ac-237">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="e32ac-238">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e32ac-238">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="e32ac-239">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e32ac-239">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="e32ac-240">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="e32ac-240">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="e32ac-241">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="e32ac-241">Test-WSMan</span></span>](Test-WSMan.md)
