---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: a1fa09116e7069f3fc7f3d196bffd20f491a93e2
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218745"
---
# <span data-ttu-id="c0ec3-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="c0ec3-103">Stop-Computer</span></span>

## <span data-ttu-id="c0ec3-104">개요</span><span class="sxs-lookup"><span data-stu-id="c0ec3-104">SYNOPSIS</span></span>
<span data-ttu-id="c0ec3-105">로컬 및 원격 컴퓨터를 중지(종료)합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="c0ec3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0ec3-106">SYNTAX</span></span>

### <span data-ttu-id="c0ec3-107">모두</span><span class="sxs-lookup"><span data-stu-id="c0ec3-107">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c0ec3-108">설명</span><span class="sxs-lookup"><span data-stu-id="c0ec3-108">DESCRIPTION</span></span>

<span data-ttu-id="c0ec3-109">`Stop-Computer`Cmdlet은 로컬 컴퓨터와 원격 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="c0ec3-110">의 매개 변수를 사용 `Stop-Computer` 하 여 인증 수준 및 대체 자격 증명을 지정 하 고 강제로 즉시 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-110">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

<span data-ttu-id="c0ec3-111">PowerShell 7.1에서 `Stop-Computer` Linux 및 macOS에 대해이 (가) 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-111">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="c0ec3-112">매개 변수는 이러한 플랫폼에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-112">The parameters have no effect on these platforms.</span></span> <span data-ttu-id="c0ec3-113">이 cmdlet은 네이티브 명령만 호출 하는 것입니다 `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-113">The cmdlet is just calling the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="c0ec3-114">예제</span><span class="sxs-lookup"><span data-stu-id="c0ec3-114">EXAMPLES</span></span>

### <span data-ttu-id="c0ec3-115">예 1: 로컬 컴퓨터 종료</span><span class="sxs-lookup"><span data-stu-id="c0ec3-115">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="c0ec3-116">이 예제에서는 로컬 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-116">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="c0ec3-117">예 2: 원격 컴퓨터와 로컬 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-117">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="c0ec3-118">이 예제에서는 두 원격 컴퓨터와 로컬 컴퓨터를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-118">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="c0ec3-119">`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 원격 컴퓨터와 로컬 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-119">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="c0ec3-120">각 컴퓨터는 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-120">Each computer is shut down.</span></span>

### <span data-ttu-id="c0ec3-121">예 3: 원격 컴퓨터를 백그라운드 작업으로 종료</span><span class="sxs-lookup"><span data-stu-id="c0ec3-121">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="c0ec3-122">이 예제에서는 `Stop-Computer` 두 원격 컴퓨터에서 백그라운드 작업으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-122">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="c0ec3-123">백그라운드 연산자는 `&` `Stop-Computer` 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-123">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="c0ec3-124">자세한 내용은 [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-124">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="c0ec3-125">`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 개의 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-125">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="c0ec3-126">`&`백그라운드 연산자는 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-126">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="c0ec3-127">작업 개체는 변수에 저장 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-127">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="c0ec3-128">변수의 작업 개체는 `$j` 파이프라인에서로 전송 되 고 `Receive-Job` 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-128">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="c0ec3-129">개체는 변수에 저장 됩니다 `$results` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-129">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="c0ec3-130">`$results`변수는 PowerShell 콘솔의 작업 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-130">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="c0ec3-131">예 4: 원격 컴퓨터 종료</span><span class="sxs-lookup"><span data-stu-id="c0ec3-131">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="c0ec3-132">이 예제에서는 지정 된 인증을 사용 하 여 원격 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-132">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="c0ec3-133">`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-133">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="c0ec3-134">**WsmanAuthentication** 매개 변수는 Kerberos를 사용 하 여 원격 연결을 설정 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-134">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="c0ec3-135">예 5: 도메인의 컴퓨터 종료</span><span class="sxs-lookup"><span data-stu-id="c0ec3-135">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="c0ec3-136">이 예에서 명령은 지정 된 도메인에 있는 모든 컴퓨터를 강제로 즉시 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-136">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="c0ec3-137">`Get-Content`**Path** 매개 변수를 사용 하 여 현재 디렉터리에서 도메인 컴퓨터의 목록으로 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-137">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="c0ec3-138">개체는 변수에 저장 됩니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-138">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="c0ec3-139">`Get-Credential`**Credential** 매개 변수를 사용 하 여 도메인 관리자의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-139">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="c0ec3-140">자격 증명은 변수에 저장 됩니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-140">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="c0ec3-141">`Stop-Computer` 컴퓨터의 **ComputerName** 매개 변수 목록에서 변수에 지정 된 컴퓨터를 종료 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-141">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="c0ec3-142">**Force** 매개 변수는 강제로 즉시 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-142">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="c0ec3-143">**Credential** 매개 변수는 변수에 저장 된 자격 증명을 제출 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-143">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="c0ec3-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0ec3-144">PARAMETERS</span></span>

### <span data-ttu-id="c0ec3-145">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c0ec3-145">-ComputerName</span></span>

<span data-ttu-id="c0ec3-146">중지할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-146">Specifies the computers to stop.</span></span> <span data-ttu-id="c0ec3-147">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-147">The default is the local computer.</span></span>

<span data-ttu-id="c0ec3-148">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-148">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="c0ec3-149">로컬 컴퓨터를 지정 하려면 컴퓨터 이름 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-149">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="c0ec3-150">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-150">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="c0ec3-151">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-151">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c0ec3-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c0ec3-152">-Confirm</span></span>

<span data-ttu-id="c0ec3-153">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-153">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0ec3-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="c0ec3-154">-Credential</span></span>

<span data-ttu-id="c0ec3-155">이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-155">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="c0ec3-156">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-156">The default is the current user.</span></span>

<span data-ttu-id="c0ec3-157">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-157">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c0ec3-158">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-158">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="c0ec3-159">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-159">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c0ec3-160">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="c0ec3-160">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0ec3-161">-Force</span><span class="sxs-lookup"><span data-stu-id="c0ec3-161">-Force</span></span>

<span data-ttu-id="c0ec3-162">컴퓨터를 강제로 즉시 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-162">Forces an immediate shut down of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0ec3-163">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="c0ec3-163">-WsmanAuthentication</span></span>

<span data-ttu-id="c0ec3-164">이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-164">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="c0ec3-165">기본값은 **Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-165">The default value is **Default**.</span></span>

<span data-ttu-id="c0ec3-166">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-166">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c0ec3-167">Basic</span><span class="sxs-lookup"><span data-stu-id="c0ec3-167">Basic</span></span>
- <span data-ttu-id="c0ec3-168">CredSSP</span><span class="sxs-lookup"><span data-stu-id="c0ec3-168">CredSSP</span></span>
- <span data-ttu-id="c0ec3-169">기본값</span><span class="sxs-lookup"><span data-stu-id="c0ec3-169">Default</span></span>
- <span data-ttu-id="c0ec3-170">다이제스트</span><span class="sxs-lookup"><span data-stu-id="c0ec3-170">Digest</span></span>
- <span data-ttu-id="c0ec3-171">Kerberos</span><span class="sxs-lookup"><span data-stu-id="c0ec3-171">Kerberos</span></span>
- <span data-ttu-id="c0ec3-172">Negotiate</span><span class="sxs-lookup"><span data-stu-id="c0ec3-172">Negotiate.</span></span>

<span data-ttu-id="c0ec3-173">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-173">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="c0ec3-174">사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-174">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c0ec3-175">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-175">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c0ec3-176">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-176">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="c0ec3-177">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-177">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0ec3-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c0ec3-178">-WhatIf</span></span>

<span data-ttu-id="c0ec3-179">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c0ec3-180">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-180">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0ec3-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0ec3-181">CommonParameters</span></span>

<span data-ttu-id="c0ec3-182">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0ec3-183">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0ec3-184">입력</span><span class="sxs-lookup"><span data-stu-id="c0ec3-184">INPUTS</span></span>

### <span data-ttu-id="c0ec3-185">없음</span><span class="sxs-lookup"><span data-stu-id="c0ec3-185">None</span></span>

<span data-ttu-id="c0ec3-186">이 cmdlet에는 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-186">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c0ec3-187">출력</span><span class="sxs-lookup"><span data-stu-id="c0ec3-187">OUTPUTS</span></span>

### <span data-ttu-id="c0ec3-188">없음</span><span class="sxs-lookup"><span data-stu-id="c0ec3-188">None</span></span>

## <span data-ttu-id="c0ec3-189">참고</span><span class="sxs-lookup"><span data-stu-id="c0ec3-189">NOTES</span></span>

<span data-ttu-id="c0ec3-190">이 cmdlet은 **Win32_OperatingSystem** WMI 클래스의 **Win32Shutdown** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-190">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="c0ec3-191">이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-191">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="c0ec3-192">PowerShell 7.1에서 `Stop-Computer` Linux 및 macOS에 대해이 (가) 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ec3-192">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="c0ec3-193">이러한 다룹니다 cmdlet은 네이티브 명령을 호출 합니다 `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="c0ec3-193">For these platorms, the cmdlet calls the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="c0ec3-194">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c0ec3-194">RELATED LINKS</span></span>

[<span data-ttu-id="c0ec3-195">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="c0ec3-195">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="c0ec3-196">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="c0ec3-196">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="c0ec3-197">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="c0ec3-197">Test-Connection</span></span>](Test-Connection.md)

