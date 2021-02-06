---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 59e70f75ac9d822db00419d84055d92a3882c11d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605475"
---
# <span data-ttu-id="27cc4-102">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="27cc4-102">New-CimSession</span></span>

## <span data-ttu-id="27cc4-103">개요</span><span class="sxs-lookup"><span data-stu-id="27cc4-103">SYNOPSIS</span></span>

<span data-ttu-id="27cc4-104">CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-104">Creates a CIM session.</span></span>

## <span data-ttu-id="27cc4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27cc4-105">SYNTAX</span></span>

### <span data-ttu-id="27cc4-106">CredentialParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="27cc4-106">CredentialParameterSet (Default)</span></span>

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### <span data-ttu-id="27cc4-107">CertificateParameterSet</span><span class="sxs-lookup"><span data-stu-id="27cc4-107">CertificateParameterSet</span></span>

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## <span data-ttu-id="27cc4-108">설명</span><span class="sxs-lookup"><span data-stu-id="27cc4-108">DESCRIPTION</span></span>

<span data-ttu-id="27cc4-109">`New-CimSession`Cmdlet은 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-109">The `New-CimSession` cmdlet creates a CIM session.</span></span> <span data-ttu-id="27cc4-110">CIM 세션은 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 연결을 나타내는 클라이언트 쪽 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-110">A CIM session is a client-side object representing a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="27cc4-111">CIM 세션에는 **컴퓨터 이름**, 사용 된 프로토콜 또는 다양 한 식별자와 같은 연결에 대 한 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-111">The CIM session contains information about the connection, such as **ComputerName**, the protocol used, or various identifiers.</span></span>

<span data-ttu-id="27cc4-112">이 cmdlet은 다른 모든 CIM cmdlet에서 사용할 수 있는 CIM 세션 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-112">This cmdlet returns a CIM session object that can be used by all other CIM cmdlets.</span></span>

## <span data-ttu-id="27cc4-113">예제</span><span class="sxs-lookup"><span data-stu-id="27cc4-113">EXAMPLES</span></span>

### <span data-ttu-id="27cc4-114">예 1: 기본 옵션을 사용 하 여 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-114">Example 1: Create a CIM session with default options</span></span>

<span data-ttu-id="27cc4-115">이 예에서는 기본 옵션을 사용 하 여 로컬 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-115">This example creates a local CIM session with default options.</span></span> <span data-ttu-id="27cc4-116">**ComputerName** 을 지정 하지 않으면에서 `New-CimSession` 로컬 컴퓨터에 대 한 DCOM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-116">If **ComputerName** is not specified, `New-CimSession` creates a DCOM session to the local computer.</span></span>

```powershell
New-CimSession
```

### <span data-ttu-id="27cc4-117">예 2: 특정 컴퓨터에 대 한 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-117">Example 2: Create a CIM session to a specific computer</span></span>

<span data-ttu-id="27cc4-118">이 예제에서는 **ComputerName** 으로 지정 된 컴퓨터에 대 한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-118">This example creates a CIM session to the computer specified by **ComputerName**.</span></span>
<span data-ttu-id="27cc4-119">기본적으로는 `New-CimSession` **ComputerName** 을 지정할 때 WSMan 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-119">By default, `New-CimSession` creates a WSMan session when **ComputerName** is specified.</span></span>

```powershell
New-CimSession -ComputerName Server01
```

### <span data-ttu-id="27cc4-120">예제 3: 여러 컴퓨터에 대 한 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-120">Example 3: Create a CIM session to multiple computers</span></span>

<span data-ttu-id="27cc4-121">이 예에서는 쉼표로 구분 된 목록에서 **ComputerName** 으로 지정 된 각 컴퓨터에 대 한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-121">This example creates a CIM session to each of the computers specified by **ComputerName**, in the comma separated list.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### <span data-ttu-id="27cc4-122">예제 4: 친숙 한 이름으로 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-122">Example 4: Create a CIM session with a friendly name</span></span>

<span data-ttu-id="27cc4-123">이 예에서는 쉼표로 구분 된 목록에서 **ComputerName** 으로 지정 된 각 컴퓨터에 대 한 원격 CIM 세션을 만들고 **이름** 을 지정 하 여 새 세션에 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-123">This example creates a remote CIM session to each of the computers specified by **ComputerName**, in the comma separated list, and assigns a friendly name to the new sessions, by specifying **Name**.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

<span data-ttu-id="27cc4-124">CIM 세션의 친숙 한 이름을 사용 하 여 다른 CIM cmdlet의 세션 (예: [CimSession)](Get-CimSession.md)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-124">You can use the friendly name of a CIM session to refer to the session in other CIM cmdlets, for example, [Get-CimSession](Get-CimSession.md).</span></span>

### <span data-ttu-id="27cc4-125">예 5: PSCredential 개체를 사용 하 여 컴퓨터에 대 한 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-125">Example 5: Create a CIM session to a computer using a PSCredential object</span></span>

<span data-ttu-id="27cc4-126">이 예제에서는 **자격 증명** 으로 지정 된 **PSCredential** 개체와 **인증** 에 지정 된 인증 유형을 사용 하 여 **ComputerName** 에서 지정 된 컴퓨터에 대 한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-126">This example creates a CIM session to the computer specified by **ComputerName**, using the **PSCredential** object specified by **Credential**, and the authentication type specified by **Authentication**.</span></span>

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

<span data-ttu-id="27cc4-127">Cmdlet을 사용 하 여 **PSCredential** 개체를 만들 수 있습니다 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) .</span><span class="sxs-lookup"><span data-stu-id="27cc4-127">You can create a **PSCredential** object using the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

### <span data-ttu-id="27cc4-128">예제 6: 특정 포트를 사용 하 여 컴퓨터에 대 한 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-128">Example 6: Create a CIM session to a computer using a specific port</span></span>

<span data-ttu-id="27cc4-129">이 예제에서는 **포트** 에 지정 된 TCP 포트를 사용 하 여 **ComputerName** 에서 지정 된 컴퓨터에 대 한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-129">This example creates a CIM session to the computer specified by **ComputerName** using the TCP port specified by **Port**.</span></span>

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### <span data-ttu-id="27cc4-130">예 7: DCOM을 사용 하 여 CIM 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="27cc4-130">Example 7: Create a CIM session using DCOM</span></span>

<span data-ttu-id="27cc4-131">이 예에서는 WSMan 대신 DCOM (Distributed COM) 프로토콜을 사용 하 여 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-131">This example creates a CIM session using the Distributed COM (DCOM) protocol instead of WSMan.</span></span>

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## <span data-ttu-id="27cc4-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27cc4-132">PARAMETERS</span></span>

### <span data-ttu-id="27cc4-133">-인증</span><span class="sxs-lookup"><span data-stu-id="27cc4-133">-Authentication</span></span>

<span data-ttu-id="27cc4-134">사용자의 자격 증명에 사용 되는 인증 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-134">Specifies the authentication type used for the user's credentials.</span></span> <span data-ttu-id="27cc4-135">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27cc4-136">기본값</span><span class="sxs-lookup"><span data-stu-id="27cc4-136">Default</span></span>
- <span data-ttu-id="27cc4-137">다이제스트</span><span class="sxs-lookup"><span data-stu-id="27cc4-137">Digest</span></span>
- <span data-ttu-id="27cc4-138">Negotiate</span><span class="sxs-lookup"><span data-stu-id="27cc4-138">Negotiate</span></span>
- <span data-ttu-id="27cc4-139">Basic</span><span class="sxs-lookup"><span data-stu-id="27cc4-139">Basic</span></span>
- <span data-ttu-id="27cc4-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="27cc4-140">Kerberos</span></span>
- <span data-ttu-id="27cc4-141">NtlmDomain</span><span class="sxs-lookup"><span data-stu-id="27cc4-141">NtlmDomain</span></span>
- <span data-ttu-id="27cc4-142">CredSsp</span><span class="sxs-lookup"><span data-stu-id="27cc4-142">CredSsp</span></span>

<span data-ttu-id="27cc4-143">**NtlmDomain** 인증 유형을 사용 하 여 로컬 컴퓨터에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-143">You cannot use the **NtlmDomain** authentication type for connection to the local computer.</span></span> <span data-ttu-id="27cc4-144">**CredSSP** 인증은 windows Vista, windows Server 2008 및 이후 버전의 windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-144">**CredSSP** authentication is available only in Windows Vista, Windows Server 2008, and later versions of Windows.</span></span>

> [!CAUTION]
> <span data-ttu-id="27cc4-145">CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 경우와 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-145">Credential Security Service Provider (CredSSP) authentication is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="27cc4-146">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="27cc4-147">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="27cc4-148">-CertificateThumbprint</span></span>

<span data-ttu-id="27cc4-149">이 작업을 수행할 수 있는 권한이 있는 사용자 계정의 디지털 공개 키 인증서 (x.509)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-149">Specifies the digital public key certificate (X.509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="27cc4-150">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="27cc4-151">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="27cc4-152">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="27cc4-153">인증서 지문을 가져오려면 [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) PowerShell 인증서 공급자에서 또는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-153">To get a certificate thumbprint, use the [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) or [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in the PowerShell Certificate Provider.</span></span>

<span data-ttu-id="27cc4-154">자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27cc4-154">For more information, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

```yaml
Type: System.String
Parameter Sets: CertificateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="27cc4-155">-ComputerName</span></span>

<span data-ttu-id="27cc4-156">CIM 세션을 만들 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-156">Specifies the name of the computer to which to create the CIM session.</span></span> <span data-ttu-id="27cc4-157">단일 컴퓨터 이름 또는 쉼표로 구분 된 여러 컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-157">Specify either a single computer name, or multiple computer names separated by a comma.</span></span>

<span data-ttu-id="27cc4-158">**ComputerName** 을 지정 하지 않으면 로컬 컴퓨터에 대 한 CIM 세션이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-158">If **ComputerName** is not specified, a CIM session to the local computer is created.</span></span> <span data-ttu-id="27cc4-159">다음 형식 중 하나로 컴퓨터 이름에 대 한 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-159">You can specify the value for computer name in one of the following formats:</span></span>

- <span data-ttu-id="27cc4-160">하나 이상의 NetBIOS 이름</span><span class="sxs-lookup"><span data-stu-id="27cc4-160">One or more NetBIOS names</span></span>
- <span data-ttu-id="27cc4-161">하나 이상의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="27cc4-161">One or more IP addresses</span></span>
- <span data-ttu-id="27cc4-162">하나 이상의 정규화 된 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-162">One or more fully qualified domain names.</span></span>

<span data-ttu-id="27cc4-163">컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화 된 도메인 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-163">If the computer is in a different domain than the user, you must specify the fully qualified domain name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-164">-Credential</span><span class="sxs-lookup"><span data-stu-id="27cc4-164">-Credential</span></span>

<span data-ttu-id="27cc4-165">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-165">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="27cc4-166">**자격 증명** 을 지정 하지 않으면 현재 사용자 계정이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-166">If **Credential** is not specified, the current user account is used.</span></span>

<span data-ttu-id="27cc4-167">다음 형식 중 하나를 사용 하 여 **자격 증명** 의 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-167">Specify the value for **Credential** using one of the following formats:</span></span>

- <span data-ttu-id="27cc4-168">사용자 이름: "User01"</span><span class="sxs-lookup"><span data-stu-id="27cc4-168">A user name: "User01"</span></span>
- <span data-ttu-id="27cc4-169">도메인 이름 및 사용자 이름: "Domain01\User01"</span><span class="sxs-lookup"><span data-stu-id="27cc4-169">A domain name and a user name: "Domain01\User01"</span></span>
- <span data-ttu-id="27cc4-170">사용자 계정 이름: " User@Domain.com "</span><span class="sxs-lookup"><span data-stu-id="27cc4-170">A user principal name: "User@Domain.com"</span></span>
- <span data-ttu-id="27cc4-171">Cmdlet에서 반환 된 개체와 같은 PSCredential 개체 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 입니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-171">A PSCredential object, such as one returned by the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

<span data-ttu-id="27cc4-172">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-172">When you type a user name, you are prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-173">-Name</span><span class="sxs-lookup"><span data-stu-id="27cc4-173">-Name</span></span>

<span data-ttu-id="27cc4-174">CIM 세션의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-174">Specifies a friendly name for the CIM session.</span></span>

<span data-ttu-id="27cc4-175">[CimSession](Get-CimSession.md) cmdlet과 같은 다른 cmdlet을 사용 하는 경우 이름을 사용 하 여 CIM 세션을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-175">You can use the name to refer to the CIM session when using other cmdlets, such as the [Get-CimSession](Get-CimSession.md) cmdlet.</span></span>
<span data-ttu-id="27cc4-176">이 이름은 컴퓨터나 현재 세션에서 고유하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-176">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-177">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="27cc4-177">-OperationTimeoutSec</span></span>

<span data-ttu-id="27cc4-178">Cmdlet이 서버의 응답을 대기 하는 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-178">Duration for which the cmdlet waits for a response from the server.</span></span>

<span data-ttu-id="27cc4-179">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-179">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="27cc4-180">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-180">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-181">-Port</span><span class="sxs-lookup"><span data-stu-id="27cc4-181">-Port</span></span>

<span data-ttu-id="27cc4-182">이 명령에 사용되는 원격 컴퓨터의 네트워크 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-182">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="27cc4-183">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-183">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="27cc4-184">기본 포트는 5985(HTTP용 WinRM 포트) 및 5986(HTTPS용 WinRM 포트)입니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-184">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="27cc4-185">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-185">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="27cc4-186">다음 명령을 사용하여 수신기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-186">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

<span data-ttu-id="27cc4-187">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="27cc4-187">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="27cc4-188">명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-188">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="27cc4-189">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-189">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-190">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="27cc4-190">-SessionOption</span></span>

<span data-ttu-id="27cc4-191">새 CIM 세션의 고급 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-191">Sets advanced options for the new CIM session.</span></span> <span data-ttu-id="27cc4-192">Cmdlet을 사용 하 여 만든 **CimSessionOption** 개체의 이름을 입력 합니다 [`New-CimSessionOption`](New-CimSessionOption.md) .</span><span class="sxs-lookup"><span data-stu-id="27cc4-192">Enter the name of a **CimSessionOption** object created using the [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-193">-SkipTestConnection</span><span class="sxs-lookup"><span data-stu-id="27cc4-193">-SkipTestConnection</span></span>

<span data-ttu-id="27cc4-194">기본적으로 cmdlet은 원격 `New-CimSession` 서버가 **port** 매개 변수를 사용 하 여 지정 된 포트 번호에서 수신 대기 하 고 있는지 확인 하 고 지정 된 계정 자격 증명을 확인 하는 두 가지 이유로 원격 WS-Management 끝점과의 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-194">By default, the `New-CimSession` cmdlet establishes a connection with a remote WS-Management endpoint for two reasons: to verify that the remote server is listening on the port number that is specified using the **Port** parameter, and to verify the specified account credentials.</span></span> <span data-ttu-id="27cc4-195">확인은 표준 WS-Identity 작업을 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-195">The verification is accomplished using a standard WS-Identity operation.</span></span> <span data-ttu-id="27cc4-196">원격 WS-Management 끝점에서 WS-Id를 사용할 수 없는 경우 또는 일부 데이터 전송 시간을 줄이기 위해 **Skiptestconnection** 스위치 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-196">You can add the **SkipTestConnection** switch parameter if the remote WS-Management endpoint cannot use WS-Identify, or to reduce some data transmission time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27cc4-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27cc4-197">CommonParameters</span></span>

<span data-ttu-id="27cc4-198">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27cc4-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27cc4-199">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27cc4-199">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="27cc4-200">입력</span><span class="sxs-lookup"><span data-stu-id="27cc4-200">INPUTS</span></span>

### <span data-ttu-id="27cc4-201">없음</span><span class="sxs-lookup"><span data-stu-id="27cc4-201">None</span></span>

<span data-ttu-id="27cc4-202">이 cmdlet은 입력을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27cc4-202">This cmdlet accepts no inputs.</span></span>

## <span data-ttu-id="27cc4-203">출력</span><span class="sxs-lookup"><span data-stu-id="27cc4-203">OUTPUTS</span></span>

### <span data-ttu-id="27cc4-204">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="27cc4-204">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="27cc4-205">참고</span><span class="sxs-lookup"><span data-stu-id="27cc4-205">NOTES</span></span>

## <span data-ttu-id="27cc4-206">관련 링크</span><span class="sxs-lookup"><span data-stu-id="27cc4-206">RELATED LINKS</span></span>

[<span data-ttu-id="27cc4-207">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="27cc4-207">Get-ChildItem</span></span>](../Microsoft.Powershell.Management/Get-ChildItem.md)

[<span data-ttu-id="27cc4-208">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="27cc4-208">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="27cc4-209">Get-Item</span><span class="sxs-lookup"><span data-stu-id="27cc4-209">Get-Item</span></span>](../Microsoft.Powershell.Management/Get-Item.md)

[<span data-ttu-id="27cc4-210">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="27cc4-210">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="27cc4-211">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="27cc4-211">Remove-CimSession</span></span>](Remove-CimSession.md)

[<span data-ttu-id="27cc4-212">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="27cc4-212">New-CimSessionOption</span></span>](New-CimSessionOption.md)

[<span data-ttu-id="27cc4-213">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="27cc4-213">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

