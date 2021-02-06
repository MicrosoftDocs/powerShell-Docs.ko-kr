---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: e7d7f132eb82dc1a709a88cbdef525aa83d867e4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605225"
---
# <span data-ttu-id="79f7f-102">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="79f7f-102">New-WSManSessionOption</span></span>

## <span data-ttu-id="79f7f-103">개요</span><span class="sxs-lookup"><span data-stu-id="79f7f-103">SYNOPSIS</span></span>
<span data-ttu-id="79f7f-104">WS-Management cmdlet에 대 한 입력 매개 변수로 사용할 세션 옵션 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-104">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="79f7f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79f7f-105">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="79f7f-106">설명</span><span class="sxs-lookup"><span data-stu-id="79f7f-106">DESCRIPTION</span></span>
<span data-ttu-id="79f7f-107">**새-WSManSessionOption** cmdlet은 wsman cmdlet에 전달할 수 있는 wsman 세션 옵션 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-107">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="79f7f-108">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="79f7f-108">Get-WSManInstance</span></span>
- <span data-ttu-id="79f7f-109">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="79f7f-109">Set-WSManInstance</span></span>
- <span data-ttu-id="79f7f-110">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="79f7f-110">Invoke-WSManAction</span></span>
- <span data-ttu-id="79f7f-111">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="79f7f-111">Connect-WSMan</span></span>

## <span data-ttu-id="79f7f-112">예제</span><span class="sxs-lookup"><span data-stu-id="79f7f-112">EXAMPLES</span></span>

### <span data-ttu-id="79f7f-113">예 1: 연결 옵션을 사용 하는 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="79f7f-113">Example 1: Create a connection that uses connection options</span></span>

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

<span data-ttu-id="79f7f-114">이 예에서는 server01 **옵션** 으로 정의 된 연결 옵션을 사용 하 여 원격 컴퓨터에 대 한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-114">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption**.</span></span>

<span data-ttu-id="79f7f-115">첫 번째 명령은 **New-WSManSessionOption** 을 사용 하 여 $a 변수에 연결 설정 옵션 집합을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-115">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="79f7f-116">이 경우 세션 옵션은 연결 시간 제한을 30초(30,000밀리초)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-116">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="79f7f-117">두 번째 명령은 *Sessionoption* 매개 변수를 사용 하 여 $a 변수에 저장 된 자격 증명을 **연결-WSMan** 에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-117">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="79f7f-118">그런 다음, **연결-WSMan** 은 지정 된 세션 옵션을 사용 하 여 원격 server01 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-118">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="79f7f-119">**연결-wsman** 은 일반적으로 원격 컴퓨터 (이 경우 server01 컴퓨터)에 연결 하기 위해 wsman 공급자의 컨텍스트에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-119">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="79f7f-120">그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터에 대한 연결을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="79f7f-121">이러한 연결은 **ComputerName** 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-121">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="79f7f-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79f7f-122">PARAMETERS</span></span>

### <span data-ttu-id="79f7f-123">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="79f7f-123">-NoEncryption</span></span>
<span data-ttu-id="79f7f-124">연결에서 HTTP를 통한 원격 작업에 암호화를 사용 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-124">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="79f7f-125">암호화 되지 않은 트래픽은 기본적으로 사용 하도록 설정 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-125">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="79f7f-126">로컬 구성에서 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-126">It must be enabled in the local configuration.</span></span>

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

### <span data-ttu-id="79f7f-127">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="79f7f-127">-OperationTimeout</span></span>
<span data-ttu-id="79f7f-128">WS-Management 작업에 대 한 제한 시간 (밀리초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-128">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79f7f-129">-System.management.automation.remoting.proxyaccesstype</span><span class="sxs-lookup"><span data-stu-id="79f7f-129">-ProxyAccessType</span></span>
<span data-ttu-id="79f7f-130">프록시 서버가 배치되는 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-130">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="79f7f-131">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="79f7f-132">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="79f7f-132">ProxyIEConfig.</span></span>
<span data-ttu-id="79f7f-133">현재 사용자의 Internet Explorer 프록시 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-133">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="79f7f-134">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="79f7f-134">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="79f7f-135">WSMan 클라이언트는 ProxyCfg.exe 유틸리티를 사용 하 여 WinHTTP에 대해 구성 된 프록시 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-135">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="79f7f-136">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="79f7f-136">ProxyAutoDetect.</span></span>
<span data-ttu-id="79f7f-137">프록시 서버 자동 검색을 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-137">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="79f7f-138">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="79f7f-138">ProxyNoProxyServer.</span></span>
<span data-ttu-id="79f7f-139">프록시 서버를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="79f7f-139">Do not use a proxy server.</span></span>
<span data-ttu-id="79f7f-140">모든 호스트 이름을 로컬에서 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-140">Resolve all host names locally.</span></span>

<span data-ttu-id="79f7f-141">기본값은 ProxyIEConfig입니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-141">The default value is ProxyIEConfig.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79f7f-142">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="79f7f-142">-ProxyAuthentication</span></span>
<span data-ttu-id="79f7f-143">프록시에 사용할 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-143">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="79f7f-144">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="79f7f-145">기본.</span><span class="sxs-lookup"><span data-stu-id="79f7f-145">Basic.</span></span>
<span data-ttu-id="79f7f-146">Basic은 사용자 이름과 암호가 암호화되지 않은 텍스트로 서버 또는 프록시에 전송되는 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-146">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="79f7f-147">다이제스트.</span><span class="sxs-lookup"><span data-stu-id="79f7f-147">Digest.</span></span>
<span data-ttu-id="79f7f-148">Digest는 챌린지에 서버 지정 데이터 문자열을 사용하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-148">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="79f7f-149">Negotiate</span><span class="sxs-lookup"><span data-stu-id="79f7f-149">Negotiate.</span></span>
<span data-ttu-id="79f7f-150">Negotiate는 인증에 사용할 체계를 확인하기 위해 서버 또는 프록시와 협상하는 챌린지-응답 체계입니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-150">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="79f7f-151">이러한 예로는 Kerberos 프로토콜 및 NTLM이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-151">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="79f7f-152">기본값은 Negotiate입니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-152">The default value is Negotiate.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79f7f-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="79f7f-153">-ProxyCredential</span></span>
<span data-ttu-id="79f7f-154">중간 웹 프록시를 통해 액세스할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-154">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

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

### <span data-ttu-id="79f7f-155">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="79f7f-155">-SkipCACheck</span></span>
<span data-ttu-id="79f7f-156">HTTPS를 통해 연결 하는 경우 클라이언트에서 서버 인증서가 신뢰할 수 있는 CA (인증 기관)에 의해 서명 되었는지 확인 하지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-156">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="79f7f-157">원격 컴퓨터가 물리적으로 안전 하 고 격리 된 네트워크에 속해 있거나 원격 컴퓨터가 WS-Management 구성에서 신뢰할 수 있는 호스트로 나열 되어 있는 경우와 같이 원격 컴퓨터를 다른 방법으로 신뢰할 수 있는 경우에만이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-157">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

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

### <span data-ttu-id="79f7f-158">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="79f7f-158">-SkipCNCheck</span></span>
<span data-ttu-id="79f7f-159">서버의 인증서 CN (일반 이름)이 서버의 호스트 이름과 일치할 필요가 없도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-159">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="79f7f-160">이 옵션은 HTTPS를 사용하는 원격 작업에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-160">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="79f7f-161">이 옵션은 신뢰할 수 있는 컴퓨터에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-161">This option should only be used for trusted computers.</span></span>

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

### <span data-ttu-id="79f7f-162">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="79f7f-162">-SkipRevocationCheck</span></span>
<span data-ttu-id="79f7f-163">연결에서 서버 인증서의 해지 상태를 확인 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-163">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

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

### <span data-ttu-id="79f7f-164">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="79f7f-164">-SPNPort</span></span>
<span data-ttu-id="79f7f-165">원격 서버의 연결 서비스 사용자 이름 (SPN)에 추가할 포트 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-165">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="79f7f-166">SPN은 인증 메커니즘이 Kerberos 또는 Negotiate인 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-166">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

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

### <span data-ttu-id="79f7f-167">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="79f7f-167">-UseUTF16</span></span>
<span data-ttu-id="79f7f-168">연결이 UTF8 형식 대신 UTF16 형식으로 요청을 인코드 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-168">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="79f7f-169">기본값은 UTF8 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="79f7f-169">The default is UTF8 encoding.</span></span>

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

### <span data-ttu-id="79f7f-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79f7f-170">CommonParameters</span></span>
<span data-ttu-id="79f7f-171">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="79f7f-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79f7f-172">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79f7f-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79f7f-173">입력</span><span class="sxs-lookup"><span data-stu-id="79f7f-173">INPUTS</span></span>

## <span data-ttu-id="79f7f-174">출력</span><span class="sxs-lookup"><span data-stu-id="79f7f-174">OUTPUTS</span></span>

### <span data-ttu-id="79f7f-175">SessionOption</span><span class="sxs-lookup"><span data-stu-id="79f7f-175">SessionOption</span></span>

## <span data-ttu-id="79f7f-176">참고</span><span class="sxs-lookup"><span data-stu-id="79f7f-176">NOTES</span></span>

## <span data-ttu-id="79f7f-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="79f7f-177">RELATED LINKS</span></span>

[<span data-ttu-id="79f7f-178">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="79f7f-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="79f7f-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="79f7f-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="79f7f-180">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="79f7f-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="79f7f-181">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="79f7f-181">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="79f7f-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="79f7f-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="79f7f-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="79f7f-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="79f7f-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="79f7f-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="79f7f-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="79f7f-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="79f7f-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="79f7f-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="79f7f-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="79f7f-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="79f7f-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="79f7f-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="79f7f-189">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="79f7f-189">Test-WSMan</span></span>](Test-WSMan.md)

