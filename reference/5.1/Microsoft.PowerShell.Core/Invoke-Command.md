---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: 652ff321ea1c6507915be9748715604166207200
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218234"
---
# <span data-ttu-id="9ed47-103">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="9ed47-103">Invoke-Command</span></span>

## <span data-ttu-id="9ed47-104">개요</span><span class="sxs-lookup"><span data-stu-id="9ed47-104">SYNOPSIS</span></span>
<span data-ttu-id="9ed47-105">로컬 및 원격 컴퓨터에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-105">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="9ed47-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9ed47-106">SYNTAX</span></span>

### <span data-ttu-id="9ed47-107">InProcess (기본값)</span><span class="sxs-lookup"><span data-stu-id="9ed47-107">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="9ed47-108">세션</span><span class="sxs-lookup"><span data-stu-id="9ed47-108">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="9ed47-109">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="9ed47-109">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="9ed47-110">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="9ed47-110">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="9ed47-111">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="9ed47-111">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="9ed47-112">URI</span><span class="sxs-lookup"><span data-stu-id="9ed47-112">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="9ed47-113">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="9ed47-113">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="9ed47-114">VMId</span><span class="sxs-lookup"><span data-stu-id="9ed47-114">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="9ed47-115">VMName</span><span class="sxs-lookup"><span data-stu-id="9ed47-115">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="9ed47-116">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="9ed47-116">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="9ed47-117">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="9ed47-117">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="9ed47-118">ContainerId</span><span class="sxs-lookup"><span data-stu-id="9ed47-118">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="9ed47-119">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="9ed47-119">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

## <span data-ttu-id="9ed47-120">설명</span><span class="sxs-lookup"><span data-stu-id="9ed47-120">DESCRIPTION</span></span>

<span data-ttu-id="9ed47-121">`Invoke-Command`Cmdlet은 로컬 또는 원격 컴퓨터에서 명령을 실행 하 고 오류를 포함 하 여 명령에서 모든 출력을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-121">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="9ed47-122">단일 명령을 사용 하 여 `Invoke-Command` 여러 컴퓨터에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-122">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="9ed47-123">원격 컴퓨터에서 명령 중 하나를 실행하려면 **ComputerName** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-123">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="9ed47-124">데이터를 공유 하는 일련의 관련 명령을 실행 하려면 cmdlet을 사용 하 여 `New-PSSession` 원격 컴퓨터에서 **pssession** (영구 연결)을 만든 다음의 **Session** 매개 변수를 사용 하 여 `Invoke-Command` **pssession** 에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-124">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession**.</span></span> <span data-ttu-id="9ed47-125">연결이 끊긴 세션에서 명령을 실행하려면 **InDisconnectedSession** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-125">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="9ed47-126">백그라운드 작업에서 명령을 실행하려면 **AsJob** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-126">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="9ed47-127">`Invoke-Command`로컬 컴퓨터에서 스크립트 블록에 명령으로를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-127">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="9ed47-128">PowerShell은 현재 범위의 자식 범위에서 즉시 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-128">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="9ed47-129">를 사용 하 여 `Invoke-Command` 원격 컴퓨터에서 명령을 실행 하기 전에 [about_Remote](./About/about_Remote.md)을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-129">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="9ed47-130">일부 코드 샘플에서는 스 플랫를 사용 하 여 줄 길이를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-130">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="9ed47-131">자세한 내용은 [about_Splatting](./About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-131">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="9ed47-132">예제</span><span class="sxs-lookup"><span data-stu-id="9ed47-132">EXAMPLES</span></span>

### <span data-ttu-id="9ed47-133">예제 1: 서버에서 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-133">Example 1: Run a script on a server</span></span>

<span data-ttu-id="9ed47-134">이 예에서는 `Test.ps1` Server01 컴퓨터에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-134">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="9ed47-135">**FilePath** 매개 변수는 로컬 컴퓨터에 있는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-135">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="9ed47-136">원격 컴퓨터에서 스크립트가 실행되고 그 결과가 로컬 컴퓨터로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-136">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="9ed47-137">예 2: 원격 서버에서 명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-137">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="9ed47-138">이 예제에서는 `Get-Culture` Server01 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-138">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="9ed47-139">**ComputerName** 매개 변수는 원격 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-139">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="9ed47-140">**Credential** 매개 변수는 명령을 실행할 권한이 있는 사용자 인 Domain01\User01의 보안 컨텍스트에서 명령을 실행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-140">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="9ed47-141">**ScriptBlock** 매개 변수는 원격 컴퓨터에서 실행할 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-141">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="9ed47-142">이에 대 한 응답으로 PowerShell은 User01 계정에 대 한 암호와 인증 방법을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-142">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="9ed47-143">Server01 컴퓨터에서 이 명령을 실행하고 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-143">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="9ed47-144">예제 3: 영구 연결에서 명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-144">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="9ed47-145">이 예에서는 `Get-Culture` Server02 이라는 원격 컴퓨터에서 영구 연결을 사용 하 여 세션에서 동일한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-145">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="9ed47-146">`New-PSSession`Cmdlet은 Server02 원격 컴퓨터에서 세션을 만들어 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-146">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="9ed47-147">일반적으로 원격 컴퓨터에서 일련의 명령을 실행 하는 경우에만 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-147">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="9ed47-148">`Invoke-Command`Cmdlet은 `Get-Culture` Server02에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-148">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="9ed47-149">**Session** 매개 변수는 변수에 저장 된 세션을 지정 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-149">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="9ed47-150">이에 대 한 응답으로 PowerShell은 Server02 컴퓨터의 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-150">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="9ed47-151">예제 4: 세션을 사용 하 여 데이터를 공유 하는 일련의 명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-151">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="9ed47-152">이 예에서는의 **ComputerName** 및 **Session** 매개 변수를 사용한 결과를 비교 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-152">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="9ed47-153">세션을 사용하여 동일한 데이터를 공유하는 일련의 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-153">It shows how to use a session to run a series of commands that share the same data.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

<span data-ttu-id="9ed47-154">처음 두 명령은의 **ComputerName** 매개 변수를 사용 `Invoke-Command` 하 여 Server02 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-154">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="9ed47-155">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 원격 컴퓨터의 PowerShell 프로세스를 가져온 다음 변수에 저장 합니다 `$p` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-155">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="9ed47-156">두 번째 명령은 PowerShell 프로세스의 **VirtualMemorySize** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-156">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="9ed47-157">**ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 명령을 실행할 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-157">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="9ed47-158">명령이 완료 되 면 세션이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-158">The session is closed when the command completes.</span></span> <span data-ttu-id="9ed47-159">`$p`변수가 하나의 연결에서 만들어졌지만 두 번째 명령을 위해 만들어진 연결에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-159">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="9ed47-160">이 문제는 원격 컴퓨터에서 영구 세션을 만든 다음 동일한 세션에서 두 명령을 실행 하 여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-160">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="9ed47-161">`New-PSSession`Cmdlet은 컴퓨터 Server02에 영구 세션을 만들고이 세션을 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-161">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="9ed47-162">`Invoke-Command`다음 줄은 **session** 매개 변수를 사용 하 여 동일한 세션에서 두 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-162">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="9ed47-163">두 명령이 모두 동일한 세션에서 실행 되므로 값은 `$p` 활성 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-163">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="9ed47-164">예 5: 지역 변수에 저장 된 명령 입력</span><span class="sxs-lookup"><span data-stu-id="9ed47-164">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="9ed47-165">이 예에서는 지역 변수에 스크립트 블록으로 저장 된 명령을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-165">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="9ed47-166">스크립트 블록을 지역 변수에 저장 하는 경우 변수를 **ScriptBlock** 매개 변수 값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-166">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-EventLog -LogName "Windows PowerShell" |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="9ed47-167">`$command`변수는 `Get-EventLog` 스크립트 블록으로 형식이 지정 된 명령을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-167">The `$command` variable stores the `Get-EventLog` command that's formatted as a script block.</span></span> <span data-ttu-id="9ed47-168">는 `Invoke-Command` `$command` S1 및 S2 원격 컴퓨터의에 저장 된 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-168">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="9ed47-169">예제 6: 여러 컴퓨터에서 단일 명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-169">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="9ed47-170">이 예제에서는를 사용 하 여 `Invoke-Command` 여러 컴퓨터에서 단일 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-170">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-EventLog "Windows PowerShell" }
}
Invoke-Command @parameters
```

<span data-ttu-id="9ed47-171">**ComputerName** 매개 변수는 쉼표로 구분 된 컴퓨터 이름 목록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-171">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="9ed47-172">컴퓨터 목록에는 로컬 컴퓨터를 나타내는 localhost 값이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-172">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="9ed47-173">**ConfigurationName** 매개 변수는 대체 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-173">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="9ed47-174">**ScriptBlock** 매개 변수는 `Get-EventLog` 를 실행 하 여 각 컴퓨터에서 Windows PowerShell 이벤트 로그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-174">The **ScriptBlock** parameter runs `Get-EventLog` to get the Windows PowerShell event logs from each computer.</span></span>

### <span data-ttu-id="9ed47-175">예 7: 여러 컴퓨터에서 호스트 프로그램의 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="9ed47-175">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="9ed47-176">이 예제에서는 200 원격 컴퓨터에서 실행 되는 PowerShell 호스트 프로그램의 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-176">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="9ed47-177">하나의 명령만 실행 되므로 각 컴퓨터에 대 한 영구 연결을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-177">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="9ed47-178">대신 이 명령은 **ComputerName** 매개 변수를 사용하여 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-178">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="9ed47-179">컴퓨터를 지정 하기 위해 cmdlet을 사용 하 여 `Get-Content` 컴퓨터 이름 파일의 Machine.txt 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-179">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="9ed47-180">`Invoke-Command`Cmdlet은 `Get-Host` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-180">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="9ed47-181">점 표기법을 사용 하 여 PowerShell 호스트의 **Version** 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-181">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="9ed47-182">이러한 명령은 한 번에 하나씩 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-182">These commands run one at a time.</span></span> <span data-ttu-id="9ed47-183">명령이 완료 되 면 모든 컴퓨터의 명령 출력이 변수에 저장 됩니다 `$version` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-183">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="9ed47-184">출력에는 데이터가 제공된 컴퓨터의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-184">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="9ed47-185">예 8: 여러 원격 컴퓨터에서 백그라운드 작업 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-185">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="9ed47-186">이 예제에서는 두 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-186">This example runs a command on two remote computers.</span></span> <span data-ttu-id="9ed47-187">`Invoke-Command`이 명령은 **AsJob** 매개 변수를 사용 하 여 명령이 백그라운드 작업으로 실행 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-187">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="9ed47-188">명령은 원격 컴퓨터에서 실행 되지만 작업은 로컬 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-188">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="9ed47-189">결과는 로컬 컴퓨터에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-189">The results are transmitted to the local computer.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

<span data-ttu-id="9ed47-190">`New-PSSession`Cmdlet은 Server01 및 Server02 원격 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-190">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="9ed47-191">`Invoke-Command`Cmdlet은 각 세션에서 백그라운드 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-191">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="9ed47-192">이 명령은 **AsJob** 매개 변수를 사용하여 백그라운드 작업으로 명령을 실행하며,</span><span class="sxs-lookup"><span data-stu-id="9ed47-192">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="9ed47-193">이 명령은 두 원격 컴퓨터에서 실행되는 각 작업에 해당하는 두 하위 작업 개체가 포함된 작업 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-193">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="9ed47-194">이 `Get-Job` 명령은 작업 개체를 `$j` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-194">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="9ed47-195">`$j`그런 다음 변수를 cmdlet으로 파이프 하 여 `Format-List` 작업 개체의 모든 속성을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-195">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="9ed47-196">마지막 명령은 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-196">The last command gets the results of the jobs.</span></span> <span data-ttu-id="9ed47-197">에서 작업 개체를 `$j` cmdlet으로 파이프 하 `Receive-Job` 고 결과를 `$results` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-197">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="9ed47-198">예 9: 원격 컴퓨터에서 실행 되는 명령에 로컬 변수 포함</span><span class="sxs-lookup"><span data-stu-id="9ed47-198">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="9ed47-199">이 예제에서는 원격 컴퓨터에서 실행되는 명령에 로컬 변수 값을 포함하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-199">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="9ed47-200">이 명령은 scope 한정자를 사용 하 여 `Using` 원격 명령에서 지역 변수를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-200">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="9ed47-201">기본적으로 모든 변수는 원격 세션에서 정의된다고 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-201">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="9ed47-202">`Using`범위 한정자는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-202">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9ed47-203">범위 한정자에 대 한 자세한 내용은 `Using` [about_Remote_Variables](./About/about_Remote_Variables.md) 및 [about_Scopes](./about/about_scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-203">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "Windows PowerShell"
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-EventLog -LogName $Using:Log -Newest 10 }
```

<span data-ttu-id="9ed47-204">`$Log`변수는 Windows PowerShell 이벤트 로그의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-204">The `$Log` variable stores the name of the event log, Windows PowerShell.</span></span> <span data-ttu-id="9ed47-205">이 `Invoke-Command` cmdlet은 `Get-EventLog` Server01에서 실행 되어 이벤트 로그에서 10 개의 최신 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-205">The `Invoke-Command` cmdlet runs `Get-EventLog` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="9ed47-206">**LogName** 매개 변수 값은 변수 이며이는 `$Log` `Using` 범위 한정자가 원격 세션이 아닌 로컬 세션에서 생성 되었음을 나타내는 범위 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-206">The value of the **LogName** parameter is the `$Log` variable, which is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="9ed47-207">예 10: 컴퓨터 이름 숨기기</span><span class="sxs-lookup"><span data-stu-id="9ed47-207">Example 10: Hide the computer name</span></span>

<span data-ttu-id="9ed47-208">이 예에서는의 **HideComputerName** 매개 변수를 사용한 결과를 보여 줍니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-208">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="9ed47-209">**HideComputerName** 는이 cmdlet이 반환 하는 개체를 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-209">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="9ed47-210">표시만 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-210">It changes only the display.</span></span> <span data-ttu-id="9ed47-211">여전히 **Format** cmdlet을 사용 하 여 영향을 받는 개체의 **PsComputerName** 속성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-211">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

<span data-ttu-id="9ed47-212">처음 두 명령은를 사용 `Invoke-Command` 하 여 `Get-Process` PowerShell 프로세스에 대 한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-212">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="9ed47-213">첫 번째 명령의 출력에는 명령이 실행된 컴퓨터의 이름을 포함하는 **PsComputerName** 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-213">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="9ed47-214">**HideComputerName** 를 사용 하는 두 번째 명령의 출력에는 **PsComputerName** 열이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-214">The output of the second command, which uses **HideComputerName** , doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="9ed47-215">예 11: 스크립트 블록에서 Param 키워드 사용</span><span class="sxs-lookup"><span data-stu-id="9ed47-215">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="9ed47-216">`Param`키워드 및 **argumentlist** 매개 변수는 스크립트 블록의 명명 된 매개 변수에 변수 값을 전달 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-216">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="9ed47-217">이 예에서는 문자로 시작 하 `a` 고 확장을 포함 하는 파일 이름을 표시 합니다 `.pdf` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-217">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="9ed47-218">키워드에 대 한 자세한 내용은 `Param` [about_Language_Keywords](./about/about_language_keywords.md#param)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-218">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

<span data-ttu-id="9ed47-219">`Invoke-Command` 및의 두 변수를 정의 하는 **ScriptBlock** 매개 변수를 사용 `$param1` `$param2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-219">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="9ed47-220">`Get-ChildItem` 명명 된 매개 변수, **이름** 및 변수 이름을 **포함** 하는을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-220">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="9ed47-221">**Argumentlist** 는 변수에 값을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-221">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="9ed47-222">예 12: 스크립트 블록에서 $args 자동 변수 사용</span><span class="sxs-lookup"><span data-stu-id="9ed47-222">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="9ed47-223">`$args`자동 변수 및 **argumentlist** 매개 변수는 스크립트 블록의 매개 변수 위치에 배열 값을 전달 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-223">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="9ed47-224">이 예제에서는 서버의 디렉터리 콘텐츠를 표시 `.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-224">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="9ed47-225">`Get-ChildItem` **Path** 매개 변수는 position 0이 고 **필터** 매개 변수는 position입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-225">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="9ed47-226">변수에 대 한 자세한 내용은 `$args` 을 참조 하십시오 [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="9ed47-226">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

<span data-ttu-id="9ed47-227">`Invoke-Command`**ScriptBlock** 매개 변수를 사용 하 고 `Get-ChildItem` `$args[0]` 및 `$args[1]` 배열 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-227">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="9ed47-228">**Argumentlist** 는 `$args` `Get-ChildItem` **경로** 및 **필터** 에 대 한 매개 변수 위치에 배열 값을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-228">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter**.</span></span>

### <span data-ttu-id="9ed47-229">예제 13: 텍스트 파일에 나열 된 모든 컴퓨터에서 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-229">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="9ed47-230">이 예제에서는 cmdlet을 사용 하 여 `Invoke-Command` `Sample.ps1` 파일에 나열 된 모든 컴퓨터에서 스크립트를 실행 합니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-230">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="9ed47-231">이 명령은 **FilePath** 매개 변수를 사용하여 스크립트 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-231">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="9ed47-232">이 명령을 사용 하면 원격 컴퓨터에서 스크립트 파일에 액세스할 수 없는 경우에도 원격 컴퓨터에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-232">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="9ed47-233">명령을 제출할 때 파일의 내용이 `Sample.ps1` 스크립트 블록으로 복사 되 고 스크립트 블록이 각 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-233">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="9ed47-234">이 절차는 **ScriptBlock** 매개 변수를 사용하여 스크립트 내용을 제출하는 작업과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-234">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="9ed47-235">예제 14: URI를 사용 하 여 원격 컴퓨터에서 명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ed47-235">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="9ed47-236">이 예제에서는 URI (Uniform Resource Identifier)로 식별 되는 원격 컴퓨터에서 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-236">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="9ed47-237">이 특정 예제에서는 `Set-Mailbox` 원격 Exchange 서버에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-237">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

<span data-ttu-id="9ed47-238">첫 번째 줄에서는 cmdlet을 사용 하 여 `Get-Credential` Windows LIVE ID 자격 증명을 변수에 저장 합니다 `$LiveCred` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-238">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="9ed47-239">PowerShell에서 사용자에 게 Windows Live ID 자격 증명을 입력 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-239">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="9ed47-240">`$parameters`변수는 cmdlet에 전달할 매개 변수를 포함 하는 해시 테이블입니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-240">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="9ed47-241">`Invoke-Command`Cmdlet은 `Set-Mailbox` **Microsoft. Exchange** 세션 구성을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-241">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="9ed47-242">**ConnectionURI** 매개 변수는 Exchange 서버 끝점의 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-242">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="9ed47-243">**Credential** 매개 변수는 변수에 저장 된 자격 증명을 지정 합니다 `$LiveCred` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-243">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="9ed47-244">**AuthenticationMechanism** 매개 변수는 기본 인증의 사용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-244">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="9ed47-245">**ScriptBlock** 매개 변수는 명령이 포함된 스크립트 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-245">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="9ed47-246">예 15: session 옵션 사용</span><span class="sxs-lookup"><span data-stu-id="9ed47-246">Example 15: Use a session option</span></span>

<span data-ttu-id="9ed47-247">이 예에서는 **Sessionoption** 매개 변수를 만들고 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-247">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="9ed47-248">`New-PSSessionOption`Cmdlet은 들어오는 HTTPS 연결을 평가 하는 동안 원격 끝에서 인증 기관, 정식 이름 및 해지 목록을 확인 하지 않도록 하는 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-248">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="9ed47-249">**Sessionoption** 개체는 변수에 저장 됩니다 `$so` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-249">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="9ed47-250">이러한 검사를 사용 하지 않도록 설정 하는 것은 문제 해결에 편리 하지만 안전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-250">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="9ed47-251">`Invoke-Command`Cmdlet은 `Get-HotFix` 명령을 원격으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-251">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="9ed47-252">**Sessionoption** 매개 변수에 변수가 지정 됩니다 `$so` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-252">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="9ed47-253">예 16: 원격 명령의 URI 리디렉션 관리</span><span class="sxs-lookup"><span data-stu-id="9ed47-253">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="9ed47-254">이 예제에서는 **Allowredirection** **sessionoption** 매개 변수를 사용 하 여 원격 명령에서 URI 리디렉션을 관리 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-254">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

<span data-ttu-id="9ed47-255">`New-PSSessionOption`Cmdlet은 변수에 저장 된 **Pssessionoption** 개체를 만듭니다 `$max` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-255">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="9ed47-256">이 명령은 **MaximumRedirection** 매개 변수를 사용하여 **PSSessionOption** 개체의 **MaximumConnectionRedirectionCount** 속성을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-256">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="9ed47-257">`Invoke-Command`Cmdlet은 `Get-Mailbox` 원격 Microsoft Exchange 서버에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-257">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="9ed47-258">**Allowredirection** 매개 변수는 대체 끝점에 대 한 연결을 리디렉션할 수 있는 명시적 권한을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-258">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="9ed47-259">**Sessionoption** 매개 변수는 변수에 저장 된 세션 개체를 사용 합니다 `$max` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-259">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="9ed47-260">결과적으로 **Connectionuri** 로 지정 된 원격 컴퓨터에서 리디렉션 메시지를 반환 하는 경우 PowerShell은 연결을 리디렉션하고, 새 대상이 다른 리디렉션 메시지를 반환 하는 경우 1의 리디렉션 수 값을 초과 하 여 `Invoke-Command` 종료 되지 않는 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-260">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="9ed47-261">예제 17: 원격 세션에서 네트워크 공유 액세스</span><span class="sxs-lookup"><span data-stu-id="9ed47-261">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="9ed47-262">이 예제에서는 원격 세션에서 네트워크 공유에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-262">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="9ed47-263">예제를 보여 주기 위해 세 대의 컴퓨터가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-263">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="9ed47-264">Server01는 로컬 컴퓨터이 고, Server02는 원격 컴퓨터 이며, Net03는 네트워크 공유를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-264">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="9ed47-265">Server01는 Server02에 연결 하 고, Server02는 Net03에 두 번째 홉을 사용 하 여 네트워크 공유에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-265">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="9ed47-266">PowerShell Remoting에서 컴퓨터 간 홉을 지 원하는 방법에 대 한 자세한 내용은 [Powershell 원격에서 두 번째 홉 만들기](/powershell/scripting/learn/remoting/ps-remoting-second-hop)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-266">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="9ed47-267">필요한 CredSSP (자격 증명 보안 지원 공급자) 위임은 로컬 컴퓨터의 클라이언트 설정과 원격 컴퓨터의 서비스 설정에서 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-267">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="9ed47-268">이 예의 명령을 실행 하려면 로컬 컴퓨터와 원격 컴퓨터에서 **Administrators** 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-268">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

<span data-ttu-id="9ed47-269">`Enable-WSManCredSSP`Cmdlet은 Server01 로컬 컴퓨터에서 Server02 원격 컴퓨터로 CredSSP 위임을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-269">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="9ed47-270">**Role** 매개 변수는 **클라이언트** 를 지정 하 여 로컬 컴퓨터에서 CredSSP 클라이언트 설정을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-270">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="9ed47-271">`New-PSSession` Server02에 대 한 **PSSession** 개체를 만들고 해당 개체를 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-271">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="9ed47-272">`Invoke-Command`이 cmdlet은 변수를 사용 하 여 `$s` 원격 컴퓨터 Server02에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-272">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="9ed47-273">**ScriptBlock** 매개 변수는 `Enable-WSManCredSSP` 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-273">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="9ed47-274">**Role** 매개 변수는 원격 컴퓨터에서 CredSSP 서버 설정을 구성 하는 **서버** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-274">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="9ed47-275">`$parameters`변수는 네트워크 공유에 연결 하기 위한 매개 변수 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-275">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="9ed47-276">`Invoke-Command`Cmdlet은 `Get-Item` 의 세션에서 명령을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-276">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="9ed47-277">이 명령은 네트워크 공유에서 스크립트를 가져옵니다 `\\Net03\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-277">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="9ed47-278">이 명령은 **CredSSP** 값을 가진 **Authentication** 매개 변수 및 값이 **Domain01\Admin01** 인 **Credential** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-278">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01**.</span></span>

### <span data-ttu-id="9ed47-279">예 18: 여러 원격 컴퓨터에서 스크립트 시작</span><span class="sxs-lookup"><span data-stu-id="9ed47-279">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="9ed47-280">이 예제에서는 100 대 이상의 컴퓨터에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-280">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="9ed47-281">로컬 컴퓨터에 대한 영향을 최소화하려면 각 컴퓨터에 연결하고 스크립트를 시작한 다음 각 컴퓨터에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-281">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="9ed47-282">이 스크립트는 연결이 끊어진 세션에서 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-282">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="9ed47-283">명령을 사용 하 여 `Invoke-Command` 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-283">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="9ed47-284">**ComputerName** 매개 변수 값은 `Get-Content` 텍스트 파일에서 원격 컴퓨터의 이름을 가져오는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-284">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="9ed47-285">**InDisconnectedSession** 매개 변수는 명령을 시작하는 즉시 세션의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-285">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="9ed47-286">**FilePath** 매개 변수 값은 `Invoke-Command` 각 컴퓨터에서 실행 되는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-286">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="9ed47-287">**Sessionoption** 값은 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-287">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="9ed47-288">**OutputBufferingMode** 값은 **Drop** 으로 설정 되 고 **IdleTimeout** 값은 **4320만** 밀리초 (12 시간)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-288">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="9ed47-289">연결 되지 않은 세션에서 실행 되는 명령 및 스크립트의 결과를 얻으려면 cmdlet을 사용 합니다 `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-289">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

## <span data-ttu-id="9ed47-290">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ed47-290">PARAMETERS</span></span>

### <span data-ttu-id="9ed47-291">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="9ed47-291">-AllowRedirection</span></span>

<span data-ttu-id="9ed47-292">이 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-292">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="9ed47-293">**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-293">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="9ed47-294">기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-294">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="9ed47-295">또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-295">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="9ed47-296">Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-296">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="9ed47-297">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-297">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-298">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="9ed47-298">-ApplicationName</span></span>

<span data-ttu-id="9ed47-299">연결 URI의 애플리케이션 이름 세그먼트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-299">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="9ed47-300">명령에 **Connectionuri** 매개 변수를 사용 하지 않는 경우이 매개 변수를 사용 하 여 응용 프로그램 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-300">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="9ed47-301">기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-301">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="9ed47-302">이 기본 설정 변수가 정의 되지 않은 경우 기본값은 WSMAN입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-302">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="9ed47-303">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-303">This value is appropriate for most uses.</span></span> <span data-ttu-id="9ed47-304">자세한 내용은 [about_Preference_Variables](./About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-304">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="9ed47-305">WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-305">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="9ed47-306">이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-306">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-307">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9ed47-307">-ArgumentList</span></span>

<span data-ttu-id="9ed47-308">명령에 있는 로컬 변수의 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-308">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="9ed47-309">명령에 있는 변수는 원격 컴퓨터에서 명령이 실행되기 전에 이 값으로 교체됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-309">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="9ed47-310">쉼표로 구분된 목록으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-310">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="9ed47-311">값은 나열 된 순서 대로 변수와 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-311">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="9ed47-312">**Argumentlist** 의 별칭은 Args입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-312">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="9ed47-313">**Argumentlist** 매개 변수의 값은 1024 같은 실제 값 이거나와 같은 지역 변수에 대 한 참조일 수 있습니다 `$max` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-313">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="9ed47-314">명령에서 로컬 변수를 사용하려면 다음 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-314">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="9ed47-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` 또는 `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="9ed47-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="9ed47-316">**Param** 키워드는 명령에 사용 되는 지역 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-316">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="9ed47-317">**Argumentlist** 는 나열 된 순서 대로 변수의 값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-317">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="9ed47-318">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-318">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-319">-AsJob</span><span class="sxs-lookup"><span data-stu-id="9ed47-319">-AsJob</span></span>

<span data-ttu-id="9ed47-320">이 cmdlet이 명령을 원격 컴퓨터에서 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-320">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="9ed47-321">이 매개 변수를 사용 하 여 완료 하는 데 오랜 시간이 걸리는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-321">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="9ed47-322">**AsJob** 매개 변수를 사용 하는 경우이 명령은 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-322">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="9ed47-323">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-323">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="9ed47-324">작업을 관리 하려면 cmdlet을 사용 `*-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-324">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="9ed47-325">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-325">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="9ed47-326">**AsJob** 매개 변수는 cmdlet을 사용 하 여 `Invoke-Command` cmdlet을 원격으로 실행 하는 것과 비슷합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-326">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="9ed47-327">그러나 **AsJob** 을 사용 하면 작업이 원격 컴퓨터에서 실행 되는 경우에도 로컬 컴퓨터에 작업이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-327">However, with **AsJob** , the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="9ed47-328">원격 작업의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-328">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="9ed47-329">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](About/about_Jobs.md) 및 [about_Remote_Jobs](About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-329">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-330">-인증</span><span class="sxs-lookup"><span data-stu-id="9ed47-330">-Authentication</span></span>

<span data-ttu-id="9ed47-331">사용자의 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-331">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="9ed47-332">CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-332">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="9ed47-333">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-333">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9ed47-334">기본값</span><span class="sxs-lookup"><span data-stu-id="9ed47-334">Default</span></span>
- <span data-ttu-id="9ed47-335">Basic</span><span class="sxs-lookup"><span data-stu-id="9ed47-335">Basic</span></span>
- <span data-ttu-id="9ed47-336">Credssp</span><span class="sxs-lookup"><span data-stu-id="9ed47-336">Credssp</span></span>
- <span data-ttu-id="9ed47-337">다이제스트</span><span class="sxs-lookup"><span data-stu-id="9ed47-337">Digest</span></span>
- <span data-ttu-id="9ed47-338">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9ed47-338">Kerberos</span></span>
- <span data-ttu-id="9ed47-339">Negotiate</span><span class="sxs-lookup"><span data-stu-id="9ed47-339">Negotiate</span></span>
- <span data-ttu-id="9ed47-340">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="9ed47-340">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="9ed47-341">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-341">The default value is Default.</span></span>

<span data-ttu-id="9ed47-342">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-342">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="9ed47-343">사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-343">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="9ed47-344">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-344">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="9ed47-345">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-345">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="9ed47-346">자세한 내용은 [자격 증명 보안 지원 공급자](/windows/win32/secauthn/credential-security-support-provider)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-346">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-347">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="9ed47-347">-CertificateThumbprint</span></span>

<span data-ttu-id="9ed47-348">연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-348">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="9ed47-349">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-349">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="9ed47-350">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-350">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="9ed47-351">로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-351">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="9ed47-352">인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-352">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="9ed47-353">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9ed47-353">-ComputerName</span></span>

<span data-ttu-id="9ed47-354">명령이 실행되는 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-354">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="9ed47-355">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-355">The default is the local computer.</span></span>

<span data-ttu-id="9ed47-356">**ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 지정 된 명령을 실행 하는 데만 사용 되 고 닫힌 임시 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-356">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="9ed47-357">영구 연결이 필요 하면 **Session** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-357">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="9ed47-358">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-358">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="9ed47-359">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 ()을 입력 `.` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-359">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="9ed47-360">**ComputerName** 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-360">To use an IP address in the value of **ComputerName** , the command must include the **Credential** parameter.</span></span> <span data-ttu-id="9ed47-361">컴퓨터를 HTTPS 전송에 대해 구성 하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM **TrustedHosts** 목록에 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-361">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="9ed47-362">**TrustedHosts** 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-362">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="9ed47-363">Windows Vista 이상 버전의 Windows 운영 체제에서 로컬 컴퓨터를 **ComputerName** 값에 포함 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-363">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName** , you must run PowerShell using the **Run as administrator** option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-364">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="9ed47-364">-ConfigurationName</span></span>

<span data-ttu-id="9ed47-365">새 **PSSession** 에 사용 되는 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-365">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="9ed47-366">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-366">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="9ed47-367">구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-367">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="9ed47-368">세션의 세션 구성은 원격 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-368">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="9ed47-369">지정 된 세션 구성이 원격 컴퓨터에 없으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-369">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="9ed47-370">기본값은 `$PSSessionConfigurationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-370">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="9ed47-371">이 기본 설정 변수가 설정 되지 않은 경우 기본값은 **Microsoft. PowerShell** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-371">If this preference variable isn't set, the default is **Microsoft.PowerShell**.</span></span> <span data-ttu-id="9ed47-372">자세한 내용은 [about_Preference_Variables](about/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-372">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-373">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="9ed47-373">-ConnectionUri</span></span>

<span data-ttu-id="9ed47-374">세션에 대한 연결 엔드포인트를 정의하는 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-374">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="9ed47-375">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-375">The URI must be fully qualified.</span></span>

<span data-ttu-id="9ed47-376">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-376">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="9ed47-377">기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-377">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="9ed47-378">연결 URI를 지정 하지 않으면 **UseSSL** 및 **Port** 매개 변수를 사용 하 여 연결 uri 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-378">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="9ed47-379">URI의 **Transport** 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-379">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="9ed47-380">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-380">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="9ed47-381">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-381">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="9ed47-382">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-382">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-383">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="9ed47-383">-ContainerId</span></span>

<span data-ttu-id="9ed47-384">컨테이너 Id의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-384">Specifies an array of container IDs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-385">-Credential</span><span class="sxs-lookup"><span data-stu-id="9ed47-385">-Credential</span></span>

<span data-ttu-id="9ed47-386">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-386">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="9ed47-387">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-387">The default is the current user.</span></span>

<span data-ttu-id="9ed47-388">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-388">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9ed47-389">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-389">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="9ed47-390">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-390">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9ed47-391">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="9ed47-391">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-392">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="9ed47-392">-EnableNetworkAccess</span></span>

<span data-ttu-id="9ed47-393">이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-393">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="9ed47-394">대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-394">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="9ed47-395">예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-395">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="9ed47-396">루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-396">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="9ed47-397">루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 해당 값을 점 ( `.` ), localhost 또는 로컬 컴퓨터 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-397">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="9ed47-398">기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-398">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="9ed47-399">**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-399">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="9ed47-400">원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-400">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="9ed47-401">세션 자격 증명을 다른 컴퓨터에 위임 하는 **인증** 매개 변수의 **CredSSP** 값을 사용 하 여 루프백 세션에서 원격 액세스를 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-401">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="9ed47-402">악의적인 액세스 로부터 컴퓨터를 보호 하기 위해 **EnableNetworkAccess** 를 사용 하 여 만든 대화형 토큰을 포함 하는 분리 된 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-402">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess** , can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="9ed47-403">CredSSP 인증을 사용하는 연결이 끊어진 세션은 다른 컴퓨터에서 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-403">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="9ed47-404">자세한 내용은 `Disconnect-PSSession`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-404">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="9ed47-405">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-405">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-406">-FilePath</span><span class="sxs-lookup"><span data-stu-id="9ed47-406">-FilePath</span></span>

<span data-ttu-id="9ed47-407">하나 이상의 원격 컴퓨터에서이 cmdlet이 실행 되는 로컬 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-407">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="9ed47-408">스크립트의 경로와 파일 이름을 입력 하거나에 대 한 스크립트 경로를 파이프 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-408">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="9ed47-409">스크립트는 로컬 컴퓨터 또는 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-409">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="9ed47-410">**Argumentlist** 를 사용 하 여 스크립트의 매개 변수 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-410">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="9ed47-411">이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 원격 컴퓨터로 전송한 다음 원격 컴퓨터에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-411">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-412">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="9ed47-412">-HideComputerName</span></span>

<span data-ttu-id="9ed47-413">이 cmdlet이 출력 표시에서 각 개체의 컴퓨터 이름을 생략 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-413">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="9ed47-414">기본적으로 개체를 생성한 컴퓨터의 이름은 화면에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-414">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="9ed47-415">이 매개 변수는 출력 표시에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-415">This parameter affects only the output display.</span></span> <span data-ttu-id="9ed47-416">개체를 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-416">It doesn't change the object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases: HCN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-417">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="9ed47-417">-InDisconnectedSession</span></span>

<span data-ttu-id="9ed47-418">이 cmdlet이 연결 되지 않은 세션에서 명령 또는 스크립트를 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-418">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="9ed47-419">**InDisconnectedSession** 매개 변수를 사용 하는 경우는 `Invoke-Command` 각 원격 컴퓨터에 영구 세션을 만들고, **ScriptBlock** 또는 **FilePath** 매개 변수로 지정 된 명령을 시작한 다음 세션에서 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-419">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="9ed47-420">명령은 연결 되지 않은 세션에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-420">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="9ed47-421">**InDisconnectedSession** 를 사용 하면 원격 세션에 대 한 연결을 유지 하지 않고 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-421">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="9ed47-422">결과를 반환 하기 전에 세션의 연결이 끊어져서 **InDisconnectedSession** 는 세션 간에 분할 되지 않고 다시 연결 된 세션에 모든 명령 결과가 반환 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-422">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="9ed47-423">**InDisconnectedSession** 은 **Session** 매개 변수 또는 **AsJob** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-423">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="9ed47-424">**InDisconnectedSession** 를 사용 하는 명령은 연결 되지 않은 세션을 나타내는 **PSSession** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-424">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="9ed47-425">명령 출력을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-425">They don't return the command output.</span></span> <span data-ttu-id="9ed47-426">연결이 끊어진 세션에 연결 하려면 `Connect-PSSession` 또는 cmdlet을 사용 `Receive-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-426">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="9ed47-427">세션에서 실행 된 명령의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-427">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="9ed47-428">연결 되지 않은 세션에서 출력을 생성 하는 명령을 실행 하려면 **OutputBufferingMode** 세션 옵션의 값을 **Drop** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-428">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop**.</span></span> <span data-ttu-id="9ed47-429">연결이 끊어진 세션에 연결 하려면 세션을 삭제 하기 전에 연결 하는 데 충분 한 시간을 제공 하도록 세션의 유휴 제한 시간을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-429">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="9ed47-430">**Sessionoption** 매개 변수 또는 기본 설정 변수에서 출력 버퍼링 모드 및 유휴 제한 시간을 설정할 수 있습니다 `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-430">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="9ed47-431">세션 옵션에 대 한 자세한 내용은 `New-PSSessionOption` 및 [about_Preference_Variables](./about/about_preference_variables.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-431">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="9ed47-432">연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-432">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="9ed47-433">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-433">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-434">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9ed47-434">-InputObject</span></span>

<span data-ttu-id="9ed47-435">명령에 대한 입력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-435">Specifies input to the command.</span></span> <span data-ttu-id="9ed47-436">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-436">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="9ed47-437">**InputObject** 매개 변수를 사용 하는 경우 `$Input` **ScriptBlock** 매개 변수 값의 자동 변수를 사용 하 여 입력 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-437">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-438">-JobName</span><span class="sxs-lookup"><span data-stu-id="9ed47-438">-JobName</span></span>

<span data-ttu-id="9ed47-439">백그라운드 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-439">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="9ed47-440">기본적으로 작업의 이름은 이며 `Job<n>` , 여기서 `<n>` 는 서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-440">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="9ed47-441">명령에서 **JobName** 매개 변수를 사용 하는 경우 명령 `Invoke-Command` 에 **AsJob** 를 포함 하지 않는 경우에도 명령이 작업으로 실행 되 고 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-441">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="9ed47-442">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-442">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-443">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="9ed47-443">-NoNewScope</span></span>

<span data-ttu-id="9ed47-444">이 cmdlet이 현재 범위의 지정 된 명령을 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-444">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="9ed47-445">기본적으로는 `Invoke-Command` 자체 범위에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-445">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="9ed47-446">이 매개 변수는 현재 세션에서 실행하는 명령 즉, **ComputerName** 및 **Session** 매개 변수를 모두 생략하는 명령에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-446">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="9ed47-447">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-447">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-448">-Port</span><span class="sxs-lookup"><span data-stu-id="9ed47-448">-Port</span></span>

<span data-ttu-id="9ed47-449">이 명령에 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-449">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="9ed47-450">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-450">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="9ed47-451">기본 포트는 5985 (HTTP의 경우 WinRM 포트) 및 5986 (HTTPS의 경우 WinRM 포트)입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-451">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="9ed47-452">대체 포트를 사용하기 전에 원격 컴퓨터가 해당 포트에서 수신하도록 원격 컴퓨터의 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-452">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="9ed47-453">수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-453">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="9ed47-454">반드시 필요한 경우가 아니면 **Port** 매개 변수를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-454">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="9ed47-455">이 명령에 설정된 포트는 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-455">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="9ed47-456">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-456">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-457">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="9ed47-457">-RunAsAdministrator</span></span>

<span data-ttu-id="9ed47-458">이 cmdlet이 명령을 관리자 권한으로 호출 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-458">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-459">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="9ed47-459">-ScriptBlock</span></span>

<span data-ttu-id="9ed47-460">실행할 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-460">Specifies the commands to run.</span></span> <span data-ttu-id="9ed47-461">명령을 중괄호로 묶어 `{ }` 스크립트 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-461">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="9ed47-462">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-462">This parameter is required.</span></span>

<span data-ttu-id="9ed47-463">기본적으로 명령에 있는 모든 변수는 원격 컴퓨터에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-463">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="9ed47-464">명령에 로컬 변수를 포함 하려면 **Argumentlist** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-464">To include local variables in the command, use **ArgumentList**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, ContainerId
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-465">-Session</span><span class="sxs-lookup"><span data-stu-id="9ed47-465">-Session</span></span>

<span data-ttu-id="9ed47-466">이 cmdlet이 명령을 실행 하는 세션의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-466">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="9ed47-467">**Pssession** 개체를 포함 하는 변수를 입력 하거나 **pssession** 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 합니다 `New-PSSession` `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-467">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="9ed47-468">**PSSession** 을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-468">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="9ed47-469">**PSSession** 을 사용 하 여 데이터를 공유 하는 일련의 관련 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-469">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="9ed47-470">단일 명령이 나 일련의 관련 되지 않은 명령을 실행 하려면 **ComputerName** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-470">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="9ed47-471">자세한 내용은 [about_PSSessions](./About/about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-471">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session, FilePathRunspace
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-472">-세션 이름</span><span class="sxs-lookup"><span data-stu-id="9ed47-472">-SessionName</span></span>

<span data-ttu-id="9ed47-473">연결이 끊긴 세션의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-473">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="9ed47-474">이 이름을 사용 하 여 명령 등의 후속 명령에서 세션을 참조할 수 있습니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-474">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="9ed47-475">이 매개 변수는 **InDisconnectedSession** 매개 변수와 함께 사용할 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-475">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="9ed47-476">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-476">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-477">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="9ed47-477">-SessionOption</span></span>

<span data-ttu-id="9ed47-478">세션에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-478">Specifies advanced options for the session.</span></span> <span data-ttu-id="9ed47-479">Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-479">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="9ed47-480">옵션의 기본값은 설정 된 경우 기본 설정 변수의 값에 따라 결정 됩니다 `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-480">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="9ed47-481">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-481">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="9ed47-482">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-482">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="9ed47-483">그러나 세션 구성에 설정 된 최대값, 할당량 또는 제한 보다 우선 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-483">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="9ed47-484">기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-484">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="9ed47-485">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-485">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="9ed47-486">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-486">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-487">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9ed47-487">-ThrottleLimit</span></span>

<span data-ttu-id="9ed47-488">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-488">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="9ed47-489">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-489">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="9ed47-490">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-490">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-491">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="9ed47-491">-UseSSL</span></span>

<span data-ttu-id="9ed47-492">이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-492">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="9ed47-493">기본적으로 SSL은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-493">By default, SSL isn't used.</span></span>

<span data-ttu-id="9ed47-494">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-494">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="9ed47-495">**UseSSL** 매개 변수는 HTTP 대신 HTTPS를 통해 데이터를 전송 하는 추가 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-495">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="9ed47-496">이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-496">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-497">-VMId</span><span class="sxs-lookup"><span data-stu-id="9ed47-497">-VMId</span></span>

<span data-ttu-id="9ed47-498">가상 컴퓨터의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-498">Specifies an array of IDs of virtual machines.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-499">-VMName</span><span class="sxs-lookup"><span data-stu-id="9ed47-499">-VMName</span></span>

<span data-ttu-id="9ed47-500">가상 컴퓨터의 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-500">Specifies an array of names of virtual machines.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ed47-501">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ed47-501">CommonParameters</span></span>

<span data-ttu-id="9ed47-502">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ed47-502">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ed47-503">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-503">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ed47-504">입력</span><span class="sxs-lookup"><span data-stu-id="9ed47-504">INPUTS</span></span>

### <span data-ttu-id="9ed47-505">System.object.</span><span class="sxs-lookup"><span data-stu-id="9ed47-505">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="9ed47-506">스크립트 블록의 명령을로 파이프 할 수 있습니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9ed47-506">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="9ed47-507">`$Input`자동 변수를 사용 하 여 명령에서 입력 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-507">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="9ed47-508">출력</span><span class="sxs-lookup"><span data-stu-id="9ed47-508">OUTPUTS</span></span>

### <span data-ttu-id="9ed47-509">Runspace (호출 된 명령의 출력 또는 호출 된 명령의 출력)를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-509">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="9ed47-510">**AsJob** 매개 변수를 사용 하는 경우이 cmdlet은 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-510">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="9ed47-511">**InDisconnectedSession** 매개 변수를 지정 하면는 `Invoke-Command` **PSSession** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-511">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="9ed47-512">그렇지 않으면 호출 된 명령의 출력을 반환 합니다 .이는 **ScriptBlock** 매개 변수의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-512">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="9ed47-513">참고</span><span class="sxs-lookup"><span data-stu-id="9ed47-513">NOTES</span></span>

<span data-ttu-id="9ed47-514">Windows Vista 이상 버전의 Windows 운영 체제에서 **ComputerName** 매개 변수를 사용 하 여 `Invoke-Command` 로컬 컴퓨터에서 명령을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-514">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="9ed47-515">여러 컴퓨터에서 명령을 실행 하는 경우 PowerShell은 목록에 나타나는 순서 대로 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-515">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="9ed47-516">그러나 명령 출력은 원격 컴퓨터에서 수신 된 순서 대로 표시 됩니다 .이는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-516">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="9ed47-517">실행 되는 명령으로 인해 발생 하는 오류는 `Invoke-Command` 명령 결과에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-517">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="9ed47-518">로컬 명령에서 종료 오류인 오류는 원격 명령에서 종료되지 않는 오류로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-518">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="9ed47-519">이 전략은 한 컴퓨터에서 종료 오류가 실행 되는 모든 컴퓨터에서 해당 명령을 닫지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-519">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="9ed47-520">이 방법은 원격 명령이 한 컴퓨터에서 실행되는 경우에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-520">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="9ed47-521">원격 컴퓨터가 로컬 컴퓨터가 신뢰 하는 도메인에 없는 경우 컴퓨터에서 사용자 자격 증명을 인증 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-521">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="9ed47-522">WS-MANAGEMENT에서 신뢰할 수 있는 호스트 목록에 원격 컴퓨터를 추가 하려면 공급자에서 다음 명령을 사용 합니다 `WSMAN` `<Remote-Computer-Name>` . 여기서은 원격 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-522">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="9ed47-523">**InDisconnectedSession** 매개 변수를 사용 하 여 **PSSession** 의 연결을 끊으면 세션 상태가 **Disconnected** 이 고 availability가 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-523">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None**.</span></span> <span data-ttu-id="9ed47-524">**State** 속성 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-524">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="9ed47-525">**연결 끊김** 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-525">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="9ed47-526">그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-526">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="9ed47-527">다른 세션에 연결되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-527">It might be connected to a different session.</span></span> <span data-ttu-id="9ed47-528">세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-528">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="9ed47-529">**Availability** 값이 **None** 이면 세션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-529">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="9ed47-530">**사용 중** 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ed47-530">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="9ed47-531">세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ed47-531">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="9ed47-532">세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ed47-532">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="9ed47-533">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9ed47-533">RELATED LINKS</span></span>

[<span data-ttu-id="9ed47-534">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="9ed47-534">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="9ed47-535">about_Remote</span><span class="sxs-lookup"><span data-stu-id="9ed47-535">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="9ed47-536">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="9ed47-536">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="9ed47-537">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="9ed47-537">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="9ed47-538">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="9ed47-538">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="9ed47-539">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="9ed47-539">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="9ed47-540">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="9ed47-540">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="9ed47-541">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="9ed47-541">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="9ed47-542">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="9ed47-542">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="9ed47-543">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="9ed47-543">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="9ed47-544">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9ed47-544">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="9ed47-545">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="9ed47-545">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="9ed47-546">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="9ed47-546">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
