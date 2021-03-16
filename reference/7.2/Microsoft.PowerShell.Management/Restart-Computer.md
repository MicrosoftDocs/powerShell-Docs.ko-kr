---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 0e6df859a19f2281cc835b725fbc52c232042e56
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605234"
---
# <span data-ttu-id="6010e-102">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="6010e-102">Restart-Computer</span></span>

## <span data-ttu-id="6010e-103">개요</span><span class="sxs-lookup"><span data-stu-id="6010e-103">SYNOPSIS</span></span>
<span data-ttu-id="6010e-104">로컬 및 원격 컴퓨터에서 운영 체제를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-104">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="6010e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6010e-105">SYNTAX</span></span>

### <span data-ttu-id="6010e-106">DefaultSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="6010e-106">DefaultSet (Default)</span></span>

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6010e-107">설명</span><span class="sxs-lookup"><span data-stu-id="6010e-107">DESCRIPTION</span></span>

<span data-ttu-id="6010e-108">`Restart-Computer`Cmdlet은 로컬 및 원격 컴퓨터에서 운영 체제를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-108">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="6010e-109">의 매개 변수를 사용 하 여 `Restart-Computer` 다시 시작 작업을 실행 하 고, 인증 수준 및 대체 자격 증명을 지정 하 고, 동시에 실행 되는 작업을 제한 하 고, 강제로 즉시 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-109">You can use the parameters of `Restart-Computer` to run the restart operations, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="6010e-110">Windows PowerShell 3.0부터 다음 명령을 실행 하기 전에 다시 시작이 완료 될 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-110">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="6010e-111">대기 시간 제한 및 쿼리 간격을 지정 하 고, 다시 시작 된 컴퓨터에서 특정 서비스를 사용할 수 있을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-111">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="6010e-112">이 기능을 사용 하면 `Restart-Computer` 스크립트 및 함수에서 효과적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-112">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

## <span data-ttu-id="6010e-113">예제</span><span class="sxs-lookup"><span data-stu-id="6010e-113">EXAMPLES</span></span>

### <span data-ttu-id="6010e-114">예 1: 로컬 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6010e-114">Example 1: Restart the local computer</span></span>

<span data-ttu-id="6010e-115">`Restart-Computer` 로컬 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-115">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="6010e-116">예 2: 여러 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6010e-116">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="6010e-117">`Restart-Computer` 원격 컴퓨터와 로컬 컴퓨터를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-117">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="6010e-118">**ComputerName** 매개 변수는 컴퓨터 이름 배열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-118">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="6010e-119">예제 3: 텍스트 파일에서 컴퓨터 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="6010e-119">Example 3: Get computer names from a text file</span></span>

<span data-ttu-id="6010e-120">`Restart-Computer` 텍스트 파일에서 컴퓨터 이름 목록을 가져오고 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-120">`Restart-Computer` gets a list of computer names from a text file and restarts the computers.</span></span> <span data-ttu-id="6010e-121">**ComputerName** 매개 변수가 지정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-121">The **ComputerName** parameter isn't specified.</span></span> <span data-ttu-id="6010e-122">하지만이 매개 변수는 첫 번째 위치 매개 변수 이기 때문에 파이프라인으로 전송 되는 텍스트 파일의 컴퓨터 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-122">But because it's the first position parameter, it accepts the computer names from the text file that are sent down the pipeline.</span></span>

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

<span data-ttu-id="6010e-123">`Get-Content` 는 **Path** 매개 변수를 사용 하 여 텍스트 파일에서 컴퓨터 이름 목록을 가져올 **Domain01.txt** 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-123">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="6010e-124">컴퓨터 이름이 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-124">The computer names are sent down the pipeline.</span></span> <span data-ttu-id="6010e-125">`Restart-Computer` 각 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-125">`Restart-Computer` restarts each computer.</span></span>

### <span data-ttu-id="6010e-126">예제 4: 텍스트 파일에 나열 된 컴퓨터를 강제로 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6010e-126">Example 4: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="6010e-127">이 예제에서는 파일에 나열 된 컴퓨터를 강제로 즉시 다시 시작 `Domain01.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-127">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="6010e-128">텍스트 파일의 컴퓨터 이름은 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-128">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="6010e-129">**Force** 매개 변수는 강제로 즉시 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-129">The **Force** parameter forces an immediate restart.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

<span data-ttu-id="6010e-130">`Get-Content` 는 **Path** 매개 변수를 사용 하 여 텍스트 파일에서 컴퓨터 이름 목록을 가져올 **Domain01.txt** 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-130">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="6010e-131">컴퓨터 이름은 변수에 저장 됩니다 `$Names` .</span><span class="sxs-lookup"><span data-stu-id="6010e-131">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="6010e-132">`Get-Credential` 사용자 이름과 암호를 묻는 메시지를 표시 하 고 해당 값을 변수에 저장 `$Creds` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-132">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="6010e-133">`Restart-Computer` 는 해당 변수와 함께 **ComputerName** 및 **Credential** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-133">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="6010e-134">**Force** 매개 변수를 설정 하면 각 컴퓨터를 즉시 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-134">The **Force** parameter causes an immediate restart of each computer.</span></span>

### <span data-ttu-id="6010e-135">예 6: 원격 컴퓨터를 다시 시작 하 고 PowerShell 대기</span><span class="sxs-lookup"><span data-stu-id="6010e-135">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="6010e-136">`Restart-Computer` 는 원격 컴퓨터를 다시 시작 하 고, 계속 하기 전에 다시 시작 된 컴퓨터에서 PowerShell을 사용할 수 있게 될 때까지 최대 5 분 (300 초) 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-136">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="6010e-137">`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-137">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="6010e-138">**Wait** 매개 변수는 다시 시작이 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-138">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="6010e-139">**의** 은 PowerShell에서 원격 컴퓨터의 명령을 실행할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-139">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="6010e-140">**Timeout** 매개 변수는 5 분 대기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-140">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="6010e-141">**Delay** 매개 변수는 2 초 마다 원격 컴퓨터를 쿼리하여 다시 시작할지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-141">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="6010e-142">예 7: WsmanAuthentication를 사용 하 여 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6010e-142">Example 7: Restart a computer by using WsmanAuthentication</span></span>

<span data-ttu-id="6010e-143">`Restart-Computer`**WsmanAuthentication** 메커니즘을 사용 하 여 원격 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-143">`Restart-Computer` restarts the remote computer using the **WsmanAuthentication** mechanism.</span></span>
<span data-ttu-id="6010e-144">Kerberos 인증 현재 사용자에 게 원격 컴퓨터를 다시 시작할 수 있는 권한이 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-144">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span> <span data-ttu-id="6010e-145">자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6010e-145">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

<span data-ttu-id="6010e-146">`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-146">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="6010e-147">**WsmanAuthentication** 매개 변수는 인증 방법을 **Kerberos** 로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-147">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="6010e-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6010e-148">PARAMETERS</span></span>

### <span data-ttu-id="6010e-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6010e-149">-ComputerName</span></span>

<span data-ttu-id="6010e-150">컴퓨터 이름 하나 또는 쉼표로 구분 된 컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-150">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="6010e-151">`Restart-Computer` 파이프라인 또는 변수의 **ComputerName** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-151">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="6010e-152">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="6010e-152">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="6010e-153">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 또는 localhost를 입력 합니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="6010e-153">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="6010e-154">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-154">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="6010e-155">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-155">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="6010e-156">**ComputerName** 매개 변수를 지정 하지 않으면에서 `Restart-Computer` 로컬 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-156">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6010e-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="6010e-157">-Credential</span></span>

<span data-ttu-id="6010e-158">이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-158">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="6010e-159">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-159">The default is the current user.</span></span>

<span data-ttu-id="6010e-160">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="6010e-160">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6010e-161">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-161">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="6010e-162">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6010e-163">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="6010e-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="6010e-164">-Delay</span><span class="sxs-lookup"><span data-stu-id="6010e-164">-Delay</span></span>

<span data-ttu-id="6010e-165">쿼리의 빈도 (초)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-165">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="6010e-166">PowerShell은 **For** 매개 변수로 지정 된 서비스를 쿼리하여 컴퓨터를 다시 시작한 후 서비스를 사용할 수 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-166">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="6010e-167">이 매개 변수는 **Wait** 및 **For** 매개 변수와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-167">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="6010e-168">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-168">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="6010e-169">**Delay** 매개 변수를 지정 하지 않으면에서 `Restart-Computer` 5 초 지연 시간을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-169">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6010e-170">-의 경우</span><span class="sxs-lookup"><span data-stu-id="6010e-170">-For</span></span>

<span data-ttu-id="6010e-171">컴퓨터를 다시 시작한 후 지정 된 서비스 또는 기능을 사용할 수 있을 때까지 기다리는 PowerShell의 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-171">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="6010e-172">이 매개 변수는 **Wait** 매개 변수에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-172">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="6010e-173">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6010e-174">**기본값**: PowerShell이 다시 시작 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-174">**Default**: Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="6010e-175">**Powershell**: 컴퓨터의 powershell 원격 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-175">**PowerShell**: Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="6010e-176">**WMI**: 컴퓨터에 대 한 Win32_ComputerSystem 쿼리에 대 한 응답을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-176">**WMI**: Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="6010e-177">**WinRM**: ws-management를 사용 하 여 컴퓨터에 대 한 원격 세션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-177">**WinRM**: Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="6010e-178">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6010e-179">-Force</span><span class="sxs-lookup"><span data-stu-id="6010e-179">-Force</span></span>

<span data-ttu-id="6010e-180">컴퓨터를 강제로 즉시 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-180">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6010e-181">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="6010e-181">-Timeout</span></span>

<span data-ttu-id="6010e-182">대기 기간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-182">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="6010e-183">시간이 경과할 때 컴퓨터를 `Restart-Computer` 다시 시작 하지 않아도 명령 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-183">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="6010e-184">**Timeout** 매개 변수는 **Wait** 매개 변수에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-184">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="6010e-185">**Timeout** 은 **대기** 매개 변수의 무한 대기 기간을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-185">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="6010e-186">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-186">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6010e-187">-Wait</span><span class="sxs-lookup"><span data-stu-id="6010e-187">-Wait</span></span>

<span data-ttu-id="6010e-188">`Restart-Computer` PowerShell 프롬프트를 표시 하지 않고 컴퓨터가 다시 시작 될 때까지 파이프라인을 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-188">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="6010e-189">스크립트에서이 매개 변수를 사용 하 여 컴퓨터를 다시 시작한 다음 다시 시작이 완료 되 면 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-189">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="6010e-190">**Wait** 매개 변수는 컴퓨터를 다시 시작할 때까지 무기한 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-190">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="6010e-191">**시간 제한** 을 사용 하 여 타이밍을 조정 하 고 **For** 및 **Delay** 매개 변수를 사용 하 여 다시 시작 된 컴퓨터에서 특정 서비스를 사용할 수 있을 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-191">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="6010e-192">로컬 컴퓨터를 다시 시작 하는 경우에는 **Wait** 매개 변수가 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-192">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="6010e-193">**ComputerName** 매개 변수 값에 원격 컴퓨터와 로컬 컴퓨터의 이름이 포함 된 경우에서 `Restart-Computer` 로컬 컴퓨터의 **대기** 에 대 한 종료 되지 않는 오류를 생성 하지만 원격 컴퓨터를 다시 시작할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-193">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="6010e-194">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6010e-195">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="6010e-195">-WsmanAuthentication</span></span>

<span data-ttu-id="6010e-196">사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-196">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="6010e-197">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="6010e-198">이 매개 변수에 허용 되는 값은 **Basic**, **CredSSP**, **Default**, **Digest**, **Kerberos** 및 **Negotiate** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-198">The acceptable values for this parameter are: **Basic**, **CredSSP**, **Default**, **Digest**, **Kerberos**, and **Negotiate**.</span></span>

<span data-ttu-id="6010e-199">자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6010e-199">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="6010e-200">사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-200">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="6010e-201">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="6010e-202">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6010e-203">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6010e-203">-Confirm</span></span>

<span data-ttu-id="6010e-204">실행 하기 전에 확인 메시지를 표시 `Restart-Computer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-204">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="6010e-205">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6010e-205">-WhatIf</span></span>

<span data-ttu-id="6010e-206">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="6010e-206">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="6010e-207">`Restart-Computer`Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-207">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="6010e-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6010e-208">CommonParameters</span></span>

<span data-ttu-id="6010e-209">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6010e-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6010e-210">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6010e-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6010e-211">입력</span><span class="sxs-lookup"><span data-stu-id="6010e-211">INPUTS</span></span>

### <span data-ttu-id="6010e-212">System.String</span><span class="sxs-lookup"><span data-stu-id="6010e-212">System.String</span></span>

<span data-ttu-id="6010e-213">`Restart-Computer` 파이프라인 또는 변수의 컴퓨터 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-213">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

## <span data-ttu-id="6010e-214">출력</span><span class="sxs-lookup"><span data-stu-id="6010e-214">OUTPUTS</span></span>

### <span data-ttu-id="6010e-215">없음</span><span class="sxs-lookup"><span data-stu-id="6010e-215">None</span></span>

<span data-ttu-id="6010e-216">`Restart-Computer` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-216">`Restart-Computer` doesn't generate any output.</span></span>

## <span data-ttu-id="6010e-217">참고</span><span class="sxs-lookup"><span data-stu-id="6010e-217">NOTES</span></span>

- <span data-ttu-id="6010e-218">Windows에서는 `Restart-Computer` WMI(Windows Management Instrumentation) (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) 클래스의 [Win32Shutdown 메서드](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-218">In Windows, `Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span> <span data-ttu-id="6010e-219">이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-219">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>
- <span data-ttu-id="6010e-220">Linux 및 Mac OS에서는 `Restart-Computer` `/sbin/shutdown` bash 도구를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6010e-220">On Linux and Mac OS, `Restart-Computer` uses the `/sbin/shutdown` bash tool.</span></span>

## <span data-ttu-id="6010e-221">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6010e-221">RELATED LINKS</span></span>

[<span data-ttu-id="6010e-222">Windows 원격 관리 정보</span><span class="sxs-lookup"><span data-stu-id="6010e-222">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="6010e-223">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="6010e-223">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="6010e-224">WS-Management 프로토콜</span><span class="sxs-lookup"><span data-stu-id="6010e-224">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)