---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213362"
---
# <span data-ttu-id="20c34-103">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="20c34-103">New-PSWorkflowSession</span></span>

## <span data-ttu-id="20c34-104">개요</span><span class="sxs-lookup"><span data-stu-id="20c34-104">SYNOPSIS</span></span>
<span data-ttu-id="20c34-105">워크플로 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-105">Creates a workflow session.</span></span>

## <span data-ttu-id="20c34-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20c34-106">SYNTAX</span></span>

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## <span data-ttu-id="20c34-107">설명</span><span class="sxs-lookup"><span data-stu-id="20c34-107">DESCRIPTION</span></span>

<span data-ttu-id="20c34-108">`New-PSWorkflowSession`Cmdlet은 Windows PowerShell 워크플로를 실행 하기 위해 특별히 설계 된 **PSSession** (사용자 관리 세션)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-108">The `New-PSWorkflowSession` cmdlet creates a user-managed session ( **PSSession** ) that is especially designed for running Windows PowerShell workflows.</span></span> <span data-ttu-id="20c34-109">이 cmdlet은 워크플로에 필요한 스크립트, 형식 및 서식 지정 파일과 옵션이 포함된 Microsoft.PowerShell.Workflow 세션 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-109">It uses the Microsoft.PowerShell.Workflow session configuration, which includes scripts, type and formatting files, and options that are required for workflows.</span></span>

<span data-ttu-id="20c34-110">`New-PSWorkflowSession`또는 해당 별칭 ()을 사용할 수 있습니다 `nwsn` .</span><span class="sxs-lookup"><span data-stu-id="20c34-110">You can use `New-PSWorkflowSession` or its alias, `nwsn`.</span></span>

<span data-ttu-id="20c34-111">또한 이 명령에 워크플로 일반 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-111">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="20c34-112">워크플로 일반 매개 변수에 대 한 자세한 내용은을 참조 하십시오 [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="20c34-112">For more information about workflow common parameters, see [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="20c34-113">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="20c34-114">예제</span><span class="sxs-lookup"><span data-stu-id="20c34-114">EXAMPLES</span></span>

### <span data-ttu-id="20c34-115">예제 1: 원격 컴퓨터에서 워크플로 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="20c34-115">Example 1: Create a workflow session on a remote computer</span></span>

<span data-ttu-id="20c34-116">이 예제에서는 ServerNode01 원격 컴퓨터에 **Workflowtests** 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-116">This example creates the **WorkflowTests** session on the ServerNode01 remote computer.</span></span>

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

<span data-ttu-id="20c34-117">**Sessionoption** 매개 변수 값은 `New-PSSessionOption` 세션에서 **Drop** 으로 출력 버퍼링 모드를 설정 하는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-117">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that sets the output buffering mode in the session to **Drop** .</span></span>

### <span data-ttu-id="20c34-118">예 2: 여러 원격 컴퓨터에 워크플로 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="20c34-118">Example 2: Create workflow sessions on multiple remote computers</span></span>

<span data-ttu-id="20c34-119">이 예제에서는 ServerNode01 및 Server12 컴퓨터에 워크플로 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-119">This example creates workflow sessions on the ServerNode01 and Server12 computers.</span></span> <span data-ttu-id="20c34-120">이 명령은 **Credential** 매개 변수를 사용하여 도메인 관리자 권한으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-120">The command uses the **Credential** parameter to run with the permissions of the domain administrator.</span></span>

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

<span data-ttu-id="20c34-121">이 명령은 **ThrottleLimit** 매개 변수를 사용하여 명령당 제한 한도를 150으로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-121">The command uses the **ThrottleLimit** parameter to increase the per-command throttle limit to 150.</span></span>
<span data-ttu-id="20c34-122">이 값은 **Microsoft. PowerShell 워크플로** 세션 구성에 설정 된 기본 제한 제한인 100 보다 우선 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-122">This value takes precedence over the default throttle limit of 100 that is set in the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

## <span data-ttu-id="20c34-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20c34-123">PARAMETERS</span></span>

### <span data-ttu-id="20c34-124">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="20c34-124">-ApplicationName</span></span>

<span data-ttu-id="20c34-125">연결 URI의 애플리케이션 이름 세그먼트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-125">Specifies the application name segment of the connection URI.</span></span>

<span data-ttu-id="20c34-126">기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-126">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="20c34-127">이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-127">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="20c34-128">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-128">This value is appropriate for most uses.</span></span> <span data-ttu-id="20c34-129">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-129">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="20c34-130">WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-130">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="20c34-131">이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-131">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="20c34-132">-인증</span><span class="sxs-lookup"><span data-stu-id="20c34-132">-Authentication</span></span>

<span data-ttu-id="20c34-133">사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-133">Specifies the mechanism that is used to authenticate the user credentials.</span></span>
<span data-ttu-id="20c34-134">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="20c34-135">기본값</span><span class="sxs-lookup"><span data-stu-id="20c34-135">Default</span></span>
- <span data-ttu-id="20c34-136">Basic</span><span class="sxs-lookup"><span data-stu-id="20c34-136">Basic</span></span>
- <span data-ttu-id="20c34-137">Credssp</span><span class="sxs-lookup"><span data-stu-id="20c34-137">Credssp</span></span>
- <span data-ttu-id="20c34-138">다이제스트</span><span class="sxs-lookup"><span data-stu-id="20c34-138">Digest</span></span>
- <span data-ttu-id="20c34-139">Kerberos</span><span class="sxs-lookup"><span data-stu-id="20c34-139">Kerberos</span></span>
- <span data-ttu-id="20c34-140">Negotiate</span><span class="sxs-lookup"><span data-stu-id="20c34-140">Negotiate</span></span>
- <span data-ttu-id="20c34-141">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="20c34-141">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="20c34-142">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-142">The default value is Default.</span></span>

<span data-ttu-id="20c34-143">CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-143">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="20c34-144">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-144">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="20c34-145">사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-145">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="20c34-146">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="20c34-147">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20c34-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="20c34-148">-CertificateThumbprint</span></span>

<span data-ttu-id="20c34-149">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-149">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="20c34-150">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="20c34-151">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="20c34-152">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="20c34-153">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` Windows PowerShell Cert: 드라이브에서 cmdlet 또는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-153">To get a certificate thumbprint, use the `Get-Item` cmdlet or the `Get-ChildItem` cmdlet in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="20c34-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="20c34-154">-ComputerName</span></span>

<span data-ttu-id="20c34-155">지정 된 컴퓨터에 대 한 영구 연결 ( **PSSession** )을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-155">Creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="20c34-156">여러 컴퓨터 이름을 입력 하면 Windows PowerShell에서 각 컴퓨터에 대해 **하나씩 여러 개의 pssession을 만듭니다** .</span><span class="sxs-lookup"><span data-stu-id="20c34-156">If you enter multiple computer names, Windows PowerShell creates multiple **PSSessions** , one for each computer.</span></span> <span data-ttu-id="20c34-157">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-157">The default is the local computer.</span></span>

<span data-ttu-id="20c34-158">하나 이상의 원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-158">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="20c34-159">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-159">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="20c34-160">컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-160">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="20c34-161">컴퓨터 이름을 따옴표로 묶을 수도 있습니다 `New-PSWorkflowSession` .</span><span class="sxs-lookup"><span data-stu-id="20c34-161">You can also pipe a computer name, in quotation marks to `New-PSWorkflowSession`.</span></span>

<span data-ttu-id="20c34-162">**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-162">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="20c34-163">또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-163">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="20c34-164">TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="20c34-164">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="20c34-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="20c34-165">-Credential</span></span>

<span data-ttu-id="20c34-166">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="20c34-167">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-167">The default is the current user.</span></span> <span data-ttu-id="20c34-168">User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 하거나, cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="20c34-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com, or enter a **PSCredential** object, such as one returned by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="20c34-169">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-169">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20c34-170">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="20c34-170">-EnableNetworkAccess</span></span>

<span data-ttu-id="20c34-171">이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-171">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="20c34-172">대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-172">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="20c34-173">예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-173">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="20c34-174">루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-174">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="20c34-175">루프백 세션을 만들려면 **ComputerName** 매개 변수를 지정 하거나 해당 값을 dot, localhost 또는 로컬 컴퓨터 이름으로 설정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-175">To create a loopback session, do not specify the **ComputerName** parameter or set its value to dot, localhost, or the name of the local computer.</span></span>

<span data-ttu-id="20c34-176">기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 포함 하는 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-176">By default, loopback sessions are created that have a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="20c34-177">**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-177">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="20c34-178">원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 매개 변수를 지정 하면 명령이 성공 하지만 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-178">If you specify the **EnableNetworkAccess** parameter when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="20c34-179">또한 세션 자격 증명을 다른 컴퓨터에 위임하는 **CredSSP** 매개 변수의 **Authentication** 값을 사용하여 루프백 세션에서 원격 액세스를 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-179">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="20c34-180">악의적인 액세스 로부터 컴퓨터를 보호 하기 위해 **EnableNetworkAccess** 매개 변수를 사용 하 여 만든 대화형 토큰을 포함 하는 분리 된 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-180">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="20c34-181">CredSSP 인증을 사용하는 연결이 끊어진 세션은 다른 컴퓨터에서 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-181">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="20c34-182">자세한 내용은 `Disconnect-PSSession` cmdlet을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-182">For more information, see the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="20c34-183">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="20c34-184">-Name</span><span class="sxs-lookup"><span data-stu-id="20c34-184">-Name</span></span>

<span data-ttu-id="20c34-185">워크플로 세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-185">Specifies a friendly name for the workflow session.</span></span> <span data-ttu-id="20c34-186">다른 cmdlet (예: 및)에서이 이름을 사용할 수 있습니다 `Get-PSSession` `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="20c34-186">You can use the name with other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="20c34-187">이 이름은 컴퓨터나 현재 세션에서 고유하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-187">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20c34-188">-Port</span><span class="sxs-lookup"><span data-stu-id="20c34-188">-Port</span></span>

<span data-ttu-id="20c34-189">이 명령에 사용되는 원격 컴퓨터의 네트워크 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-189">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="20c34-190">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-190">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="20c34-191">기본 포트는 5985 (HTTP의 경우 WinRM 포트) 및 5986 (HTTPS의 경우 WinRM 포트)입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-191">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="20c34-192">다른 포트를 사용 하기 전에 해당 포트에서 수신 대기 하도록 원격 컴퓨터의 WinRM 수신기를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-192">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="20c34-193">다음 명령을 사용하여 수신기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-193">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="20c34-194">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-194">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="20c34-195">명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-195">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="20c34-196">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-196">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="20c34-197">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="20c34-197">-SessionOption</span></span>

<span data-ttu-id="20c34-198">세션에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-198">Specifies advanced options for the session.</span></span> <span data-ttu-id="20c34-199">Cmdlet을 사용 하 여 만든 것과 같은 **Sessionoption** 개체를 입력 합니다 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="20c34-199">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="20c34-200">옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-200">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="20c34-201">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-201">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="20c34-202">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-202">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="20c34-203">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-203">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="20c34-204">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-204">For more information about session configurations, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="20c34-205">기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="20c34-205">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="20c34-206">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-206">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20c34-207">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="20c34-207">-ThrottleLimit</span></span>

<span data-ttu-id="20c34-208">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-208">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="20c34-209">이 매개 변수를 생략 하거나 값 0을 입력 하면 **Microsoft. PowerShellWorkflow** 세션 구성 100에 대 한 기본값이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-209">If you omit this parameter or enter a value of 0 (zero), the default value for the **Microsoft.PowerShellWorkflow** session configuration, 100, is used.</span></span>

<span data-ttu-id="20c34-210">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-210">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20c34-211">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="20c34-211">-UseSSL</span></span>

<span data-ttu-id="20c34-212">이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-212">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="20c34-213">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-213">By default, SSL is not used.</span></span>

<span data-ttu-id="20c34-214">WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-214">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="20c34-215">**UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-215">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="20c34-216">이 매개 변수를 지정 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-216">If you specify this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="20c34-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20c34-217">CommonParameters</span></span>

<span data-ttu-id="20c34-218">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20c34-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20c34-219">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20c34-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20c34-220">입력</span><span class="sxs-lookup"><span data-stu-id="20c34-220">INPUTS</span></span>

### <span data-ttu-id="20c34-221">Runspace [], System.string이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-221">System.Management.Automation.Runspaces.PSSession[], System.String</span></span>

<span data-ttu-id="20c34-222">이 cmdlet에 세션 또는 컴퓨터 이름을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-222">You can pipe a session or a computer name to this cmdlet.</span></span>

## <span data-ttu-id="20c34-223">출력</span><span class="sxs-lookup"><span data-stu-id="20c34-223">OUTPUTS</span></span>

### <span data-ttu-id="20c34-224">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-224">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="20c34-225">참고</span><span class="sxs-lookup"><span data-stu-id="20c34-225">NOTES</span></span>

<span data-ttu-id="20c34-226">`New-PSWorkflowSession`명령은 다음 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c34-226">A `New-PSWorkflowSession` command is equivalent to the following command:</span></span>

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## <span data-ttu-id="20c34-227">관련 링크</span><span class="sxs-lookup"><span data-stu-id="20c34-227">RELATED LINKS</span></span>

[<span data-ttu-id="20c34-228">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="20c34-228">Disconnect-PSSession</span></span>](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[<span data-ttu-id="20c34-229">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="20c34-229">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="20c34-230">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="20c34-230">New-PSTransportOption</span></span>](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[<span data-ttu-id="20c34-231">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="20c34-231">Register-PSSessionConfiguration</span></span>](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[<span data-ttu-id="20c34-232">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="20c34-232">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="20c34-233">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="20c34-233">about_Session_Configurations</span></span>](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[<span data-ttu-id="20c34-234">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="20c34-234">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="20c34-235">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="20c34-235">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
