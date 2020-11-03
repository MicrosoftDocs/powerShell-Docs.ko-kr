---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 112b4a1e0a790c32b6a3ea2011fbc72ec86a0324
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218714"
---
# <span data-ttu-id="77aaa-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="77aaa-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="77aaa-104">개요</span><span class="sxs-lookup"><span data-stu-id="77aaa-104">SYNOPSIS</span></span>
<span data-ttu-id="77aaa-105">리소스 URI 및 선택기에 따라 지정된 개체에 대한 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="77aaa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="77aaa-106">SYNTAX</span></span>

### <span data-ttu-id="77aaa-107">URI (기본값)</span><span class="sxs-lookup"><span data-stu-id="77aaa-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="77aaa-108">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="77aaa-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="77aaa-109">설명</span><span class="sxs-lookup"><span data-stu-id="77aaa-109">DESCRIPTION</span></span>
<span data-ttu-id="77aaa-110">RESOURCE_URI로 지정 된 개체에 대 **한 작업을 실행 합니다** . 여기서 매개 변수는 키 값 쌍으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-110">The **Invoke-WSManAction** runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="77aaa-111">이 cmdlet은 WSMan 연결/전송 계층을 사용하여 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="77aaa-112">예제</span><span class="sxs-lookup"><span data-stu-id="77aaa-112">EXAMPLES</span></span>

### <span data-ttu-id="77aaa-113">예제 1: 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="77aaa-113">Example 1: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="77aaa-114">이 명령은 스풀러 서비스에 해당 하는 Win32_Service WMI 클래스 인스턴스의 **StartService** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-114">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="77aaa-115">반환 값은 작업의 성공 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="77aaa-116">이 경우 반환 값 0은 성공을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="77aaa-117">반환 값 5는 서비스가 이미 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="77aaa-118">예제 2: 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="77aaa-118">Example 2: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="77aaa-119">이 명령은 파일의 입력을 사용 하 여 스풀러 서비스에 대해 **StopService** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-119">This command calls the **StopService** method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="77aaa-120">Input.xml 파일은 다음 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### <span data-ttu-id="77aaa-121">예제 3: 지정 된 매개 변수 값을 사용 하 여 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="77aaa-121">Example 3: Invoke a method with specified parameter values</span></span>

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

<span data-ttu-id="77aaa-122">이 명령은 Win32_Process 클래스의 **Create** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-122">This command calls the **Create** method of the Win32_Process class.</span></span>
<span data-ttu-id="77aaa-123">이 메서드는 두 개의 매개 변수 값 Notepad.exe와 C:\.를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-123">It passes the method two parameter values, Notepad.exe and C:\.</span></span>
<span data-ttu-id="77aaa-124">그 결과 메모장을 실행 하는 새 프로세스가 만들어지고 새 프로세스의 현재 디렉터리는 C:\.로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-124">As a result, a new process is created to run Notepad, and the current directory of the new process is set to C:\.</span></span>

### <span data-ttu-id="77aaa-125">예제 4: 원격 컴퓨터에서 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="77aaa-125">Example 4: Invoke a method on a remote computer</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="77aaa-126">이 명령은 스풀러 서비스에 해당 하는 Win32_Service WMI 클래스 인스턴스의 **StartService** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-126">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="77aaa-127">*ComputerName* 매개 변수가 지정 되었으므로 명령은 원격 server01 컴퓨터에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-127">Because the *ComputerName* parameter is specified, the command runs against the remote server01 computer.</span></span>

## <span data-ttu-id="77aaa-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77aaa-128">PARAMETERS</span></span>

### <span data-ttu-id="77aaa-129">-Action</span><span class="sxs-lookup"><span data-stu-id="77aaa-129">-Action</span></span>
<span data-ttu-id="77aaa-130">ResourceURI 및 선택기로 지정 된 관리 개체에 대해 실행할 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-130">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77aaa-131">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="77aaa-131">-ApplicationName</span></span>
<span data-ttu-id="77aaa-132">연결의 애플리케이션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-132">Specifies the application name in the connection.</span></span>
<span data-ttu-id="77aaa-133">*ApplicationName* 매개 변수의 기본값은 WSMAN입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-133">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="77aaa-134">원격 엔드포인트의 완전한 식별자 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-134">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="77aaa-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="77aaa-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="77aaa-136">`http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="77aaa-136">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="77aaa-137">세션을 호스트하는 IIS(인터넷 정보 서비스)는 이 엔드포인트가 포함된 요청을 지정된 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-137">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="77aaa-138">이러한 기본 WSMAN 설정은 대부분의 용도에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-138">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="77aaa-139">이 매개 변수는 많은 컴퓨터에서 PowerShell을 실행 하는 한 컴퓨터에 대 한 원격 연결을 설정할 때 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-139">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="77aaa-140">이 경우 IIS는 효율성을 위해 WS-MANAGEMENT (관리용 웹 서비스)를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-140">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="77aaa-141">-인증</span><span class="sxs-lookup"><span data-stu-id="77aaa-141">-Authentication</span></span>
<span data-ttu-id="77aaa-142">서버에서 사용할 인증 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-142">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="77aaa-143">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="77aaa-144">기본.</span><span class="sxs-lookup"><span data-stu-id="77aaa-144">Basic.</span></span>
<span data-ttu-id="77aaa-145">Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-145">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="77aaa-146">기본.</span><span class="sxs-lookup"><span data-stu-id="77aaa-146">Default.</span></span>
<span data-ttu-id="77aaa-147">WS-Management 프로토콜로 구현된 인증 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-147">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="77aaa-148">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-148">This is the default.</span></span>
- <span data-ttu-id="77aaa-149">다이제스트.</span><span class="sxs-lookup"><span data-stu-id="77aaa-149">Digest.</span></span>
<span data-ttu-id="77aaa-150">Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-150">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="77aaa-151">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="77aaa-151">Kerberos.</span></span>
<span data-ttu-id="77aaa-152">클라이언트 컴퓨터와 서버가 Kerberos 인증서를 사용하여 상호 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-152">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="77aaa-153">Negotiate</span><span class="sxs-lookup"><span data-stu-id="77aaa-153">Negotiate.</span></span>
<span data-ttu-id="77aaa-154">Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-154">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="77aaa-155">예를 들어이 매개 변수 값은 협상을 통해 Kerberos 프로토콜 또는 NTLM이 사용 되는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-155">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="77aaa-156">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="77aaa-156">CredSSP.</span></span>
<span data-ttu-id="77aaa-157">사용자가 자격 증명을 위임할 수 있도록 하는 CredSSP (Credential Security Support Provider) 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-157">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="77aaa-158">이 옵션은 한 원격 컴퓨터에서 실행되지만 다른 원격 컴퓨터에서 데이터를 수집하거나 추가 명령을 실행하는 명령을 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="77aaa-159">주의: CredSSP는 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-159">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="77aaa-160">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="77aaa-161">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="77aaa-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="77aaa-162">-CertificateThumbprint</span></span>
<span data-ttu-id="77aaa-163">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="77aaa-164">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="77aaa-165">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="77aaa-166">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="77aaa-167">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="77aaa-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="77aaa-168">-ComputerName</span></span>
<span data-ttu-id="77aaa-169">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-169">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="77aaa-170">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="77aaa-171">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="77aaa-172">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-172">The local computer is the default.</span></span>
<span data-ttu-id="77aaa-173">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="77aaa-174">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="77aaa-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="77aaa-175">-ConnectionURI</span></span>
<span data-ttu-id="77aaa-176">연결 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="77aaa-177">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-177">The format of this string is as follows:</span></span>

<span data-ttu-id="77aaa-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="77aaa-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="77aaa-179">다음 문자열은이 매개 변수의 형식이 올바르게 지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-179">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="77aaa-180">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="77aaa-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="77aaa-181">-Credential</span></span>
<span data-ttu-id="77aaa-182">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="77aaa-183">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-183">The default is the current user.</span></span>
<span data-ttu-id="77aaa-184">User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-184">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="77aaa-185">또는 Get-Credential cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-185">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="77aaa-186">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-186">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="77aaa-187">-FilePath</span><span class="sxs-lookup"><span data-stu-id="77aaa-187">-FilePath</span></span>
<span data-ttu-id="77aaa-188">관리 리소스를 업데이트하는 데 사용되는 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="77aaa-189">*ResourceURI* 매개 변수 및 *SelectorSet* 매개 변수를 사용 하 여 관리 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-189">You specify the management resource by using the *ResourceURI* parameter and the *SelectorSet* parameter.</span></span>
<span data-ttu-id="77aaa-190">예를 들어 다음 명령은 *FilePath* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-190">For example, the following command uses the *FilePath* parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="77aaa-191">이 명령은 파일의 입력을 사용 하 여 **스풀러** 서비스에 대해 **StopService** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-191">This command calls the **StopService** method on the **Spooler** service by using input from a file.</span></span>
<span data-ttu-id="77aaa-192">Input.xml 파일은 다음 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-192">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="77aaa-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="77aaa-193">-OptionSet</span></span>
<span data-ttu-id="77aaa-194">요청의 특성을 수정 하거나 구체화 하기 위해 서비스에 대 한 스위치 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-194">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="77aaa-195">이러한 스위치는 서비스 마다 다르기 때문에 명령줄 셸에 사용 되는 스위치와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-195">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="77aaa-196">원하는 수의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-196">Any number of options can be specified.</span></span>

<span data-ttu-id="77aaa-197">다음 예제에서는 a, b 및 c 매개 변수에 대해 값 1, 2 및 3을 전달하는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="77aaa-198">-Port</span><span class="sxs-lookup"><span data-stu-id="77aaa-198">-Port</span></span>
<span data-ttu-id="77aaa-199">클라이언트가 WinRM 서비스에 연결될 때 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="77aaa-200">전송이 HTTP인 경우 기본 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="77aaa-201">전송이 HTTPS인 경우 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-201">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="77aaa-202">전송으로 HTTPS를 사용 하는 경우 *ComputerName* 매개 변수 값이 서버의 인증서 CN (일반 이름)과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-202">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="77aaa-203">그러나 *Skipcncheck* 매개 변수가 *sessionoption* 매개 변수의 일부로 지정 된 경우 서버의 인증서 일반 이름이 서버의 호스트 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-203">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="77aaa-204">*Skipcncheck* 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-204">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="77aaa-205">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="77aaa-205">-ResourceURI</span></span>
<span data-ttu-id="77aaa-206">리소스 클래스 또는 인스턴스의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-206">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="77aaa-207">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="77aaa-208">URI는 접두사와 리소스 경로로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-208">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="77aaa-209">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="77aaa-209">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="77aaa-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="77aaa-210">-SelectorSet</span></span>
<span data-ttu-id="77aaa-211">특정 관리 리소스 인스턴스를 선택하는 데 사용되는 값 쌍의 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="77aaa-212">*SelectorSet* 는 리소스의 인스턴스가 두 개 이상 있을 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="77aaa-213">*SelectorSet* 의 값은 해시 테이블 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="77aaa-214">다음 예제에서는 이 매개 변수 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-214">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="77aaa-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="77aaa-215">-SessionOption</span></span>
<span data-ttu-id="77aaa-216">WS-Management 세션에 대 한 확장 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-216">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="77aaa-217">New-WSManSessionOption cmdlet을 사용 하 여 만든 **Sessionoption** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-217">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="77aaa-218">사용할 수 있는 옵션에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="77aaa-218">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="77aaa-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="77aaa-219">-UseSSL</span></span>
<span data-ttu-id="77aaa-220">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="77aaa-221">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-221">By default, SSL is not used.</span></span>

<span data-ttu-id="77aaa-222">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-222">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="77aaa-223">*UseSSL* 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-223">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="77aaa-224">연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-224">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="77aaa-225">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="77aaa-225">-ValueSet</span></span>
<span data-ttu-id="77aaa-226">관리 리소스를 수정하는 데 도움이 되는 해시 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="77aaa-227">*ResourceURI* 및 *SelectorSet* 를 사용 하 여 관리 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-227">You specify the management resource by using *ResourceURI* and *SelectorSet*.</span></span>
<span data-ttu-id="77aaa-228">*Valueset* 매개 변수 값은 해시 테이블 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-228">The value of the *ValueSet* parameter must be a hash table.</span></span>

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

### <span data-ttu-id="77aaa-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77aaa-229">CommonParameters</span></span>
<span data-ttu-id="77aaa-230">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77aaa-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77aaa-231">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77aaa-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77aaa-232">입력</span><span class="sxs-lookup"><span data-stu-id="77aaa-232">INPUTS</span></span>

### <span data-ttu-id="77aaa-233">없음</span><span class="sxs-lookup"><span data-stu-id="77aaa-233">None</span></span>
<span data-ttu-id="77aaa-234">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="77aaa-235">출력</span><span class="sxs-lookup"><span data-stu-id="77aaa-235">OUTPUTS</span></span>

### <span data-ttu-id="77aaa-236">없음</span><span class="sxs-lookup"><span data-stu-id="77aaa-236">None</span></span>
<span data-ttu-id="77aaa-237">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77aaa-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="77aaa-238">참고</span><span class="sxs-lookup"><span data-stu-id="77aaa-238">NOTES</span></span>

## <span data-ttu-id="77aaa-239">관련 링크</span><span class="sxs-lookup"><span data-stu-id="77aaa-239">RELATED LINKS</span></span>

[<span data-ttu-id="77aaa-240">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="77aaa-240">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="77aaa-241">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="77aaa-241">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="77aaa-242">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="77aaa-242">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="77aaa-243">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="77aaa-243">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="77aaa-244">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="77aaa-244">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="77aaa-245">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="77aaa-245">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="77aaa-246">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="77aaa-246">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="77aaa-247">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="77aaa-247">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="77aaa-248">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="77aaa-248">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="77aaa-249">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="77aaa-249">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="77aaa-250">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="77aaa-250">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="77aaa-251">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="77aaa-251">Test-WSMan</span></span>](Test-WSMan.md)

