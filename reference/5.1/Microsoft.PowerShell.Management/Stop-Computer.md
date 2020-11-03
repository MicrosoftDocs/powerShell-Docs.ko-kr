---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218257"
---
# <span data-ttu-id="9911d-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-103">Stop-Computer</span></span>

## <span data-ttu-id="9911d-104">개요</span><span class="sxs-lookup"><span data-stu-id="9911d-104">SYNOPSIS</span></span>
<span data-ttu-id="9911d-105">로컬 및 원격 컴퓨터를 중지(종료)합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="9911d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9911d-106">SYNTAX</span></span>

### <span data-ttu-id="9911d-107">모두</span><span class="sxs-lookup"><span data-stu-id="9911d-107">All</span></span>

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9911d-108">설명</span><span class="sxs-lookup"><span data-stu-id="9911d-108">DESCRIPTION</span></span>

<span data-ttu-id="9911d-109">`Stop-Computer`Cmdlet은 로컬 컴퓨터와 원격 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="9911d-110">의 매개 변수를 사용 하 여 `Stop-Computer` 종료 작업을 백그라운드 작업으로 실행 하 고, 인증 수준 및 대체 자격 증명을 지정 하 고, 명령을 실행 하기 위해 만들어지는 동시 연결을 제한 하 고, 강제로 즉시 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-110">You can use the parameters of `Stop-Computer` to run the shutdown operations as a background job, to specify the authentication levels and alternate credentials, to limit the concurrent connections that are created to run the command, and to force an immediate shut down.</span></span>

<span data-ttu-id="9911d-111">**AsJob** 매개 변수를 사용 하지 않으면이 Cmdlet은 PowerShell 원격을 요구 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-111">This cmdlet doesn't require PowerShell remoting unless you use the **AsJob** parameter.</span></span>

## <span data-ttu-id="9911d-112">예제</span><span class="sxs-lookup"><span data-stu-id="9911d-112">EXAMPLES</span></span>

### <span data-ttu-id="9911d-113">예 1: 로컬 컴퓨터 종료</span><span class="sxs-lookup"><span data-stu-id="9911d-113">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="9911d-114">이 예제에서는 로컬 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-114">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="9911d-115">예 2: 원격 컴퓨터와 로컬 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-115">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="9911d-116">이 예제에서는 두 원격 컴퓨터와 로컬 컴퓨터를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-116">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="9911d-117">`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 원격 컴퓨터와 로컬 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-117">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="9911d-118">각 컴퓨터는 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-118">Each computer is shut down.</span></span>

### <span data-ttu-id="9911d-119">예 3: 원격 컴퓨터를 백그라운드 작업으로 종료</span><span class="sxs-lookup"><span data-stu-id="9911d-119">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="9911d-120">이 예제에서는 `Stop-Computer` 두 원격 컴퓨터에서 백그라운드 작업으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-120">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

<span data-ttu-id="9911d-121">`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 두 개의 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-121">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="9911d-122">**AsJob** 매개 변수는 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-122">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="9911d-123">작업 개체는 변수에 저장 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="9911d-123">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="9911d-124">변수의 작업 개체는 `$j` 파이프라인에서로 전송 되 고 `Receive-Job` 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-124">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="9911d-125">개체는 변수에 저장 됩니다 `$results` .</span><span class="sxs-lookup"><span data-stu-id="9911d-125">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="9911d-126">`$results`변수는 PowerShell 콘솔의 작업 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-126">The `$results` variable displays the job information in the PowerShell console.</span></span>

<span data-ttu-id="9911d-127">**AsJob** 은 로컬 컴퓨터에 작업을 만들고 결과를 로컬 컴퓨터에 자동으로 반환 하기 때문에 로컬 명령으로를 실행할 수 있습니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="9911d-127">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

### <span data-ttu-id="9911d-128">예 4: 원격 컴퓨터 종료</span><span class="sxs-lookup"><span data-stu-id="9911d-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="9911d-129">이 예제에서는 지정 된 인증을 사용 하 여 원격 컴퓨터를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="9911d-130">`Stop-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="9911d-131">**가장** 매개 변수는 사용자 지정 된 가장을 지정 하 고 **DcomAuthentication** 매개 변수는 인증 수준 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-131">The **Impersonation** parameter specifies a customized impersonation and the **DcomAuthentication** parameter specifies authentication-level settings.</span></span>

### <span data-ttu-id="9911d-132">예 5: 도메인의 컴퓨터 종료</span><span class="sxs-lookup"><span data-stu-id="9911d-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="9911d-133">이 예에서 명령은 지정 된 도메인에 있는 모든 컴퓨터를 강제로 즉시 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

<span data-ttu-id="9911d-134">`Get-Content`**Path** 매개 변수를 사용 하 여 현재 디렉터리에서 도메인 컴퓨터의 목록으로 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="9911d-135">개체는 변수에 저장 됩니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9911d-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="9911d-136">`Get-Credential`**Credential** 매개 변수를 사용 하 여 도메인 관리자의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="9911d-137">자격 증명은 변수에 저장 됩니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="9911d-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="9911d-138">`Stop-Computer` 컴퓨터의 **ComputerName** 매개 변수 목록에서 변수에 지정 된 컴퓨터를 종료 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="9911d-139">**Force** 매개 변수는 강제로 즉시 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="9911d-140">**ThrottleLimit** 매개 변수는 명령을 10 개의 동시 연결로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-140">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span> <span data-ttu-id="9911d-141">**Credential** 매개 변수는 변수에 저장 된 자격 증명을 제출 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="9911d-141">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="9911d-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9911d-142">PARAMETERS</span></span>

### <span data-ttu-id="9911d-143">-AsJob</span><span class="sxs-lookup"><span data-stu-id="9911d-143">-AsJob</span></span>

<span data-ttu-id="9911d-144">이 cmdlet이 백그라운드 작업으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-144">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="9911d-145">이 매개 변수를 사용 하려면 원격을 사용 하도록 로컬 및 원격 컴퓨터를 구성 해야 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-145">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="9911d-146">자세한 내용은 [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9911d-146">For more information, see [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="9911d-147">**AsJob** 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-147">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="9911d-148">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-148">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="9911d-149">AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-149">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="9911d-150">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="9911d-150">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="9911d-151">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) 및 [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9911d-151">For more information about PowerShell background jobs, see [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) and [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="9911d-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9911d-152">-ComputerName</span></span>

<span data-ttu-id="9911d-153">중지할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-153">Specifies the computers to stop.</span></span> <span data-ttu-id="9911d-154">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-154">The default is the local computer.</span></span>

<span data-ttu-id="9911d-155">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-155">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="9911d-156">로컬 컴퓨터를 지정 하려면 컴퓨터 이름 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-156">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="9911d-157">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-157">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="9911d-158">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-158">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="9911d-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9911d-159">-Confirm</span></span>

<span data-ttu-id="9911d-160">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9911d-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="9911d-161">-Credential</span></span>

<span data-ttu-id="9911d-162">이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-162">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="9911d-163">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-163">The default is the current user.</span></span>

<span data-ttu-id="9911d-164">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="9911d-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9911d-165">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-165">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="9911d-166">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9911d-167">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="9911d-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="9911d-168">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="9911d-168">-DcomAuthentication</span></span>

<span data-ttu-id="9911d-169">이 cmdlet이 WMI와 함께 사용 하는 인증 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-169">Specifies the authentication level that this cmdlet uses with WMI.</span></span> <span data-ttu-id="9911d-170">`Stop-Computer` WMI를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-170">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="9911d-171">기본값은 **Packet** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-171">The default value is **Packet**.</span></span>

<span data-ttu-id="9911d-172">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9911d-173">**기본값** : Windows 인증.</span><span class="sxs-lookup"><span data-stu-id="9911d-173">**Default** : Windows Authentication.</span></span>
- <span data-ttu-id="9911d-174">**None** : COM 인증을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-174">**None** : No COM authentication.</span></span>
- <span data-ttu-id="9911d-175">**연결** : 연결 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-175">**Connect** : Connect-level COM authentication.</span></span>
- <span data-ttu-id="9911d-176">**호출** : 호출 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-176">**Call** : Call-level COM authentication.</span></span>
- <span data-ttu-id="9911d-177">**패킷** : 패킷 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-177">**Packet** : Packet-level COM authentication.</span></span>
- <span data-ttu-id="9911d-178">**PacketIntegrity** : 패킷 무결성 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-178">**PacketIntegrity** : Packet Integrity-level COM authentication.</span></span>
- <span data-ttu-id="9911d-179">**PacketPrivacy** : 패킷 개인 정보 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-179">**PacketPrivacy** : Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="9911d-180">**변경 되지 않음** : 이전 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-180">**Unchanged** : Same as the previous command.</span></span>

<span data-ttu-id="9911d-181">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationlevel](/dotnet/api/system.management.authenticationlevel)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9911d-181">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9911d-182">-Force</span><span class="sxs-lookup"><span data-stu-id="9911d-182">-Force</span></span>

<span data-ttu-id="9911d-183">컴퓨터를 강제로 즉시 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-183">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="9911d-184">-가장</span><span class="sxs-lookup"><span data-stu-id="9911d-184">-Impersonation</span></span>

<span data-ttu-id="9911d-185">이 cmdlet이 WMI를 호출할 때 사용할 가장 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-185">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="9911d-186">기본값은 **Impersonate** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-186">The default value is **Impersonate**.</span></span>

<span data-ttu-id="9911d-187">`Stop-Computer` WMI를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-187">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="9911d-188">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-188">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9911d-189">**기본값** : 기본 가장.</span><span class="sxs-lookup"><span data-stu-id="9911d-189">**Default** : Default impersonation.</span></span>
- <span data-ttu-id="9911d-190">**Anonymous** : 호출자의 id를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-190">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="9911d-191">**식별** : 개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-191">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="9911d-192">**Impersonate** : 개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-192">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9911d-193">-Protocol</span><span class="sxs-lookup"><span data-stu-id="9911d-193">-Protocol</span></span>

<span data-ttu-id="9911d-194">컴퓨터를 다시 시작하는 데 사용할 프로토콜을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-194">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="9911d-195">이 매개 변수에 허용 되는 값은 **WSMan** 및 **DCOM** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-195">The acceptable values for this parameter are: **WSMan** and **DCOM**.</span></span> <span data-ttu-id="9911d-196">기본값은 **DCOM** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-196">The default value is **DCOM**.</span></span>

<span data-ttu-id="9911d-197">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-197">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9911d-198">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9911d-198">-ThrottleLimit</span></span>

<span data-ttu-id="9911d-199">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-199">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="9911d-200">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-200">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="9911d-201">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-201">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="9911d-202">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="9911d-202">-WsmanAuthentication</span></span>

<span data-ttu-id="9911d-203">이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-203">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="9911d-204">기본값은 **Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-204">The default value is **Default**.</span></span>

<span data-ttu-id="9911d-205">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9911d-206">Basic</span><span class="sxs-lookup"><span data-stu-id="9911d-206">Basic</span></span>
- <span data-ttu-id="9911d-207">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9911d-207">CredSSP</span></span>
- <span data-ttu-id="9911d-208">기본값</span><span class="sxs-lookup"><span data-stu-id="9911d-208">Default</span></span>
- <span data-ttu-id="9911d-209">다이제스트</span><span class="sxs-lookup"><span data-stu-id="9911d-209">Digest</span></span>
- <span data-ttu-id="9911d-210">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9911d-210">Kerberos</span></span>
- <span data-ttu-id="9911d-211">Negotiate</span><span class="sxs-lookup"><span data-stu-id="9911d-211">Negotiate.</span></span>

<span data-ttu-id="9911d-212">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9911d-212">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="9911d-213">사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-213">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="9911d-214">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-214">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="9911d-215">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-215">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="9911d-216">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9911d-217">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9911d-217">-WhatIf</span></span>

<span data-ttu-id="9911d-218">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-218">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9911d-219">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-219">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9911d-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9911d-220">CommonParameters</span></span>

<span data-ttu-id="9911d-221">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9911d-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9911d-222">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9911d-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9911d-223">입력</span><span class="sxs-lookup"><span data-stu-id="9911d-223">INPUTS</span></span>

### <span data-ttu-id="9911d-224">없음</span><span class="sxs-lookup"><span data-stu-id="9911d-224">None</span></span>

<span data-ttu-id="9911d-225">이 cmdlet에는 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-225">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9911d-226">출력</span><span class="sxs-lookup"><span data-stu-id="9911d-226">OUTPUTS</span></span>

### <span data-ttu-id="9911d-227">없음 또는 System.web. Remorerereor 작업</span><span class="sxs-lookup"><span data-stu-id="9911d-227">None or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="9911d-228">**AsJob** 매개 변수를 지정 하는 경우이 Cmdlet은 **system.object** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-228">The cmdlet returns a **System.Management.Automation.RemotingJob** object, if you specify the **AsJob** parameter.</span></span> <span data-ttu-id="9911d-229">그렇지 않으면 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-229">Otherwise, it doesn't generate any output.</span></span>

## <span data-ttu-id="9911d-230">참고</span><span class="sxs-lookup"><span data-stu-id="9911d-230">NOTES</span></span>

<span data-ttu-id="9911d-231">이 cmdlet은 **Win32_OperatingSystem** WMI 클래스의 **Win32Shutdown** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-231">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="9911d-232">이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9911d-232">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="9911d-233">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9911d-233">RELATED LINKS</span></span>

[<span data-ttu-id="9911d-234">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-234">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="9911d-235">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-235">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="9911d-236">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-236">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="9911d-237">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-237">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="9911d-238">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-238">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="9911d-239">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="9911d-239">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="9911d-240">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="9911d-240">Test-Connection</span></span>](Test-Connection.md)
