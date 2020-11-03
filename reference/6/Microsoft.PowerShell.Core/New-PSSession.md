---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 90bd1d539bb6bc071df6bfcf326adc57e24fff8f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218434"
---
# <span data-ttu-id="c3edf-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-103">New-PSSession</span></span>

## <span data-ttu-id="c3edf-104">개요</span><span class="sxs-lookup"><span data-stu-id="c3edf-104">SYNOPSIS</span></span>
<span data-ttu-id="c3edf-105">로컬 또는 원격 컴퓨터에 대한 영구 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="c3edf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3edf-106">SYNTAX</span></span>

### <span data-ttu-id="c3edf-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="c3edf-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-108">VMId</span><span class="sxs-lookup"><span data-stu-id="c3edf-108">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-109">URI</span><span class="sxs-lookup"><span data-stu-id="c3edf-109">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-110">VMName</span><span class="sxs-lookup"><span data-stu-id="c3edf-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-111">세션</span><span class="sxs-lookup"><span data-stu-id="c3edf-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="c3edf-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-113">SSHHost</span><span class="sxs-lookup"><span data-stu-id="c3edf-113">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="c3edf-114">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="c3edf-114">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="c3edf-115">설명</span><span class="sxs-lookup"><span data-stu-id="c3edf-115">DESCRIPTION</span></span>

<span data-ttu-id="c3edf-116">`New-PSSession`Cmdlet은 로컬 또는 원격 컴퓨터에 PowerShell 세션 ( **PSSession** )을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-116">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="c3edf-117">**PSSession** 을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-117">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="c3edf-118">**PSSession** 을 사용 하 여 함수 또는 변수 값과 같은 데이터를 공유 하는 여러 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-118">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="c3edf-119">**PSSession** 에서 명령을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-119">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="c3edf-120">**PSSession** 을 사용 하 여 원격 컴퓨터와 직접 상호 작용 하려면 cmdlet을 사용 `Enter-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-120">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="c3edf-121">자세한 내용은 [about_PSSessions](about/about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-121">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="c3edf-122">또는의 **ComputerName** 매개 변수를 사용 하 여 **PSSession** 을 만들지 않고 원격 컴퓨터에서 명령을 실행할 수 있습니다 `Enter-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-122">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="c3edf-123">**ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 명령에 사용 되는 임시 연결을 만든 다음 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-123">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="c3edf-124">PowerShell 6.0부터 ssh (Secure Shell)를 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 하 고 원격 컴퓨터에서 SSH를 사용할 수 있고 원격 컴퓨터가 PowerShell SSH 끝점으로 구성 된 경우 원격 컴퓨터에서 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="c3edf-125">SSH 기반 PowerShell 원격 세션의 혜택은 여러 플랫폼 (Windows, Linux, macOS)에서 작동할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-125">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="c3edf-126">SSH 기반 세션의 경우 **HostName** 또는 **SSHConnection** 매개 변수 집합을 사용 하 여 원격 컴퓨터 및 관련 연결 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-126">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="c3edf-127">PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="c3edf-128">서버 인증서를 신뢰할 수 없는 HTTPS 끝점을 사용 하 여 Linux 또는 macOS 클라이언트에서 WSMan 원격을 사용 하는 경우 (예: 자체 서명 된 인증서)</span><span class="sxs-lookup"><span data-stu-id="c3edf-128">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="c3edf-129">연결을 성공적으로 `PSSessionOption` `-SkipCACheck` 설정 하려면 및를 포함 하는를 제공 해야 합니다 `-SkipCNCheck` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-129">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="c3edf-130">서버 인증서와 대상 시스템에 대 한 네트워크 연결을 지정할 수 있는 환경에 있는 경우에만이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-130">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="c3edf-131">예제</span><span class="sxs-lookup"><span data-stu-id="c3edf-131">EXAMPLES</span></span>

### <span data-ttu-id="c3edf-132">예 1: 로컬 컴퓨터에서 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-132">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="c3edf-133">이 명령은 로컬 컴퓨터에 새 **pssession** 을 만든 다음 변수에 **pssession** 을 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-133">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="c3edf-134">이제이 **PSSession** 을 사용 하 여 로컬 컴퓨터에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-134">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="c3edf-135">예 2: 원격 컴퓨터에서 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-135">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="c3edf-136">이 명령은 Server01 컴퓨터에 새 **PSSession** 을 만든 다음 `$Server01` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-136">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="c3edf-137">여러 **PSSession** 개체를 만들 때 유용한 이름의 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-137">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="c3edf-138">이렇게 하면 이후 명령에서 **PSSession** 개체를 관리 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-138">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="c3edf-139">예 3: 여러 컴퓨터에서 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-139">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="c3edf-140">이 명령은 **ComputerName** 매개 변수로 지정 된 각 컴퓨터에 하나씩 세 개의 **PSSession** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-140">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="c3edf-141">이 명령은 대입 연산자 (=)를 사용 하 여 새 **PSSession** 개체를 변수에 할당 합니다. `$s1` , `$s2` , `$s3`</span><span class="sxs-lookup"><span data-stu-id="c3edf-141">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="c3edf-142">Server01 **pssession** 을에 할당 하 `$s1` 고, Server02 **Pssession** 을에 `$s2` , Server03 **pssession** 을에 할당 `$s3` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-142">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="c3edf-143">여러 개체를 일련의 변수에 할당 하면 PowerShell에서 각 개체를 계열의 변수에 각각 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-143">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="c3edf-144">변수보다 개체가 많은 경우에는 나머지 모든 개체가 마지막 변수에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-144">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="c3edf-145">개체보다 변수가 많은 경우에는 나머지 변수가 비어 있습니다(null).</span><span class="sxs-lookup"><span data-stu-id="c3edf-145">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="c3edf-146">예제 4: 지정 된 포트를 사용 하 여 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-146">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="c3edf-147">이 명령은 서버 포트 8081에 연결 되 고 SSL 프로토콜을 사용 하는 Server01 컴퓨터에 새 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-147">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="c3edf-148">새 **PSSession** 은 E12 라는 대체 세션 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-148">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="c3edf-149">포트를 설정하기 전에 포트 8081에서 수신 대기하도록 원격 컴퓨터의 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-149">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="c3edf-150">자세한 내용은 **Port** 매개 변수에 대 한 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-150">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="c3edf-151">예 5: 기존 세션을 기반으로 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-151">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="c3edf-152">이 명령은 기존 **pssession** 과 동일한 속성을 사용 하 여 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-152">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="c3edf-153">기존 **pssession** 의 리소스가 모두 소모 되 고 일부 수요를 오프 로드 하는 데 새 **pssession** 이 필요한 경우이 명령 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-153">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="c3edf-154">이 명령은의 **Session** 매개 변수를 사용 하 여 `New-PSSession` 변수에 저장 된 **PSSession** 을 지정 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-154">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="c3edf-155">Domain1\Admin01 사용자의 자격 증명이 이 명령을 완료하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-155">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="c3edf-156">예 6: 다른 도메인에서 전역 범위를 사용 하 여 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-156">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="c3edf-157">이 예제에서는 다른 도메인의 컴퓨터에 전역 범위를 사용 하 여 **PSSession** 을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-157">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="c3edf-158">기본적으로 명령줄에서 생성 된 **pssession** 개체는 로컬 범위를 사용 하 여 생성 되 고 스크립트에서 생성 된 **pssession** 개체에는 스크립트 범위가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-158">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="c3edf-159">전역 범위를 사용 하 여 **pssession** 을 만들려면 새 **pssession** 을 만든 다음 전역 범위로 캐스팅 되는 변수에 **pssession** 을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-159">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="c3edf-160">이 경우 `$s` 변수는 전역 범위로 캐스팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-160">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="c3edf-161">이 명령은 **ComputerName** 매개 변수를 사용하여 원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-161">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="c3edf-162">컴퓨터가 사용자 계정과 다른 도메인에 있기 때문에 컴퓨터의 전체 이름은 사용자의 자격 증명과 함께 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-162">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="c3edf-163">예 7: 많은 컴퓨터에 대 한 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-163">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="c3edf-164">이 명령은 Servers.txt 파일에 나열 된 각 200 컴퓨터에 **pssession** 을 만들고 결과 **pssession** 을 변수에 저장 합니다 `$rs` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-164">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="c3edf-165">**PSSession** 개체의 스로틀 제한은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-165">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="c3edf-166">컴퓨터의 이름이 데이터베이스, 스프레드시트, 텍스트 파일 또는 다른 텍스트 변환 가능 형식에 저장된 경우 이 명령 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-166">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="c3edf-167">예 8: URI를 사용 하 여 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-167">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="c3edf-168">이 명령은 Server01 컴퓨터에 **PSSession** 을 만들어 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-168">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="c3edf-169">**URI** 매개 변수를 사용 하 여 전송 프로토콜, 원격 컴퓨터, 포트 및 대체 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-169">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="c3edf-170">또한 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터에서 세션을 만들 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-170">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="c3edf-171">예 9: 세션 집합에서 백그라운드 작업 실행</span><span class="sxs-lookup"><span data-stu-id="c3edf-171">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="c3edf-172">이러한 명령은 **pssession** 개체 집합을 만든 다음 각 **pssession** 개체에서 백그라운드 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-172">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="c3edf-173">첫 번째 명령은 Servers.txt 파일에 나열 된 각 컴퓨터에 새 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-173">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="c3edf-174">Cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-174">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="c3edf-175">**ComputerName** 매개 변수 값은 cmdlet을 사용 하 여 `Get-Content` Servers.txt 파일의 컴퓨터 이름 목록을 가져오는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-175">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="c3edf-176">이 명령은 **Credential** 매개 변수를 사용 하 여 도메인 관리자의 권한이 있는 **PSSession** 개체를 만들고 **ThrottleLimit** 매개 변수를 사용 하 여 명령을 동시 연결 16 개로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-176">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="c3edf-177">이 명령은 **PSSession** 개체를 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-177">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="c3edf-178">두 번째 명령은 cmdlet의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` `Get-Process PowerShell` 의 각 **PSSession** 개체에서 명령을 실행 하는 백그라운드 작업을 시작 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-178">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="c3edf-179">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](About/about_Jobs.md) 및 [about_Remote_Jobs](About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-179">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="c3edf-180">예 10: 해당 URI를 사용 하 여 컴퓨터에 대 한 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-180">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="c3edf-181">이 명령은 컴퓨터 이름이 아닌 URI로 지정 된 컴퓨터에 연결 하는 **PSSession** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-181">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="c3edf-182">예 11: 세션 옵션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-182">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="c3edf-183">이 예에서는 세션 옵션 개체를 만들고 **sessionoption** 매개 변수를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-183">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="c3edf-184">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSessionOption` 세션 옵션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-184">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="c3edf-185">결과 **Sessionoption** 개체를 `$so` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-185">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="c3edf-186">두 번째 명령은 새 세션의 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-186">The second command uses the option in a new session.</span></span> <span data-ttu-id="c3edf-187">이 명령은 cmdlet을 사용 하 여 `New-PSSession` 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-187">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="c3edf-188">SessionOption 매개 변수 값은 변수의 **sessionoption** 개체입니다 `$so` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-188">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="c3edf-189">예 12: SSH를 사용 하 여 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-189">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="c3edf-190">이 예제에서는 Secure Shell (SSH)를 사용 하 여 새 **PSSession** 을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-190">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="c3edf-191">SSH가 원격 컴퓨터에서 암호를 묻는 메시지를 표시 하도록 구성 된 경우 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-191">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="c3edf-192">그렇지 않은 경우에는 SSH 키 기반 사용자 인증을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-192">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="c3edf-193">예 13: SSH를 사용 하 여 세션을 만들고 포트 및 사용자 인증 키 지정</span><span class="sxs-lookup"><span data-stu-id="c3edf-193">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="c3edf-194">이 예제에서는 Secure Shell (SSH)를 사용 하 여 **PSSession** 을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-194">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="c3edf-195">**Port** 매개 변수를 사용 하 여 사용할 포트를 지정 하 고 **keyfilepath** 매개 변수를 사용 하 여 원격 컴퓨터에서 사용자를 식별 하 고 인증 하는 데 사용 되는 RSA 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-195">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="c3edf-196">예제 14: SSH를 사용 하 여 여러 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="c3edf-196">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="c3edf-197">이 예에서는 Secure Shell (SSH) 및 **SSHConnection** 매개 변수 집합을 사용 하 여 여러 세션을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-197">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="c3edf-198">**SSHConnection** 매개 변수는 각 세션에 대 한 연결 정보를 포함 하는 해시 테이블의 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-198">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="c3edf-199">이 예제에서는 대상 원격 컴퓨터에 키 기반 사용자 인증을 지원 하도록 구성 된 SSH가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-199">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="c3edf-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3edf-200">PARAMETERS</span></span>

### <span data-ttu-id="c3edf-201">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="c3edf-201">-AllowRedirection</span></span>

<span data-ttu-id="c3edf-202">이 cmdlet이이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-202">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="c3edf-203">**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-203">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="c3edf-204">기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-204">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="c3edf-205">또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-205">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="c3edf-206">Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 **$PSSessionOption** 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-206">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="c3edf-207">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-207">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-208">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="c3edf-208">-ApplicationName</span></span>

<span data-ttu-id="c3edf-209">연결 URI의 애플리케이션 이름 세그먼트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-209">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="c3edf-210">명령에서 **ConnectionURI**  매개 변수를 사용하지 않는 경우 이 매개 변수를 사용하여 응용 프로그램 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-210">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="c3edf-211">기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-211">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="c3edf-212">이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-212">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="c3edf-213">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-213">This value is appropriate for most uses.</span></span> <span data-ttu-id="c3edf-214">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-214">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c3edf-215">WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-215">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="c3edf-216">이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-216">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-217">-인증</span><span class="sxs-lookup"><span data-stu-id="c3edf-217">-Authentication</span></span>

<span data-ttu-id="c3edf-218">사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-218">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="c3edf-219">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-219">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3edf-220">기본값</span><span class="sxs-lookup"><span data-stu-id="c3edf-220">Default</span></span>
- <span data-ttu-id="c3edf-221">Basic</span><span class="sxs-lookup"><span data-stu-id="c3edf-221">Basic</span></span>
- <span data-ttu-id="c3edf-222">Credssp</span><span class="sxs-lookup"><span data-stu-id="c3edf-222">Credssp</span></span>
- <span data-ttu-id="c3edf-223">다이제스트</span><span class="sxs-lookup"><span data-stu-id="c3edf-223">Digest</span></span>
- <span data-ttu-id="c3edf-224">Kerberos</span><span class="sxs-lookup"><span data-stu-id="c3edf-224">Kerberos</span></span>
- <span data-ttu-id="c3edf-225">Negotiate</span><span class="sxs-lookup"><span data-stu-id="c3edf-225">Negotiate</span></span>
- <span data-ttu-id="c3edf-226">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="c3edf-226">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="c3edf-227">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-227">The default value is Default.</span></span>

<span data-ttu-id="c3edf-228">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-228">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="c3edf-229">사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스 (예: 원격 네트워크 공유 액세스)에 대 한 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-229">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c3edf-230">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-230">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c3edf-231">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-231">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-232">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="c3edf-232">-CertificateThumbprint</span></span>

<span data-ttu-id="c3edf-233">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-233">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="c3edf-234">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-234">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c3edf-235">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-235">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c3edf-236">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-236">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="c3edf-237">인증서를 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-237">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-238">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c3edf-238">-ComputerName</span></span>

<span data-ttu-id="c3edf-239">컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-239">Specifies an array of names of computers.</span></span> <span data-ttu-id="c3edf-240">이 cmdlet은 지정 된 컴퓨터에 대 한 영구 연결 ( **PSSession** )을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-240">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="c3edf-241">여러 컴퓨터 이름을 입력 하면에서 `New-PSSession` 각 컴퓨터에 대해 하나씩 여러 **PSSession** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-241">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="c3edf-242">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-242">The default is the local computer.</span></span>

<span data-ttu-id="c3edf-243">하나 이상의 원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-243">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="c3edf-244">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-244">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="c3edf-245">컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-245">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="c3edf-246">컴퓨터 이름을 따옴표로 파이프 할 수도 있습니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-246">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="c3edf-247">**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-247">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="c3edf-248">또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-248">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="c3edf-249">TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c3edf-249">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="c3edf-250">**ComputerName** 매개 변수 값에 로컬 컴퓨터를 포함 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-250">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-251">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c3edf-251">-ConfigurationName</span></span>

<span data-ttu-id="c3edf-252">새 **PSSession** 에 사용 되는 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-252">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="c3edf-253">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-253">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="c3edf-254">구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-254">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="c3edf-255">세션의 세션 구성은 원격 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-255">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="c3edf-256">지정된 세션 구성이 원격 컴퓨터에 없으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-256">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="c3edf-257">기본값은 `$PSSessionConfigurationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-257">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="c3edf-258">이 기본 설정 변수를 설정하지 않으면 Microsoft.PowerShell이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-258">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="c3edf-259">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-259">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-260">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="c3edf-260">-ConnectionUri</span></span>

<span data-ttu-id="c3edf-261">세션에 대 한 연결 끝점을 정의 하는 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-261">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="c3edf-262">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-262">The URI must be fully qualified.</span></span> <span data-ttu-id="c3edf-263">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-263">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="c3edf-264">기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-264">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="c3edf-265">**ConnectionURI** 를 지정하지 않은 경우 **UseSSL** , **ComputerName** , **Port** 및 **ApplicationName** 매개 변수를 사용하여 **ConnectionURI** 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-265">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="c3edf-266">URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-266">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="c3edf-267">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-267">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="c3edf-268">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-268">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="c3edf-269">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-269">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-270">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="c3edf-270">-ContainerId</span></span>

<span data-ttu-id="c3edf-271">컨테이너의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-271">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="c3edf-272">이 cmdlet은 지정 된 각 컨테이너와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-272">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="c3edf-273">명령을 사용 `docker ps` 하 여 컨테이너 id 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-273">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="c3edf-274">자세한 내용은 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 명령에 대 한 도움말을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-274">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-275">-Credential</span><span class="sxs-lookup"><span data-stu-id="c3edf-275">-Credential</span></span>

<span data-ttu-id="c3edf-276">이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-276">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="c3edf-277">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-277">The default is the current user.</span></span>

<span data-ttu-id="c3edf-278">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-278">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c3edf-279">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-279">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="c3edf-280">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-280">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c3edf-281">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="c3edf-281">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-282">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="c3edf-282">-EnableNetworkAccess</span></span>

<span data-ttu-id="c3edf-283">이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-283">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="c3edf-284">대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-284">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="c3edf-285">예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-285">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="c3edf-286">루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-286">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="c3edf-287">루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 해당 값을 점 (.), localhost 또는 로컬 컴퓨터 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-287">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="c3edf-288">기본적으로이 cmdlet은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 루프백 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-288">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="c3edf-289">**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-289">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="c3edf-290">원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-290">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="c3edf-291">또한 세션 자격 증명을 다른 컴퓨터에 위임 하는 **인증** 매개 변수의 CredSSP 값을 사용 하 여 루프백 세션에서 원격 액세스를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-291">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="c3edf-292">악의적인 액세스 로부터 컴퓨터를 보호 하기 위해 **EnableNetworkAccess** 매개 변수를 사용 하 여 만든 대화형 토큰을 포함 하는 분리 된 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-292">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="c3edf-293">CredSSP 인증을 사용하는 연결이 끊어진 세션은 다른 컴퓨터에서 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-293">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="c3edf-294">자세한 내용은 `Disconnect-PSSession`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-294">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="c3edf-295">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-295">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-296">-HostName</span><span class="sxs-lookup"><span data-stu-id="c3edf-296">-HostName</span></span>

<span data-ttu-id="c3edf-297">Secure Shell (SSH) 기반 연결에 대 한 컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-297">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="c3edf-298">이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 ComputerName 매개 변수와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-298">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="c3edf-299">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-299">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-300">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="c3edf-300">-KeyFilePath</span></span>

<span data-ttu-id="c3edf-301">SSH (Secure Shell)에서 원격 컴퓨터의 사용자를 인증 하는 데 사용 하는 키 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-301">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="c3edf-302">SSH를 사용 하면 기본 암호 인증 대신 개인/공개 키를 통해 사용자 인증을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-302">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="c3edf-303">키 인증을 사용 하도록 원격 컴퓨터를 구성 하는 경우이 매개 변수를 사용 하 여 사용자를 식별 하는 키를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-303">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="c3edf-304">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-304">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-305">-Name</span><span class="sxs-lookup"><span data-stu-id="c3edf-305">-Name</span></span>

<span data-ttu-id="c3edf-306">**PSSession** 의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-306">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="c3edf-307">및 등의 다른 cmdlet을 사용 하는 경우 이름을 사용 하 여 **PSSession** 을 참조할 수 `Get-PSSession` 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-307">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="c3edf-308">이 이름은 컴퓨터나 현재 세션에서 고유하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-308">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-309">-Port</span><span class="sxs-lookup"><span data-stu-id="c3edf-309">-Port</span></span>

<span data-ttu-id="c3edf-310">이 명령에 사용되는 원격 컴퓨터의 네트워크 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-310">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="c3edf-311">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-311">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="c3edf-312">기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-312">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="c3edf-313">다른 포트를 사용 하기 전에 해당 포트에서 수신 대기 하도록 원격 컴퓨터의 WinRM 수신기를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-313">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="c3edf-314">다음 명령을 사용하여 수신기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-314">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="c3edf-315">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-315">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="c3edf-316">명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-316">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="c3edf-317">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-317">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-318">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="c3edf-318">-RunAsAdministrator</span></span>

<span data-ttu-id="c3edf-319">**PSSession** 이 관리자 권한으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-319">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-320">-Session</span><span class="sxs-lookup"><span data-stu-id="c3edf-320">-Session</span></span>

<span data-ttu-id="c3edf-321">이 cmdlet이 새 **pssession** 의 모델로 사용 하는 **PSSession** 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-321">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="c3edf-322">이 매개 변수는 지정 된 **pssession** 개체와 동일한 속성을 가진 새 **pssession** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-322">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="c3edf-323">**Pssession** 개체를 포함 하는 변수를 입력 하거나 **pssession** 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 합니다 `New-PSSession` `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-323">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="c3edf-324">결과로 생성 된 **PSSession** 개체의 컴퓨터 이름, 응용 프로그램 이름, 연결 URI, 포트, 구성 이름, 제한 한도 및 SSL(SECURE SOCKETS LAYER) (SSL) 값이 원본과 동일 하지만 표시 이름, ID 및 인스턴스 ID (GUID)는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-324">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-325">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="c3edf-325">-SessionOption</span></span>

<span data-ttu-id="c3edf-326">세션에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-326">Specifies advanced options for the session.</span></span> <span data-ttu-id="c3edf-327">Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-327">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="c3edf-328">옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-328">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="c3edf-329">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-329">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="c3edf-330">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-330">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="c3edf-331">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-331">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="c3edf-332">기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-332">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="c3edf-333">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-333">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="c3edf-334">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-334">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-335">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="c3edf-335">-SSHConnection</span></span>

<span data-ttu-id="c3edf-336">이 매개 변수는 해시 테이블의 배열을 사용 합니다. 여기서 각 해시 테이블에는 SSH (Secure Shell) 연결을 설정 하는 데 필요한 하나 이상의 연결 매개 변수가 포함 되어 있습니다 (호스트 이름, 포트, 사용자 이름, KeyFilePath).</span><span class="sxs-lookup"><span data-stu-id="c3edf-336">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="c3edf-337">Hashtable 연결 매개 변수는 **HostName** 매개 변수 집합에 대해 정의 된 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-337">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="c3edf-338">**SSHConnection** 매개 변수는 각 세션에 다른 연결 정보가 필요한 여러 세션을 만드는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-338">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="c3edf-339">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-340">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="c3edf-340">-SSHTransport</span></span>

<span data-ttu-id="c3edf-341">SSH (Secure Shell)를 사용 하 여 원격 연결을 설정 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-341">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="c3edf-342">기본적으로 PowerShell은 Windows WinRM을 사용 하 여 원격 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-342">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="c3edf-343">이 스위치를 사용 하면 PowerShell에서 호스트 이름 매개 변수 집합을 사용 하 여 SSH 기반 원격 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-343">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="c3edf-344">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-344">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-345">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c3edf-345">-ThrottleLimit</span></span>

<span data-ttu-id="c3edf-346">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-346">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="c3edf-347">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-347">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="c3edf-348">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-348">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-349">-UserName</span><span class="sxs-lookup"><span data-stu-id="c3edf-349">-UserName</span></span>

<span data-ttu-id="c3edf-350">원격 컴퓨터에서 세션을 만드는 데 사용 되는 계정의 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-350">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="c3edf-351">사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-351">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="c3edf-352">SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-352">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="c3edf-353">키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로를 KeyFilePath 매개 변수를 통해 제공할 수 있으며 암호 프롬프트가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-353">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="c3edf-354">클라이언트 사용자 키 파일이 SSH 알려진 위치에 있는 경우 키 기반 인증에는 KeyFilePath 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-354">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="c3edf-355">자세한 내용은 키 기반 사용자 인증에 대 한 SSH 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-355">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="c3edf-356">필수 매개 변수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-356">This is not a required parameter.</span></span> <span data-ttu-id="c3edf-357">UserName 매개 변수를 지정 하지 않으면 현재 로그온 사용자 이름이 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-357">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="c3edf-358">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-358">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-359">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="c3edf-359">-UseSSL</span></span>

<span data-ttu-id="c3edf-360">이 cmdlet이 SSL 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-360">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="c3edf-361">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-361">By default, SSL is not used.</span></span>

<span data-ttu-id="c3edf-362">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-362">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="c3edf-363">**UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-363">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="c3edf-364">이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-364">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="c3edf-365">-VMId</span><span class="sxs-lookup"><span data-stu-id="c3edf-365">-VMId</span></span>

<span data-ttu-id="c3edf-366">가상 컴퓨터의 ID 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-366">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="c3edf-367">이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-367">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="c3edf-368">사용할 수 있는 가상 컴퓨터를 보려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-368">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-369">-VMName</span><span class="sxs-lookup"><span data-stu-id="c3edf-369">-VMName</span></span>

<span data-ttu-id="c3edf-370">가상 컴퓨터의 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-370">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="c3edf-371">이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-371">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="c3edf-372">사용할 수 있는 가상 컴퓨터를 확인 하려면 cmdlet을 사용 합니다 `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-372">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-373">-HostName</span><span class="sxs-lookup"><span data-stu-id="c3edf-373">-HostName</span></span>

<span data-ttu-id="c3edf-374">Secure Shell (SSH) 기반 연결에 대 한 컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-374">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="c3edf-375">이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 ComputerName 매개 변수와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-375">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>
<span data-ttu-id="c3edf-376">이 매개 변수는 형식을 사용 하 여 호스트 이름 매개 변수 값의 일부로 사용자 이름 및/또는 포트를 지정 하도록 지원 합니다 `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-376">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span>
<span data-ttu-id="c3edf-377">호스트 이름의 일부로 지정 된 사용자 이름 및/또는 포트가 `-UserName` 지정 된 경우 및 매개 변수 보다 우선적으로 적용 `-Port` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-377">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span>
<span data-ttu-id="c3edf-378">이를 통해 특정 사용자 이름 및/또는 포트를 포함 하는 여러 컴퓨터 이름을이 매개 변수에 전달할 수 있으며, 다른 사용자 이름 및/또는 포트는 `-UserName` 및 매개 변수에서 사용할 수 있습니다 `-Port` .</span><span class="sxs-lookup"><span data-stu-id="c3edf-378">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="c3edf-379">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-379">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: HostName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-380">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="c3edf-380">-KeyFilePath</span></span>

<span data-ttu-id="c3edf-381">SSH (Secure Shell)에서 원격 컴퓨터의 사용자를 인증 하는 데 사용 하는 키 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-381">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="c3edf-382">SSH를 사용 하면 기본 암호 인증 대신 개인/공개 키를 통해 사용자 인증을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-382">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="c3edf-383">키 인증을 사용 하도록 원격 컴퓨터를 구성 하는 경우이 매개 변수를 사용 하 여 사용자를 식별 하는 키를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-383">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="c3edf-384">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-384">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-385">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="c3edf-385">-SSHTransport</span></span>

<span data-ttu-id="c3edf-386">SSH (Secure Shell)를 사용 하 여 원격 연결을 설정 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-386">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="c3edf-387">기본적으로 PowerShell은 Windows WinRM을 사용 하 여 원격 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-387">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="c3edf-388">이 스위치를 사용 하면 PowerShell에서 호스트 이름 매개 변수 집합을 사용 하 여 SSH 기반 원격 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-388">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="c3edf-389">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-389">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-390">-UserName</span><span class="sxs-lookup"><span data-stu-id="c3edf-390">-UserName</span></span>

<span data-ttu-id="c3edf-391">원격 컴퓨터에서 세션을 만드는 데 사용 되는 계정의 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-391">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="c3edf-392">사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-392">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="c3edf-393">SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-393">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="c3edf-394">키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로를 KeyFilePath 매개 변수를 통해 제공할 수 있으며 암호 프롬프트가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-394">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="c3edf-395">클라이언트 사용자 키 파일이 SSH 알려진 위치에 있는 경우 키 기반 인증에는 KeyFilePath 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-395">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="c3edf-396">자세한 내용은 키 기반 사용자 인증에 대 한 SSH 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-396">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="c3edf-397">필수 매개 변수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-397">This is not a required parameter.</span></span> <span data-ttu-id="c3edf-398">UserName 매개 변수를 지정 하지 않으면 현재 로그온 사용자 이름이 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-398">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="c3edf-399">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-399">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-400">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="c3edf-400">-SSHConnection</span></span>

<span data-ttu-id="c3edf-401">이 매개 변수는 해시 테이블의 배열을 사용 합니다. 여기서 각 해시 테이블에는 SSH (Secure Shell) 연결을 설정 하는 데 필요한 연결 매개 변수 (호스트 이름, 포트, 사용자 이름, KeyFilePath, 하위 시스템)가 하나 이상 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-401">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath, Subsystem).</span></span>

<span data-ttu-id="c3edf-402">Hashtable 연결 매개 변수는 **HostName** 매개 변수 집합에 대해 정의 된 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-402">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>
<span data-ttu-id="c3edf-403">해시 테이블의 키 순서에 따라 마지막으로 지정 된 연결에 사용 되는 사용자 이름과 포트가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-403">Note that the order of the keys in the hashtable result in user name and port being used for the connection where the last one specified is used.</span></span>  <span data-ttu-id="c3edf-404">예를 들어를 사용 하는 경우 `@{UserName="first";HostName="second@host"}` 사용자 이름이 `second` 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-404">For example, if you use `@{UserName="first";HostName="second@host"}`, then the user name `second` will be used.</span></span>  <span data-ttu-id="c3edf-405">그러나를 사용 하 `@{HostName="second@host:22";Port=23}` 는 경우에는 포트 23이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-405">However, if you use `@{HostName="second@host:22";Port=23}`, then port 23 will be used.</span></span>

<span data-ttu-id="c3edf-406">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-406">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="c3edf-407">**SSHConnection** 매개 변수는 각 세션에 다른 연결 정보가 필요한 여러 세션을 만드는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-407">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

```yaml
Type: hashtable
Parameter Sets: SSHConnection
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-408">-하위 시스템</span><span class="sxs-lookup"><span data-stu-id="c3edf-408">-Subsystem</span></span>

<span data-ttu-id="c3edf-409">새 **PSSession** 에 사용 되는 SSH 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-409">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="c3edf-410">이는 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-410">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="c3edf-411">하위 시스템은 미리 정의 된 매개 변수를 사용 하 여 특정 버전의 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-411">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="c3edf-412">지정 된 하위 시스템이 원격 컴퓨터에 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-412">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="c3edf-413">이 매개 변수를 사용 하지 않는 경우 기본값은 ' powershell ' 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-413">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3edf-414">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3edf-414">CommonParameters</span></span>

<span data-ttu-id="c3edf-415">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3edf-415">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3edf-416">자세한 내용은 about_CommonParameters(https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-416">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3edf-417">입력</span><span class="sxs-lookup"><span data-stu-id="c3edf-417">INPUTS</span></span>

### <span data-ttu-id="c3edf-418">System.string, SYSTEM.URI, Runspace. n a m a.</span><span class="sxs-lookup"><span data-stu-id="c3edf-418">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="c3edf-419">문자열, URI 또는 세션 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-419">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="c3edf-420">출력</span><span class="sxs-lookup"><span data-stu-id="c3edf-420">OUTPUTS</span></span>

### <span data-ttu-id="c3edf-421">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-421">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="c3edf-422">참고</span><span class="sxs-lookup"><span data-stu-id="c3edf-422">NOTES</span></span>

- <span data-ttu-id="c3edf-423">이 cmdlet은 PowerShell 원격 인프라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-423">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="c3edf-424">이 cmdlet을 사용 하려면 PowerShell 원격을 사용 하도록 로컬 컴퓨터와 모든 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-424">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="c3edf-425">자세한 내용은 [about_Remote_Requirements](About/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-425">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="c3edf-426">로컬 컴퓨터에서 **PSSession** 을 만들려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-426">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="c3edf-427">**Pssession** 을 마친 후에는 cmdlet을 사용 `Remove-PSSession` 하 여 **pssession** 을 삭제 하 고 해당 리소스를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-427">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="c3edf-428">**HostName** 및 **SSHConnection** 매개 변수 집합은 PowerShell 6.0부터 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-428">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="c3edf-429">Secure Shell (SSH)를 기반으로 PowerShell 원격 기능을 제공 하기 위해 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-429">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="c3edf-430">SSH와 PowerShell은 여러 플랫폼 (Windows, Linux, macOS)에서 지원 되며 powershell 원격은 PowerShell 및 SSH가 설치 되 고 구성 되는 이러한 플랫폼에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-430">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="c3edf-431">이는 WinRM을 기반으로 하는 이전 Windows 전용 원격 시스템과 별개 이며, 대부분의 WinRM 특정 기능 및 제한 사항이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-431">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="c3edf-432">예를 들어 WinRM 기반 할당량, 세션 옵션, 사용자 지정 끝점 구성 및 연결 끊기/다시 연결 기능은 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3edf-432">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="c3edf-433">PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3edf-433">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="c3edf-434">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c3edf-434">RELATED LINKS</span></span>

[<span data-ttu-id="c3edf-435">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-435">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="c3edf-436">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-436">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="c3edf-437">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-437">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="c3edf-438">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-438">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="c3edf-439">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-439">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="c3edf-440">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c3edf-440">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="c3edf-441">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-441">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="c3edf-442">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3edf-442">Remove-PSSession</span></span>](Remove-PSSession.md)
