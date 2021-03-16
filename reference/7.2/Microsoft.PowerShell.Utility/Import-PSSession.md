---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 1a87783f9d12d852d3a6809e9457a55ad6e7be50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601833"
---
# <span data-ttu-id="9fc19-102">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="9fc19-102">Import-PSSession</span></span>

## <span data-ttu-id="9fc19-103">개요</span><span class="sxs-lookup"><span data-stu-id="9fc19-103">SYNOPSIS</span></span>
<span data-ttu-id="9fc19-104">다른 세션의 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-104">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="9fc19-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9fc19-105">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="9fc19-106">설명</span><span class="sxs-lookup"><span data-stu-id="9fc19-106">DESCRIPTION</span></span>

<span data-ttu-id="9fc19-107">`Import-PSSession`Cmdlet은 로컬 또는 원격 컴퓨터의 PSSession에서 cmdlet, 함수 및 별칭과 같은 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-107">The `Import-PSSession` cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span> <span data-ttu-id="9fc19-108">`Get-Command`Cmdlet이 PSSession에서 찾을 수 있는 모든 명령을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-108">You can import any command that the `Get-Command` cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="9fc19-109">명령을 사용 하 여 `Import-PSSession` Microsoft Exchange Server shell과 같은 사용자 지정 된 셸에서 또는 현재 세션에 있지 않은 Windows PowerShell 모듈 및 스냅인 또는 다른 요소를 포함 하는 세션에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-109">Use an `Import-PSSession` command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="9fc19-110">명령을 가져오려면 먼저 cmdlet을 사용 `New-PSSession` 하 여 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-110">To import commands, first use the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="9fc19-111">그런 다음 cmdlet을 사용 `Import-PSSession` 하 여 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-111">Then, use the `Import-PSSession` cmdlet to import the commands.</span></span> <span data-ttu-id="9fc19-112">기본적으로는 `Import-PSSession` 현재 세션에 있는 명령과 이름이 같은 명령을 제외한 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-112">By default, `Import-PSSession` imports all commands except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="9fc19-113">모든 명령을 가져오려면 **AllowClobber** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-113">To import all the commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="9fc19-114">가져온 명령은 세션의 다른 명령과 같은 방법으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-114">You can use imported commands just as you would use any command in the session.</span></span> <span data-ttu-id="9fc19-115">가져온 명령을 사용할 때 명령에서 가져온 부분은 암시적으로는 원래 있던 세션에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-115">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span> <span data-ttu-id="9fc19-116">그러나 원격 작업은 전적으로 Windows PowerShell에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-116">However, the remote operations are handled entirely by Windows PowerShell.</span></span> <span data-ttu-id="9fc19-117">다른 세션(PSSession)에 대한 연결을 열어 두어야 하는 경우를 제외하면 원격 작업은 신경쓰지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-117">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span> <span data-ttu-id="9fc19-118">다른 세션에 대한 연결을 닫으면 가져온 명령을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-118">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="9fc19-119">가져온 명령은 로컬 명령 보다 실행 하는 데 더 오래 걸릴 수 있으므로는 `Import-PSSession` 가져온 모든 명령에 **AsJob** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-119">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="9fc19-120">이 매개 변수는 명령을 Windows PowerShell 백그라운드 작업으로 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-120">This parameter allows you to run the command as a Windows PowerShell background job.</span></span> <span data-ttu-id="9fc19-121">자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-121">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span></span>

<span data-ttu-id="9fc19-122">를 사용 하는 경우 `Import-PSSession` Windows PowerShell은 가져온 명령을 사용자의 세션에만 존재 하는 임시 모듈에 추가 하 고 해당 모듈을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-122">When you use `Import-PSSession`, Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span> <span data-ttu-id="9fc19-123">이후 세션에서 사용할 수 있는 영구 모듈을 만들려면 cmdlet을 사용 `Export-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-123">To create a persistent module that you can use in future sessions, use the `Export-PSSession` cmdlet.</span></span>

<span data-ttu-id="9fc19-124">이 `Import-PSSession` cmdlet은 Windows PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-124">The `Import-PSSession` cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span> <span data-ttu-id="9fc19-125">명령을 현재 세션으로 가져올 때 원래 세션이 나 원래 컴퓨터의 유사한 세션에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-125">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="9fc19-126">Windows PowerShell 3.0부터 cmdlet을 사용 `Import-Module` 하 여 원격 세션에서 현재 세션으로 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-126">Beginning in Windows PowerShell 3.0, you can use the `Import-Module` cmdlet to import modules from a remote session into the current session.</span></span> <span data-ttu-id="9fc19-127">이 기능은 암시적 원격을 사용하며</span><span class="sxs-lookup"><span data-stu-id="9fc19-127">This feature uses implicit remoting.</span></span> <span data-ttu-id="9fc19-128">를 사용 하 여 `Import-PSSession` 원격 세션에서 선택한 모듈을 현재 세션으로 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-128">It is equivalent to using `Import-PSSession` to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="9fc19-129">예제</span><span class="sxs-lookup"><span data-stu-id="9fc19-129">EXAMPLES</span></span>

### <span data-ttu-id="9fc19-130">예제 1: PSSession에서 모든 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fc19-130">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="9fc19-131">이 명령은 현재 세션에 있는 명령과 이름이 같은 명령을 제외하고 Server01 컴퓨터의 PSSession에 있는 모든 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-131">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="9fc19-132">**CommandName** 매개 변수를 사용하지 않으므로 가져온 명령에 필요한 모든 형식 지정 데이터도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-132">Because this command does not use the **CommandName** parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="9fc19-133">예 2: 특정 문자열로 끝나는 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fc19-133">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="9fc19-134">이 명령은 "-test"로 끝나는 이름의 명령을 PSSession에서 로컬 세션으로 가져온 다음 가져온 cmdlet을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-134">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="9fc19-135">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-135">The first command uses the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="9fc19-136">PSSession을 `$S` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-136">It saves the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="9fc19-137">두 번째 명령은 cmdlet을 사용 하 여 `Import-PSSession` 의 PSSession에 있는 명령을 `$S` 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-137">The second command uses the `Import-PSSession` cmdlet to import commands from the PSSession in `$S` into the current session.</span></span> <span data-ttu-id="9fc19-138">**CommandName** 매개 변수를 사용하여 Test 명사가 포함된 명령을 지정하고 **FormatTypeName** 매개 변수를 사용하여 Test 명령에 대한 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-138">It uses the **CommandName** parameter to specify commands with the Test noun and the **FormatTypeName** parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="9fc19-139">세 번째 및 네 번째 명령은 가져온 명령을 현재 세션에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-139">The third and fourth commands use the imported commands in the current session.</span></span> <span data-ttu-id="9fc19-140">가져온 명령은 실제로 현재 세션에 추가되므로 로컬 구문을 사용하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-140">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span> <span data-ttu-id="9fc19-141">가져온 명령을 실행 하는 데 cmdlet을 사용할 필요는 없습니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-141">You do not need to use the `Invoke-Command` cmdlet to run an imported command.</span></span>

### <span data-ttu-id="9fc19-142">예제 3: PSSession에서 cmdlet 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fc19-142">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="9fc19-143">이 예제에서는 가져온 cmdlet을 로컬 cmdlet과 같은 방법으로 사용할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-143">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="9fc19-144">이러한 명령은 Server01 컴퓨터의 PSSession에서 및 cmdlet을 가져오고 `New-Test` `Get-Test` `Set-Test` Server02 컴퓨터의 pssession에서 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-144">These commands import the `New-Test` and `Get-Test` cmdlets from a PSSession on the Server01 computer and the `Set-Test` cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="9fc19-145">이 cmdlet은 각기 다른 PSSession에서 가져온 것이지만 cmdlet 간에 개체를 파이프해도 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-145">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="9fc19-146">예제 4: 가져온 명령을 백그라운드 작업으로 실행</span><span class="sxs-lookup"><span data-stu-id="9fc19-146">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="9fc19-147">이 예제에서는 가져온 명령을 백그라운드 작업으로 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-147">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="9fc19-148">가져온 명령은 로컬 명령 보다 실행 하는 데 더 오래 걸릴 수 있으므로는 `Import-PSSession` 가져온 모든 명령에 **AsJob** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-148">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="9fc19-149">**AsJob** 매개 변수를 사용하면 명령을 백그라운드 작업으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-149">The **AsJob** parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="9fc19-150">첫 번째 명령은 Server01 컴퓨터에 PSSession을 만들고 PSSession 개체를 변수에 저장 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-150">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the `$S` variable.</span></span>

<span data-ttu-id="9fc19-151">두 번째 명령은를 사용 하 여 `Import-PSSession` 의 PSSession에서 현재 세션으로 테스트 cmdlet을 가져옵니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-151">The second command uses `Import-PSSession` to import the Test cmdlets from the PSSession in `$S` into the current session.</span></span>

<span data-ttu-id="9fc19-152">세 번째 명령은 가져온 cmdlet의 **AsJob** 매개 변수를 사용 하 여 `New-Test` `New-Test` 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-152">The third command uses the **AsJob** parameter of the imported `New-Test` cmdlet to run a `New-Test` command as a background job.</span></span> <span data-ttu-id="9fc19-153">이 명령은에서 반환 하는 작업 개체를 저장 `New-Test` `$batch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-153">The command saves the job object that `New-Test` returns in the `$batch` variable.</span></span>

<span data-ttu-id="9fc19-154">네 번째 명령은 cmdlet을 사용 하 여 `Receive-Job` 변수의 작업 결과를 가져옵니다 `$batch` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-154">The fourth command uses the `Receive-Job` cmdlet to get the results of the job in the `$batch` variable.</span></span>

### <span data-ttu-id="9fc19-155">예 5: Windows PowerShell 모듈에서 cmdlet 및 함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fc19-155">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="9fc19-156">이 예제에서는 cmdlet 및 함수를 원격 컴퓨터의 Windows PowerShell 모듈에서 현재 세션으로 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-156">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="9fc19-157">첫 번째 명령은 Server01 컴퓨터에 PSSession을 만든 다음 변수에 저장 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-157">The first command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span>

<span data-ttu-id="9fc19-158">두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Import-Module` 의 PSSession에서 명령을 실행 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-158">The second command uses the `Invoke-Command` cmdlet to run an `Import-Module` command in the PSSession in `$S`.</span></span>

<span data-ttu-id="9fc19-159">일반적으로이 모듈은 `Import-Module` Windows PowerShell 프로필의 명령으로 모든 세션에 추가 되지만 프로필은 pssession에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-159">Typically, the module would be added to all sessions by an `Import-Module` command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="9fc19-160">세 번째 명령은의 **module** 매개 변수를 사용 하 여 `Import-PSSession` 모듈의 cmdlet 및 함수를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-160">The third command uses the **Module** parameter of `Import-PSSession` to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="9fc19-161">예제 6: 임시 파일에 모듈 만들기</span><span class="sxs-lookup"><span data-stu-id="9fc19-161">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="9fc19-162">이 예제에서는 `Import-PSSession` 디스크에서 임시 파일에 모듈을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-162">This example shows that `Import-PSSession` creates a module in a temporary file on disk.</span></span> <span data-ttu-id="9fc19-163">또한 현재 세션으로 가져오기 전에 모든 명령이 함수로 변환됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-163">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="9fc19-164">이 명령은 cmdlet을 사용 하 여 `Import-PSSession` `Get-Date` Cmdlet 및 searchhelp 함수를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-164">The command uses the `Import-PSSession` cmdlet to import a `Get-Date` cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="9fc19-165">`Import-PSSession`Cmdlet은 임시 모듈을 나타내는 **Psmoduleinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-165">The `Import-PSSession` cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span> <span data-ttu-id="9fc19-166">**Path** 속성의 값은 `Import-PSSession` 스크립트 모듈 (.psm1) 파일을 임시 위치에 만들었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-166">The value of the **Path** property shows that `Import-PSSession` created a script module (.psm1) file in a temporary location.</span></span> <span data-ttu-id="9fc19-167">**ExportedFunctions** 속성은 `Get-Date` Cmdlet과 searchhelp 함수를 둘 다 함수로 가져왔으므로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-167">The **ExportedFunctions** property shows that the `Get-Date` cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="9fc19-168">예 7: 가져온 명령에 의해 숨겨진 명령 실행</span><span class="sxs-lookup"><span data-stu-id="9fc19-168">Example 7: Run a command that is hidden by an imported command</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

<span data-ttu-id="9fc19-169">이 예제에서는 가져온 명령에서 숨기는 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-169">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="9fc19-170">첫 번째 명령은 `Get-Date` 변수의 PSSession에서 cmdlet을 가져옵니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-170">The first command imports a `Get-Date` cmdlet from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="9fc19-171">현재 세션에 cmdlet이 포함 되어 있으므로 `Get-Date` 명령에 **AllowClobber** 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-171">Because the current session includes a `Get-Date` cmdlet, the **AllowClobber** parameter is required in the command.</span></span>

<span data-ttu-id="9fc19-172">두 번째 명령은 cmdlet의 **all** 매개 변수를 사용 하 여 `Get-Command` `Get-Date` 현재 세션에 있는 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-172">The second command uses the **All** parameter of the `Get-Command` cmdlet to get all `Get-Date` commands in the current session.</span></span> <span data-ttu-id="9fc19-173">출력은 세션에 원래 cmdlet과 함수가 포함 되어 있음을 보여 줍니다 `Get-Date` `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-173">The output shows that the session includes the original `Get-Date` cmdlet and a `Get-Date` function.</span></span> <span data-ttu-id="9fc19-174">`Get-Date`함수는의 PSSession에서 가져온 cmdlet을 실행 `Get-Date` `$S` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-174">The `Get-Date` function runs the imported `Get-Date` cmdlet in the PSSession in `$S`.</span></span>

<span data-ttu-id="9fc19-175">세 번째 명령은 명령을 실행 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-175">The third command runs a `Get-Date` command.</span></span> <span data-ttu-id="9fc19-176">함수는 cmdlet 보다 우선 하므로 Windows PowerShell에서 율리우스 날짜를 반환 하는 가져온 함수를 실행 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-176">Because functions take precedence over cmdlets, Windows PowerShell runs the imported `Get-Date` function, which returns a Julian date.</span></span>

<span data-ttu-id="9fc19-177">네 번째 및 다섯 번째 명령은 가져온 명령에서 숨기는 명령을 실행하는 데 정규화된 이름을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-177">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="9fc19-178">네 번째 명령은 원래 `Get-Date` cmdlet이 현재 세션에 추가 된 Windows PowerShell 스냅인의 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-178">The fourth command gets the name of the Windows PowerShell snap-in that added the original `Get-Date` cmdlet to the current session.</span></span>

<span data-ttu-id="9fc19-179">다섯 번째 명령은 cmdlet의 스냅인 정규화 된 이름을 사용 하 여 `Get-Date` `Get-Date` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-179">The fifth command uses the snap-in-qualified name of the `Get-Date` cmdlet to run a `Get-Date` command.</span></span>

<span data-ttu-id="9fc19-180">명령 우선 순위 및 숨겨진 명령에 대한 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-180">For more information about command precedence and hidden commands, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="9fc19-181">예 8: 이름에 특정 문자열이 있는 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fc19-181">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

<span data-ttu-id="9fc19-182">이 명령은의 PSSession에 있는 항목의 이름이 포함 된 명령을 가져옵니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-182">This command imports commands whose names include Item from the PSSession in `$S`.</span></span> <span data-ttu-id="9fc19-183">명령에는 **CommandName** 매개 변수는 포함 되지만 **FormatTypeData** 매개 변수는 포함 되어 있지 않으므로 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-183">Because the command includes the **CommandName** parameter but not the **FormatTypeData** parameter, only the command is imported.</span></span>

<span data-ttu-id="9fc19-184">를 사용 하 여 `Import-PSSession` 원격 컴퓨터에서 명령을 실행 하 고 현재 세션에 명령에 대 한 형식 지정 데이터가 이미 있는 경우이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-184">Use this command when you are using `Import-PSSession` to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="9fc19-185">예 9: Module 매개 변수를 사용 하 여 세션으로 가져온 명령 검색</span><span class="sxs-lookup"><span data-stu-id="9fc19-185">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

<span data-ttu-id="9fc19-186">이 명령은의 **Module** 매개 변수를 사용 하 여 `Get-Command` 명령에 의해 세션으로 가져온 명령을 찾는 방법을 보여 줍니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-186">This command shows how to use the **Module** parameter of `Get-Command` to find out which commands were imported into the session by an `Import-PSSession` command.</span></span>

<span data-ttu-id="9fc19-187">첫 번째 명령은 cmdlet을 사용 하 여 `Import-PSSession` 변수의 PSSession에서 "bits"를 포함 하는 명령을 가져옵니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-187">The first command uses the `Import-PSSession` cmdlet to import commands whose names include "bits" from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="9fc19-188">`Import-PSSession`명령은 임시 모듈을 반환 하 고,이 명령은 모듈을 변수에 저장 합니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-188">The `Import-PSSession` command returns a temporary module, and the command saves the module in the `$m` variable.</span></span>

<span data-ttu-id="9fc19-189">두 번째 명령은 cmdlet을 사용 하 여 `Get-Command` 변수에서 모듈에 의해 내보내지는 명령을 가져옵니다 `$M` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-189">The second command uses the `Get-Command` cmdlet to get the commands that are exported by the module in the `$M` variable.</span></span>

<span data-ttu-id="9fc19-190">**Module** 매개 변수는 모듈 이름에 사용되는 문자열 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-190">The **Module** parameter takes a string value, which is designed for the module name.</span></span> <span data-ttu-id="9fc19-191">그러나 모듈 개체를 제출할 경우 Windows PowerShell은 모듈 이름을 반환하는 모듈 개체의 **ToString** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-191">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="9fc19-192">`Get-Command`명령은 "와 동일 합니다 `Get-Command $M.Name` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-192">The `Get-Command` command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="9fc19-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9fc19-193">PARAMETERS</span></span>

### <span data-ttu-id="9fc19-194">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="9fc19-194">-AllowClobber</span></span>

<span data-ttu-id="9fc19-195">현재 세션에 있는 명령과 이름이 동일한 경우에도이 cmdlet이 지정 된 명령을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-195">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="9fc19-196">현재 세션에 있는 명령과 이름이 같은 명령을 가져오는 경우 가져온 명령이 원래 명령을 숨기거나 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-196">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span> <span data-ttu-id="9fc19-197">자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-197">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="9fc19-198">기본적으로는 `Import-PSSession` 현재 세션에 있는 명령과 이름이 동일한 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-198">By default, `Import-PSSession` does not import commands that have the same name as commands in the current session.</span></span>

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

### <span data-ttu-id="9fc19-199">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9fc19-199">-ArgumentList</span></span>

<span data-ttu-id="9fc19-200">지정 된 인수 (매개 변수 값)를 사용 하 여 생성 되는 명령 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-200">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="9fc19-201">예를 들어 `Get-Item` 인증서 (Cert:)에서 명령의 변형을 가져오려면 드라이브의 PSSession에 `$S` 를 입력 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-201">For instance, to import the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="9fc19-202">-인증서</span><span class="sxs-lookup"><span data-stu-id="9fc19-202">-Certificate</span></span>

<span data-ttu-id="9fc19-203">에서 만드는 임시 모듈에서 서식 파일 (\* .Format.ps1xml) 또는 스크립트 모듈 파일 (. .psm1)에 서명 하는 데 사용 되는 클라이언트 인증서를 지정 합니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-203">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that `Import-PSSession` creates.</span></span>

<span data-ttu-id="9fc19-204">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-204">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="9fc19-205">인증서를 찾으려면 cmdlet을 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 (Cert:)에서 cmdlet을 사용 합니다. 드라이브나.</span><span class="sxs-lookup"><span data-stu-id="9fc19-205">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="9fc19-206">인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-206">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-207">-CommandName</span><span class="sxs-lookup"><span data-stu-id="9fc19-207">-CommandName</span></span>

<span data-ttu-id="9fc19-208">지정 된 이름이 나 이름 패턴을 사용 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-208">Specifies commands with the specified names or name patterns.</span></span> <span data-ttu-id="9fc19-209">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-209">Wildcards are permitted.</span></span> <span data-ttu-id="9fc19-210">**CommandName** 또는 별칭, **이름** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-210">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="9fc19-211">기본적으로는 `Import-PSSession` 현재 세션에 있는 명령과 이름이 같은 명령을 제외 하 고 세션에서 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-211">By default, `Import-PSSession` imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="9fc19-212">이렇게 하면 가져온 명령이 세션의 명령을 숨기거나 바꾸지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-212">This prevents imported commands from hiding or replacing commands in the session.</span></span> <span data-ttu-id="9fc19-213">다른 명령을 숨기거나 바꾸는 명령을 포함하여 모든 명령을 가져오려면 **AllowClobber** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-213">To import all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="9fc19-214">**CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-214">If you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="9fc19-215">마찬가지로, **FormatTypeName** 매개 변수를 사용할 경우 **CommandName** 매개 변수를 사용하지 않으면 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-215">Similarly, if you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-216">-CommandType</span><span class="sxs-lookup"><span data-stu-id="9fc19-216">-CommandType</span></span>

<span data-ttu-id="9fc19-217">명령 개체의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-217">Specifies the type of command objects.</span></span> <span data-ttu-id="9fc19-218">기본값은 Cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-218">The default value is Cmdlet.</span></span> <span data-ttu-id="9fc19-219">**CommandType** 또는 별칭 **Type** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-219">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="9fc19-220">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-220">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9fc19-221">앤티앨리어스.</span><span class="sxs-lookup"><span data-stu-id="9fc19-221">Alias.</span></span> <span data-ttu-id="9fc19-222">원격 세션에 있는 Windows PowerShell 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-222">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="9fc19-223">모두.</span><span class="sxs-lookup"><span data-stu-id="9fc19-223">All.</span></span> <span data-ttu-id="9fc19-224">원격 세션에 있는 cmdlet 및 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-224">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="9fc19-225">애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-225">Application.</span></span> <span data-ttu-id="9fc19-226">`$env:path`.Txt, .exe 및 .dll 파일을 비롯 하 여 원격 세션의 Path 환경 변수 ()에 나열 된 경로에 Windows-PowerShell 파일 이외의 모든 파일.</span><span class="sxs-lookup"><span data-stu-id="9fc19-226">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable (`$env:path`) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="9fc19-227">#A0.</span><span class="sxs-lookup"><span data-stu-id="9fc19-227">Cmdlet.</span></span> <span data-ttu-id="9fc19-228">원격 세션에 있는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-228">The cmdlets in the remote session.</span></span> <span data-ttu-id="9fc19-229">기본값은 "Cmdlet"입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-229">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="9fc19-230">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="9fc19-230">ExternalScript.</span></span> <span data-ttu-id="9fc19-231">원격 세션의 Path 환경 변수 ()에 나열 된 경로에 있는 ps1 파일. `$env:path`</span><span class="sxs-lookup"><span data-stu-id="9fc19-231">The .ps1 files in the paths listed in the Path environment variable (`$env:path`) in the remote session.</span></span>
- <span data-ttu-id="9fc19-232">필터 및 함수</span><span class="sxs-lookup"><span data-stu-id="9fc19-232">Filter and Function.</span></span> <span data-ttu-id="9fc19-233">원격 세션에 있는 Windows PowerShell 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-233">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="9fc19-234">스크립트.</span><span class="sxs-lookup"><span data-stu-id="9fc19-234">Script.</span></span> <span data-ttu-id="9fc19-235">원격 세션에 있는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-235">The script blocks in the remote session.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-236">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="9fc19-236">-DisableNameChecking</span></span>

<span data-ttu-id="9fc19-237">이 cmdlet은 이름에 승인 되지 않은 동사 나 금지 된 문자가 포함 된 cmdlet 또는 함수를 가져올 때 경고 메시지를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-237">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="9fc19-238">기본적으로 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 Windows PowerShell은 다음 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-238">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="9fc19-239">"경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-239">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="9fc19-240">자세한 내용을 보려면 Verbose 매개 변수를 사용 하 고, `Get-Verb` 승인 된 동사 목록을 보려면을 입력 합니다. "</span><span class="sxs-lookup"><span data-stu-id="9fc19-240">Use the Verbose parameter for more detail or type `Get-Verb` to see the list of approved verbs."</span></span>

<span data-ttu-id="9fc19-241">이 메시지는 경고일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-241">This message is only a warning.</span></span> <span data-ttu-id="9fc19-242">비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-242">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="9fc19-243">메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-243">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="9fc19-244">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="9fc19-244">-FormatTypeName</span></span>

<span data-ttu-id="9fc19-245">지정 된 Microsoft .NET Framework 형식에 대 한 형식 지정 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-245">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="9fc19-246">유형 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-246">Enter the type names.</span></span>
<span data-ttu-id="9fc19-247">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-247">Wildcards are permitted.</span></span>

<span data-ttu-id="9fc19-248">이 매개 변수 값은 `Get-FormatData` 명령을 가져올 세션의 명령에서 반환 하는 형식의 이름 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-248">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="9fc19-249">원격 세션의 모든 형식 지정 데이터를 가져오려면를 입력 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-249">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="9fc19-250">명령에 **CommandName** 또는 **formattypename** 매개 변수가 포함 되어 있지 않으면 `Import-PSSession` `Get-FormatData` 원격 세션의 명령에서 반환 하는 모든 .NET Framework 형식에 대 한 형식 지정 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-250">If the command does not include either the **CommandName** or **FormatTypeName** parameter, `Import-PSSession` imports formatting instructions for all .NET Framework types returned by a `Get-FormatData` command in the remote session.</span></span>

<span data-ttu-id="9fc19-251">**FormatTypeName** 매개 변수를 사용할 경우 **CommandName** 매개 변수를 사용하지 않으면 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-251">If you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="9fc19-252">마찬가지로, **CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-252">Similarly, if you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-253">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="9fc19-253">-FullyQualifiedModule</span></span>

<span data-ttu-id="9fc19-254">PowerShell SDK의 [ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) 의 설명 섹션에서 설명 하는 이름이 **ModuleSpecification** 개체 형식으로 지정 된 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-254">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in the PowerShell SDK.</span></span> <span data-ttu-id="9fc19-255">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식으로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-255">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

- <span data-ttu-id="9fc19-256">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` 또는</span><span class="sxs-lookup"><span data-stu-id="9fc19-256">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` or</span></span>
- <span data-ttu-id="9fc19-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span><span class="sxs-lookup"><span data-stu-id="9fc19-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span></span>

<span data-ttu-id="9fc19-258">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-258">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="9fc19-259">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-259">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="9fc19-260">두 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-260">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-261">-모듈</span><span class="sxs-lookup"><span data-stu-id="9fc19-261">-Module</span></span>

<span data-ttu-id="9fc19-262">Windows PowerShell 스냅인 및 모듈에서 명령의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-262">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span> <span data-ttu-id="9fc19-263">스냅인 및 모듈 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-263">Enter the snap-in and module names.</span></span> <span data-ttu-id="9fc19-264">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-264">Wildcards are not permitted.</span></span>

<span data-ttu-id="9fc19-265">`Import-PSSession` 스냅인에서 공급자를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-265">`Import-PSSession` cannot import providers from a snap-in.</span></span>

<span data-ttu-id="9fc19-266">자세한 내용은 [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) 및 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-266">For more information, see [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-267">-접두사</span><span class="sxs-lookup"><span data-stu-id="9fc19-267">-Prefix</span></span>

<span data-ttu-id="9fc19-268">가져온 명령 이름의 명사에 대 한 접두사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-268">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="9fc19-269">이 매개 변수를 사용하면 세션에 있는 서로 다른 명령의 이름이 같은 경우 발생할 수 있는 이름 충돌을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-269">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="9fc19-270">예를 들어, 접두사를 원격으로 지정 하 고 cmdlet을 가져오면이 `Get-Date` cmdlet은 세션에서로 알려져 `Get-RemoteDate` 있으며 원래 cmdlet과는 혼동 되지 않습니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-270">For instance, if you specify the prefix Remote and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-RemoteDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

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

### <span data-ttu-id="9fc19-271">-Session</span><span class="sxs-lookup"><span data-stu-id="9fc19-271">-Session</span></span>

<span data-ttu-id="9fc19-272">Cmdlet을 가져올 **PSSession** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-272">Specifies the **PSSession** from which the cmdlets are imported.</span></span> <span data-ttu-id="9fc19-273">세션 개체가 포함 된 변수를 입력 하거나 세션 개체를 가져오는 명령 (예: 또는 명령)을 `New-PSSession` 입력 `Get-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-273">Enter a variable that contains a session object or a command that gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="9fc19-274">세션은 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-274">You can specify only one session.</span></span> <span data-ttu-id="9fc19-275">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-275">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fc19-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9fc19-276">CommonParameters</span></span>

<span data-ttu-id="9fc19-277">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9fc19-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9fc19-278">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9fc19-279">입력</span><span class="sxs-lookup"><span data-stu-id="9fc19-279">INPUTS</span></span>

### <span data-ttu-id="9fc19-280">없음</span><span class="sxs-lookup"><span data-stu-id="9fc19-280">None</span></span>

<span data-ttu-id="9fc19-281">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-281">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="9fc19-282">출력</span><span class="sxs-lookup"><span data-stu-id="9fc19-282">OUTPUTS</span></span>

### <span data-ttu-id="9fc19-283">System.object..</span><span class="sxs-lookup"><span data-stu-id="9fc19-283">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="9fc19-284">`Import-PSSession` 및 cmdlet이 반환 하는 것과 동일한 모듈 개체를 반환 `New-Module` `Get-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-284">`Import-PSSession` returns the same module object that `New-Module` and `Get-Module` cmdlets return.</span></span>
<span data-ttu-id="9fc19-285">그러나 가져온 모듈은 임시 모듈이며 현재 세션에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-285">However, the imported module is temporary and exists only in the current session.</span></span> <span data-ttu-id="9fc19-286">디스크에 영구 모듈을 만들려면 cmdlet을 사용 `Export-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-286">To create a permanent module on disk, use the `Export-PSSession` cmdlet.</span></span>

## <span data-ttu-id="9fc19-287">참고</span><span class="sxs-lookup"><span data-stu-id="9fc19-287">NOTES</span></span>

- <span data-ttu-id="9fc19-288">`Import-PSSession` 은 PowerShell 원격 인프라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-288">`Import-PSSession` relies on the  PowerShell remoting infrastructure.</span></span> <span data-ttu-id="9fc19-289">이 cmdlet을 사용하려면 WS-Management 원격 기능을 사용하도록 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-289">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="9fc19-290">자세한 내용은 [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) 및 [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-290">For more information, see [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) and [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="9fc19-291">`Import-PSSession` 변수 또는 PowerShell 공급자를 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-291">`Import-PSSession` does not import variables or  PowerShell providers.</span></span>
- <span data-ttu-id="9fc19-292">현재 세션에 있는 명령과 이름이 같은 명령을 가져오는 경우 가져온 명령은 세션에 있는 별칭, 함수 및 cmdlet을 숨길 수 있으며 세션에 있는 함수 및 변수를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-292">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="9fc19-293">이름 충돌을 방지하려면 **Prefix** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-293">To prevent name conflicts, use the **Prefix** parameter.</span></span> <span data-ttu-id="9fc19-294">자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-294">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="9fc19-295">`Import-PSSession` 모든 명령을 가져오기 전에 함수로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-295">`Import-PSSession` converts all commands into functions before it imports them.</span></span> <span data-ttu-id="9fc19-296">그 결과 가져온 명령은 원래 명령 유형을 유지할 때의 동작과 다소 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-296">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="9fc19-297">예를 들어 PSSession에서 cmdlet을 가져온 다음 모듈 또는 스냅인에서 같은 이름의 cmdlet을 가져오는 경우 함수가 cmdlet보다 우선적으로 적용되기 때문에 항상 PSSession에서 가져온 cmdlet이 기본적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-297">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="9fc19-298">반대로 별칭을 같은 이름의 별칭이 있는 세션으로 가져오는 경우 별칭이 함수보다 우선적으로 적용되기 때문에 항상 원래 별칭이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-298">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="9fc19-299">자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc19-299">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="9fc19-300">`Import-PSSession` cmdlet을 사용 하 여 `Write-Progress` 명령 진행률을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-300">`Import-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="9fc19-301">명령이 실행되는 동안 진행률 표시줄을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-301">You might see the progress bar while the command is running.</span></span>
- <span data-ttu-id="9fc19-302">가져올 명령을 찾기 위해에서 cmdlet을 `Import-PSSession` 사용 하 여 `Invoke-Command` `Get-Command` PSSession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-302">To find the commands to import, `Import-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="9fc19-303">명령에 대 한 형식 지정 데이터를 가져오기 위해 cmdlet을 사용 합니다 `Get-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-303">To get formatting data for the commands, it uses the `Get-FormatData` cmdlet.</span></span> <span data-ttu-id="9fc19-304">명령을 실행할 때 이러한 cmdlet의 오류 메시지가 표시 될 수 있습니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-304">You might see error messages from these cmdlets when you run an `Import-PSSession` command.</span></span> <span data-ttu-id="9fc19-305">또한,, `Import-PSSession` `Get-Command` `Get-FormatData` `Select-Object` 및 cmdlet을 포함 하지 않는 PSSession에서 명령을 가져올 수 없습니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-305">Also, `Import-PSSession` cannot import commands from a PSSession that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>
- <span data-ttu-id="9fc19-306">가져온 명령의 경우 사용자 인터페이스를 통해 메모장 등의 프로그램을 시작할 수 없다는 점을 포함하여 다른 원격 명령과 동일한 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-306">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
- <span data-ttu-id="9fc19-307">Windows PowerShell 프로필은 pssession에서 실행 되지 않으므로 프로필을 통해 세션에 추가 하는 명령은에서 사용할 수 없습니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9fc19-307">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Import-PSSession`.</span></span> <span data-ttu-id="9fc19-308">프로필에서 명령을 가져오려면 명령을 `Invoke-Command` 가져오기 전에 명령을 사용 하 여 PSSession에서 프로필을 수동으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-308">To import commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before importing commands.</span></span>
- <span data-ttu-id="9fc19-309">에서 `Import-PSSession` 형식 지정 데이터를 가져오지 않는 경우에도에서 만드는 임시 모듈에 서식 파일을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-309">The temporary module that `Import-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="9fc19-310">명령이 형식 지정 데이터를 가져오지 않는 경우 만든 형식 지정 파일에 형식 지정 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-310">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
- <span data-ttu-id="9fc19-311">를 사용 하려면 `Import-PSSession` 현재 세션의 실행 정책을 제한 하거나 AllSigned 수 없습니다 .이는를 만드는 임시 모듈에 `Import-PSSession` 이러한 정책에서 금지 되는 서명 되지 않은 스크립트 파일이 포함 되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-311">To use `Import-PSSession`, the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that `Import-PSSession` creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="9fc19-312">`Import-PSSession`로컬 컴퓨터에 대 한 실행 정책을 변경 하지 않고를 사용 하려면의 **Scope** 매개 변수를 사용 하 여 `Set-ExecutionPolicy` 단일 프로세스에 대 한 덜 제한적인 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-312">To use `Import-PSSession` without changing the execution policy for the local computer, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>
- <span data-ttu-id="9fc19-313">Windows PowerShell 2.0에서는 다른 세션에서 가져온 명령에 대한 도움말 항목에 **Prefix** 매개 변수를 사용하여 할당한 접두사가 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-313">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the **Prefix** parameter.</span></span> <span data-ttu-id="9fc19-314">Windows PowerShell 2.0에서 가져온 명령에 대한 도움말을 가져오려면 접두사가 없는 원래 명령 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc19-314">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="9fc19-315">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9fc19-315">RELATED LINKS</span></span>

[<span data-ttu-id="9fc19-316">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="9fc19-316">Export-PSSession</span></span>](Export-PSSession.md)