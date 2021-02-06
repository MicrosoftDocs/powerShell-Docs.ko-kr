---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 54a2ca8a28d54bfe1d9676acdaace4592f62620f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601244"
---
# <span data-ttu-id="3d59c-102">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="3d59c-102">New-CimSessionOption</span></span>

## <span data-ttu-id="3d59c-103">개요</span><span class="sxs-lookup"><span data-stu-id="3d59c-103">SYNOPSIS</span></span>
<span data-ttu-id="3d59c-104">New-CimSession cmdlet에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-104">Specifies advanced options for the New-CimSession cmdlet.</span></span>

## <span data-ttu-id="3d59c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d59c-105">SYNTAX</span></span>

### <span data-ttu-id="3d59c-106">ProtocolTypeSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="3d59c-106">ProtocolTypeSet (Default)</span></span>

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### <span data-ttu-id="3d59c-107">WSManParameterSet</span><span class="sxs-lookup"><span data-stu-id="3d59c-107">WSManParameterSet</span></span>

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### <span data-ttu-id="3d59c-108">DcomParameterSet</span><span class="sxs-lookup"><span data-stu-id="3d59c-108">DcomParameterSet</span></span>

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## <span data-ttu-id="3d59c-109">설명</span><span class="sxs-lookup"><span data-stu-id="3d59c-109">DESCRIPTION</span></span>

<span data-ttu-id="3d59c-110">`New-CimSessionOption`Cmdlet은 CIM 세션 옵션 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-110">The `New-CimSessionOption` cmdlet creates an instance of a CIM session options object.</span></span> <span data-ttu-id="3d59c-111">Cim 세션 옵션 개체를 cmdlet에 대 한 입력으로 사용 하 여 `New-CimSession` cim 세션의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-111">You use a CIM session options object as input to the `New-CimSession` cmdlet to specify the options for a CIM session.</span></span>

<span data-ttu-id="3d59c-112">이 cmdlet에는 두 개의 매개 변수 집합, 즉 WsMan 옵션과 DCOM (Distributed Component Object Model) 옵션에 대 한 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-112">This cmdlet has two parameter sets, one for WsMan options and one for Distributed Component Object Model (DCOM) options.</span></span> <span data-ttu-id="3d59c-113">사용 하는 매개 변수에 따라 cmdlet은 DCOM 세션 옵션의 인스턴스를 반환 하거나 WsMan 세션 옵션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-113">Depending on which parameters you use, the cmdlet returns either an instance of DCOM session options or returns WsMan session options.</span></span>

## <span data-ttu-id="3d59c-114">예제</span><span class="sxs-lookup"><span data-stu-id="3d59c-114">EXAMPLES</span></span>

### <span data-ttu-id="3d59c-115">예제 1: DCOM에 대 한 CIM 세션 옵션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3d59c-115">Example 1: Create a CIM session options object for DCOM</span></span>

<span data-ttu-id="3d59c-116">이 예에서는 DCOM 프로토콜에 대 한 CIM 세션 옵션 개체를 만들고 라는 변수에 저장 `$so` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-116">This example creates a CIM session options object for the DCOM protocol and stores it in a variable named `$so`.</span></span> <span data-ttu-id="3d59c-117">그런 다음 변수의 내용이 cmdlet에 전달 됩니다 `New-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="3d59c-117">The contents of the variable are then passed to the `New-CimSession` cmdlet.</span></span>
<span data-ttu-id="3d59c-118">`New-CimSession` 그런 다음는 변수에 정의 된 옵션을 사용 하 여 Server01 라는 원격 서버를 사용 하 여 새 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-118">`New-CimSession` then creates a new CIM session with the remote server named Server01, using the options defined in the variable.</span></span>

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### <span data-ttu-id="3d59c-119">예제 2: WsMan에 대 한 CIM 세션 옵션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3d59c-119">Example 2: Create a CIM session options object for WsMan</span></span>

<span data-ttu-id="3d59c-120">이 예에서는 WsMan 프로토콜에 대 한 CIM 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-120">This example creates a CIM session options object for the WsMan protocol.</span></span> <span data-ttu-id="3d59c-121">개체는 **proxyauthentication** 매개 변수로 지정 된 **Kerberos** 의 인증 모드에 대 한 구성, **ProxyCredential** 매개 변수로 지정 된 자격 증명을 포함 하 고, CA 검사를 건너뛰고 CN 검사를 건너뛰고 SSL을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-121">The object contains configuration for the authentication mode of **Kerberos** specified by the **ProxyAuthentication** parameter, the credentials specified by the **ProxyCredential** parameter, and specifies that the command is to skip the CA check, skip the CN check, and use SSL.</span></span>

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### <span data-ttu-id="3d59c-122">예제 3: 지정 된 문화권을 사용 하 여 CIM 세션 옵션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3d59c-122">Example 3: Create a CIM session options object with the culture specified</span></span>

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

<span data-ttu-id="3d59c-123">이 예에서는 CIM 세션에 사용 되는 문화권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-123">This example specifies the culture that is used for the CIM session.</span></span> <span data-ttu-id="3d59c-124">기본적으로 클라이언트의 문화권은 작업을 수행할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-124">By default, the culture of the client is used when performing operations.</span></span> <span data-ttu-id="3d59c-125">그러나 **culture** 매개 변수를 사용 하 여 기본 문화권을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-125">However, the default culture can be overridden using the **Culture** parameter.</span></span>

## <span data-ttu-id="3d59c-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d59c-126">PARAMETERS</span></span>

### <span data-ttu-id="3d59c-127">-문화권</span><span class="sxs-lookup"><span data-stu-id="3d59c-127">-Culture</span></span>

<span data-ttu-id="3d59c-128">CIM 세션에 사용할 사용자 인터페이스 문화권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-128">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="3d59c-129">다음 형식 중 하나를 사용 하 여이 매개 변수에 대 한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-129">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="3d59c-130">`<languagecode2>-<country/regioncode2>`"En-us"와 같은 형식의 문화권 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-130">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="3d59c-131">**CultureInfo** 개체를 포함 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-131">A variable that contains a **CultureInfo** object.</span></span>
- <span data-ttu-id="3d59c-132">[-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md) 와 같은 **CultureInfo** 개체를 가져오는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-132">A command that gets a **CultureInfo** object, such as [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-133">-EncodePortInServicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="3d59c-133">-EncodePortInServicePrincipalName</span></span>

<span data-ttu-id="3d59c-134">Kerberos 연결이 서비스 사용자 이름 (SPN)에 서비스 포트 번호를 포함 하는 서비스에 연결 하 고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-134">Indicates that the Kerberos connection is connecting to a service whose service principal name (SPN) includes the service port number.</span></span> <span data-ttu-id="3d59c-135">이 유형의 연결은 일반적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-135">This type of connection is not common.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-136">-Encoding</span><span class="sxs-lookup"><span data-stu-id="3d59c-136">-Encoding</span></span>

<span data-ttu-id="3d59c-137">WsMan 프로토콜에 사용 되는 인코딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-137">Specifies the encoding used for the WsMan protocol.</span></span> <span data-ttu-id="3d59c-138">이 매개 변수에 허용 되는 값은 **Default**, **Utf8** 또는 **Utf16** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-138">The acceptable values for this parameter are: **Default**, **Utf8**, or **Utf16**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-139">-HttpPrefix</span><span class="sxs-lookup"><span data-stu-id="3d59c-139">-HttpPrefix</span></span>

<span data-ttu-id="3d59c-140">컴퓨터 이름과 포트 번호 뒤에 HTTP URL의 부분을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-140">Specifies the part of the HTTP URL after the computer name and port number.</span></span> <span data-ttu-id="3d59c-141">이를 변경 하는 것은 일반적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-141">Changing this is not common.</span></span> <span data-ttu-id="3d59c-142">기본적으로이 매개 변수의 값은 **/wsman** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-142">By default, the value of this parameter is **/wsman**.</span></span>

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-143">-가장</span><span class="sxs-lookup"><span data-stu-id="3d59c-143">-Impersonation</span></span>

<span data-ttu-id="3d59c-144">가장을 사용 하 여 WMI (WMI(Windows Management Instrumentation))에 대 한 DCOM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-144">Creates a DCOM session to Windows Management Instrumentation (WMI) using impersonation.</span></span>

<span data-ttu-id="3d59c-145">이 매개 변수에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-145">Valid values for this parameter are:</span></span>

- <span data-ttu-id="3d59c-146">기본값: DCOM은 일반적인 보안 협상 알고리즘을 사용 하 여 가장 수준을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-146">Default: DCOM can choose the impersonation level using its normal security negotiation algorithm.</span></span>
- <span data-ttu-id="3d59c-147">없음: 클라이언트가 서버에 대해 익명입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-147">None: The client is anonymous to the server.</span></span> <span data-ttu-id="3d59c-148">서버 프로세스는 클라이언트를 가장할 수 있지만 가장 토큰에는 정보가 포함 되어 있지 않으며 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-148">The server process can impersonate the client, but the impersonation token does not contain any information and cannot be used.</span></span>
- <span data-ttu-id="3d59c-149">식별: 개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-149">Identify: Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="3d59c-150">Impersonate: 개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-150">Impersonate: Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="3d59c-151">Delegate: 개체가 다른 개체가 호출자의 자격 증명을 사용할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-151">Delegate: Allows objects to permit other objects to use the credentials of the caller.</span></span>

<span data-ttu-id="3d59c-152">**가장** 을 지정 하지 않으면 Cmdlet은 `New-CimSession` **Impersonate** 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-152">If **Impersonation** is not specified, the `New-CimSession` cmdlet uses the value of **Impersonate**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-153">-MaxEnvelopeSizeKB</span><span class="sxs-lookup"><span data-stu-id="3d59c-153">-MaxEnvelopeSizeKB</span></span>

<span data-ttu-id="3d59c-154">어느 방향에서 든 WsMan XML 메시지의 크기 제한을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-154">Specifies the size limit of WsMan XML messages for either direction.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-155">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="3d59c-155">-NoEncryption</span></span>

<span data-ttu-id="3d59c-156">데이터 암호화가 해제 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-156">Specifies that data encryption is turned off.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-157">-PacketIntegrity</span><span class="sxs-lookup"><span data-stu-id="3d59c-157">-PacketIntegrity</span></span>

<span data-ttu-id="3d59c-158">WMI에 생성 된 DCOM 세션이 COM (구성 요소 개체 모델) _PacketIntegrity_ 기능을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-158">Specifies that the DCOM session created to WMI uses the Component Object Model (COM) _PacketIntegrity_ functionality.</span></span> <span data-ttu-id="3d59c-159">기본적으로 DCOM을 사용 하 여 만든 모든 CIM 세션은 **PacketIntegrity** 매개 변수를 **True** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-159">By default, all CIM sessions created using DCOM have the **PacketIntegrity** parameter set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-160">-PacketPrivacy</span><span class="sxs-lookup"><span data-stu-id="3d59c-160">-PacketPrivacy</span></span>

<span data-ttu-id="3d59c-161">COM _PacketPrivacy_ 를 사용 하 여 WMI에 대 한 DCOM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-161">Creates a DCOM session to WMI using the COM _PacketPrivacy_.</span></span> <span data-ttu-id="3d59c-162">기본적으로 DCOM을 사용 하 여 만든 모든 CIM 세션은 **PacketPrivacy** 매개 변수를 **true** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-162">By default, all CIM sessions created using DCOM have the **PacketPrivacy** parameter set to **true**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-163">-Protocol</span><span class="sxs-lookup"><span data-stu-id="3d59c-163">-Protocol</span></span>

<span data-ttu-id="3d59c-164">사용할 프로토콜을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-164">Specifies the protocol to use.</span></span> <span data-ttu-id="3d59c-165">이 매개 변수에 허용 되는 값은 **DCOM**, **Default** 또는 **Wsman** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-165">The acceptable values for this parameter are: **DCOM**, **Default**, or **Wsman**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-166">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="3d59c-166">-ProxyAuthentication</span></span>

<span data-ttu-id="3d59c-167">프록시 확인에 사용할 인증 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-167">Specifies the authentication method to use for proxy resolution.</span></span> <span data-ttu-id="3d59c-168">이 매개 변수에 허용 되는 값은 **Default**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain** 또는 **CredSsp** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-168">The acceptable values for this parameter are: **Default**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain**, or **CredSsp**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-169">-ProxyCertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="3d59c-169">-ProxyCertificateThumbprint</span></span>

<span data-ttu-id="3d59c-170">프록시 인증용 사용자 계정의 (x.509) 디지털 공개 키 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-170">Specifies the (x.509) digital public key certificate of a user account for proxy authentication.</span></span>
<span data-ttu-id="3d59c-171">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-171">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="3d59c-172">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-172">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="3d59c-173">로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-173">They can only be mapped to local user accounts and they do not work with domain accounts.</span></span>

<span data-ttu-id="3d59c-174">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-174">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="3d59c-175">-ProxyCredential</span></span>

<span data-ttu-id="3d59c-176">프록시 인증에 사용할 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-176">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="3d59c-177">다음 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-177">Enter one of the following:</span></span>

- <span data-ttu-id="3d59c-178">PSCredential 개체를 포함 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-178">A variable that contains a PSCredential object.</span></span>
- <span data-ttu-id="3d59c-179">와 같은 PSCredential 개체를 가져오는 명령입니다. `Get-Credential`</span><span class="sxs-lookup"><span data-stu-id="3d59c-179">A command that gets a PSCredential object, such as `Get-Credential`</span></span>

<span data-ttu-id="3d59c-180">이 옵션을 설정 하지 않으면 자격 증명을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-180">If this option is not set, then you cannot specify any credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-181">-ProxyType</span><span class="sxs-lookup"><span data-stu-id="3d59c-181">-ProxyType</span></span>

<span data-ttu-id="3d59c-182">사용할 호스트 이름 확인 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-182">Specifies the host name resolution mechanism to use.</span></span> <span data-ttu-id="3d59c-183">이 매개 변수에 허용 되는 값은 **None**, **WinHttp**, **Auto** 또는 **internetexplorer** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-183">The acceptable values for this parameter are: **None**, **WinHttp**, **Auto**, or **InternetExplorer**.</span></span>

<span data-ttu-id="3d59c-184">이 매개 변수의 기본값은 **Internetexplorer** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-184">The default value of this parameter is **InternetExplorer**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-185">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="3d59c-185">-SkipCACheck</span></span>

<span data-ttu-id="3d59c-186">HTTPS를 통해 연결할 때 클라이언트가 서버 인증서가 신뢰할 수 있는 CA (인증 기관)에 의해 서명 되었는지 확인 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-186">Indicates that when connecting over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="3d59c-187">원격 컴퓨터가 물리적으로 안전 하 고 격리 된 네트워크에 속해 있거나 원격 컴퓨터가 WinRM 구성에서 신뢰할 수 있는 호스트로 나열 되어 있는 경우와 같이 원격 컴퓨터를 다른 메커니즘을 사용 하 여 신뢰할 수 있는 경우에만이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-187">Use this parameter only when the remote computer is trusted using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated, or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-188">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="3d59c-188">-SkipCNCheck</span></span>

<span data-ttu-id="3d59c-189">서버의 인증서 CN (일반 이름)이 서버의 호스트 이름과 일치 하지 않아도 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-189">Indicates that the certificate common name (CN) of the server does not need to match the hostname of the server.</span></span> <span data-ttu-id="3d59c-190">이 매개 변수는 HTTPS 프로토콜을 사용 하는 신뢰할 수 있는 컴퓨터의 원격 작업에만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-190">Use this parameter for remote operations only with trusted computers that use the HTTPS protocol.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-191">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="3d59c-191">-SkipRevocationCheck</span></span>

<span data-ttu-id="3d59c-192">서버 인증서에 대 한 해지 확인을 건너뛰도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-192">Indicates that the revocation check for server certificates is skipped.</span></span> <span data-ttu-id="3d59c-193">이 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-193">Use this parameter only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-194">-UICulture</span><span class="sxs-lookup"><span data-stu-id="3d59c-194">-UICulture</span></span>

<span data-ttu-id="3d59c-195">CIM 세션에 사용할 사용자 인터페이스 문화권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-195">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="3d59c-196">다음 형식 중 하나를 사용 하 여이 매개 변수에 대 한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-196">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="3d59c-197">`<languagecode2>-<country/regioncode2>`"En-us"와 같은 형식의 문화권 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-197">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="3d59c-198">CultureInfo 개체를 포함 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-198">A variable that contains a CultureInfo object.</span></span>
- <span data-ttu-id="3d59c-199">와 같은 CultureInfo 개체를 가져오는 명령 `Get-Culture` 입니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-199">A command that gets a CultureInfo object, such as `Get-Culture`.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-200">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="3d59c-200">-UseSsl</span></span>

<span data-ttu-id="3d59c-201">원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL을 사용 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-201">Indicates that SSL should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="3d59c-202">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-202">By default, SSL is not used.</span></span> <span data-ttu-id="3d59c-203">WsMan은 HTTP를 사용 하는 경우에도 네트워크를 통해 전송 되는 모든 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-203">WsMan encrypts all content that is transmitted over the network, even when using HTTP.</span></span>

<span data-ttu-id="3d59c-204">이 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-204">This parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="3d59c-205">연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-205">If SSL is not available on the port used for the connection and you specify this parameter, then the command fails.</span></span>

<span data-ttu-id="3d59c-206">이 매개 변수는 **PacketPrivacy** 매개 변수가 지정 되지 않은 경우에만 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-206">It is recommended that you use this parameter only when the **PacketPrivacy** parameter is not specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d59c-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d59c-207">CommonParameters</span></span>

<span data-ttu-id="3d59c-208">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d59c-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d59c-209">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d59c-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d59c-210">입력</span><span class="sxs-lookup"><span data-stu-id="3d59c-210">INPUTS</span></span>

### <span data-ttu-id="3d59c-211">없음</span><span class="sxs-lookup"><span data-stu-id="3d59c-211">None</span></span>

<span data-ttu-id="3d59c-212">이 cmdlet은 입력 개체를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-212">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="3d59c-213">출력</span><span class="sxs-lookup"><span data-stu-id="3d59c-213">OUTPUTS</span></span>

### <span data-ttu-id="3d59c-214">CIMSessionOption</span><span class="sxs-lookup"><span data-stu-id="3d59c-214">CIMSessionOption</span></span>

<span data-ttu-id="3d59c-215">이 cmdlet은 CIM 세션 옵션 정보를 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d59c-215">This cmdlet returns an object that contains CIM session options information.</span></span>

## <span data-ttu-id="3d59c-216">참고</span><span class="sxs-lookup"><span data-stu-id="3d59c-216">NOTES</span></span>

## <span data-ttu-id="3d59c-217">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3d59c-217">RELATED LINKS</span></span>

[<span data-ttu-id="3d59c-218">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="3d59c-218">Get-ChildItem</span></span>](../microsoft.powershell.management/get-childitem.md)

[<span data-ttu-id="3d59c-219">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="3d59c-219">Get-Credential</span></span>](../microsoft.powershell.security/get-credential.md)

[<span data-ttu-id="3d59c-220">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="3d59c-220">Get-Culture</span></span>](../microsoft.powershell.utility/get-culture.md)

[<span data-ttu-id="3d59c-221">Get-Item</span><span class="sxs-lookup"><span data-stu-id="3d59c-221">Get-Item</span></span>](../microsoft.powershell.management/get-item.md)

[<span data-ttu-id="3d59c-222">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="3d59c-222">New-CimSession</span></span>](New-CimSession.md)

