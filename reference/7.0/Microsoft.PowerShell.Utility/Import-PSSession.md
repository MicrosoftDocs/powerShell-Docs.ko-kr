---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: fafc4da46eb6b6f7cf252d5ca2aa50f6bd42b49f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93209786"
---
# <span data-ttu-id="15fe1-103">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="15fe1-103">Import-PSSession</span></span>

## <span data-ttu-id="15fe1-104">개요</span><span class="sxs-lookup"><span data-stu-id="15fe1-104">SYNOPSIS</span></span>
<span data-ttu-id="15fe1-105">다른 세션의 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-105">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="15fe1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15fe1-106">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="15fe1-107">설명</span><span class="sxs-lookup"><span data-stu-id="15fe1-107">DESCRIPTION</span></span>

<span data-ttu-id="15fe1-108">**가져오기-pssession** cmdlet은 로컬 또는 원격 컴퓨터의 PSSession에서 cmdlet, 함수 및 별칭과 같은 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-108">The **Import-PSSession** cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span>
<span data-ttu-id="15fe1-109">Get-Command cmdlet이 PSSession에서 찾을 수 있는 모든 명령을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-109">You can import any command that the Get-Command cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="15fe1-110">**가져오기-PSSession** 명령을 사용 하 여 Microsoft Exchange Server shell과 같은 사용자 지정 된 셸에서 또는 PowerShell 모듈 및 스냅인을 포함 하는 세션 또는 현재 세션에 있지 않은 다른 요소에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-110">Use an **Import-PSSession** command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="15fe1-111">명령을 가져오려면 먼저 New-PSSession cmdlet을 사용 하 여 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-111">To import commands, first use the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="15fe1-112">그런 다음 **Import-PSSession** cmdlet을 사용하여 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-112">Then, use the **Import-PSSession** cmdlet to import the commands.</span></span>
<span data-ttu-id="15fe1-113">기본적으로 **Import-PSSession** 은 현재 세션에 있는 명령과 이름이 같은 명령을 제외한 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-113">By default, **Import-PSSession** imports all commands except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="15fe1-114">모든 명령을 가져오려면 *AllowClobber* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-114">To import all the commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="15fe1-115">가져온 명령은 세션의 다른 명령과 같은 방법으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-115">You can use imported commands just as you would use any command in the session.</span></span>
<span data-ttu-id="15fe1-116">가져온 명령을 사용할 때 명령에서 가져온 부분은 암시적으로는 원래 있던 세션에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-116">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span>
<span data-ttu-id="15fe1-117">그러나 원격 작업은 PowerShell에서 전체적으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-117">However, the remote operations are handled entirely by PowerShell.</span></span>
<span data-ttu-id="15fe1-118">다른 세션(PSSession)에 대한 연결을 열어 두어야 하는 경우를 제외하면 원격 작업은 신경쓰지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-118">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span>
<span data-ttu-id="15fe1-119">다른 세션에 대한 연결을 닫으면 가져온 명령을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-119">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="15fe1-120">가져온 명령의 경우 로컬 명령보다 실행 시간이 오래 걸릴 수 있으므로 **Import-PSSession** 은 가져온 모든 명령에 *AsJob* 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-120">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="15fe1-121">이 매개 변수를 사용 하 여 명령을 PowerShell 백그라운드 작업으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-121">This parameter allows you to run the command as a PowerShell background job.</span></span>
<span data-ttu-id="15fe1-122">자세한 내용은 about_Jobs를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-122">For more information, see about_Jobs.</span></span>

<span data-ttu-id="15fe1-123">**가져오기 PSSession** 을 사용 하는 경우 PowerShell은 가져온 명령을 세션에만 존재 하는 임시 모듈에 추가 하 고 해당 모듈을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-123">When you use **Import-PSSession** , PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span>
<span data-ttu-id="15fe1-124">이후 세션에서 사용할 수 있는 영구 모듈을 만들려면 Export-PSSession cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-124">To create a persistent module that you can use in future sessions, use the Export-PSSession cmdlet.</span></span>

<span data-ttu-id="15fe1-125">**가져오기 PSSession** Cmdlet은 PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-125">The **Import-PSSession** cmdlet uses the implicit remoting feature of PowerShell.</span></span>
<span data-ttu-id="15fe1-126">명령을 현재 세션으로 가져올 때 원래 세션이 나 원래 컴퓨터의 유사한 세션에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-126">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="15fe1-127">Windows PowerShell 3.0 부터는 Import-Module cmdlet을 사용 하 여 원격 세션에서 현재 세션으로 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-127">Beginning in Windows PowerShell 3.0, you can use the Import-Module cmdlet to import modules from a remote session into the current session.</span></span>
<span data-ttu-id="15fe1-128">이 기능은 암시적 원격을 사용하며</span><span class="sxs-lookup"><span data-stu-id="15fe1-128">This feature uses implicit remoting.</span></span>
<span data-ttu-id="15fe1-129">**Import-PSSession** 을 사용하여 원격 세션의 선택한 모듈을 현재 세션으로 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-129">It is equivalent to using **Import-PSSession** to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="15fe1-130">예제</span><span class="sxs-lookup"><span data-stu-id="15fe1-130">EXAMPLES</span></span>

### <span data-ttu-id="15fe1-131">예제 1: PSSession에서 모든 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="15fe1-131">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="15fe1-132">이 명령은 현재 세션에 있는 명령과 이름이 같은 명령을 제외하고 Server01 컴퓨터의 PSSession에 있는 모든 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-132">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="15fe1-133">*CommandName* 매개 변수를 사용하지 않으므로 가져온 명령에 필요한 모든 형식 지정 데이터도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-133">Because this command does not use the *CommandName* parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="15fe1-134">예 2: 특정 문자열로 끝나는 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="15fe1-134">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="15fe1-135">이 명령은 "-test"로 끝나는 이름의 명령을 PSSession에서 로컬 세션으로 가져온 다음 가져온 cmdlet을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-135">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="15fe1-136">첫 번째 명령은 New-PSSession cmdlet을 사용 하 여 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-136">The first command uses the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="15fe1-137">PSSession을 $S 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-137">It saves the PSSession in the $S variable.</span></span>

<span data-ttu-id="15fe1-138">두 번째 명령은 **import-module** cmdlet을 사용 하 여 $S에서 pssession의 명령을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-138">The second command uses the **Import-PSSession** cmdlet to import commands from the PSSession in $S into the current session.</span></span>
<span data-ttu-id="15fe1-139">*CommandName* 매개 변수를 사용하여 Test 명사가 포함된 명령을 지정하고 *FormatTypeName* 매개 변수를 사용하여 Test 명령에 대한 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-139">It uses the *CommandName* parameter to specify commands with the Test noun and the *FormatTypeName* parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="15fe1-140">세 번째 및 네 번째 명령은 가져온 명령을 현재 세션에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-140">The third and fourth commands use the imported commands in the current session.</span></span>
<span data-ttu-id="15fe1-141">가져온 명령은 실제로 현재 세션에 추가되므로 로컬 구문을 사용하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-141">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span>
<span data-ttu-id="15fe1-142">Invoke-Command cmdlet을 사용 하 여 가져온 명령을 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-142">You do not need to use the Invoke-Command cmdlet to run an imported command.</span></span>

### <span data-ttu-id="15fe1-143">예제 3: PSSession에서 cmdlet 가져오기</span><span class="sxs-lookup"><span data-stu-id="15fe1-143">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="15fe1-144">이 예제에서는 가져온 cmdlet을 로컬 cmdlet과 같은 방법으로 사용할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-144">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="15fe1-145">이 명령은 Server01 컴퓨터의 PSSession에서 New-Test 및 Get-Test cmdlet을 가져오고 Server02 컴퓨터의 PSSession에서 Set-Test cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-145">These commands import the New-Test and Get-Test cmdlets from a PSSession on the Server01 computer and the Set-Test cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="15fe1-146">이 cmdlet은 각기 다른 PSSession에서 가져온 것이지만 cmdlet 간에 개체를 파이프해도 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-146">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="15fe1-147">예제 4: 가져온 명령을 백그라운드 작업으로 실행</span><span class="sxs-lookup"><span data-stu-id="15fe1-147">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="15fe1-148">이 예제에서는 가져온 명령을 백그라운드 작업으로 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-148">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="15fe1-149">가져온 명령의 경우 로컬 명령보다 실행 시간이 오래 걸릴 수 있으므로 **Import-PSSession** 은 가져온 모든 명령에 *AsJob* 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-149">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="15fe1-150">*AsJob* 매개 변수를 사용하면 명령을 백그라운드 작업으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-150">The *AsJob* parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="15fe1-151">첫 번째 명령은 Server01 컴퓨터에 PSSession을 만든 다음 $S 변수에 PSSession 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-151">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the $S variable.</span></span>

<span data-ttu-id="15fe1-152">두 번째 명령은 **가져오기-pssession** 을 사용 하 여 $S의 PSSession에서 현재 세션으로 테스트 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-152">The second command uses **Import-PSSession** to import the Test cmdlets from the PSSession in $S into the current session.</span></span>

<span data-ttu-id="15fe1-153">세 번째 명령은 가져온 New-Test cmdlet의 *AsJob* 매개 변수를 사용하여 New-Test 명령을 백그라운드 작업으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-153">The third command uses the *AsJob* parameter of the imported New-Test cmdlet to run a New-Test command as a background job.</span></span>
<span data-ttu-id="15fe1-154">New-Test가 반환하는 작업 개체를 $batch 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-154">The command saves the job object that New-Test returns in the $batch variable.</span></span>

<span data-ttu-id="15fe1-155">네 번째 명령은 Receive-Job cmdlet을 사용 하 여 $batch 변수의 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-155">The fourth command uses the Receive-Job cmdlet to get the results of the job in the $batch variable.</span></span>

### <span data-ttu-id="15fe1-156">예 5: PowerShell 모듈에서 cmdlet 및 함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="15fe1-156">Example 5: Import cmdlets and functions from a PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="15fe1-157">이 예제에서는 원격 컴퓨터의 PowerShell 모듈에서 현재 세션으로 cmdlet 및 함수를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-157">This example shows how to import the cmdlets and functions from a PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="15fe1-158">첫 번째 명령은 Server01 컴퓨터에 PSSession을 만든 다음 $S 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-158">The first command creates a PSSession on the Server01 computer and saves it in the $S variable.</span></span>

<span data-ttu-id="15fe1-159">두 번째 명령은 **Invoke 명령** cmdlet을 사용 하 여 $S의 PSSession에서 Import-Module 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-159">The second command uses the **Invoke-Command** cmdlet to run an Import-Module command in the PSSession in $S.</span></span>

<span data-ttu-id="15fe1-160">일반적으로 모듈은 PowerShell 프로필의 **import-module** 명령으로 모든 세션에 추가 되지만 프로필은 pssession에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-160">Typically, the module would be added to all sessions by an **Import-Module** command in a PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="15fe1-161">세 번째 명령은 import-module의 *module*  매개 변수를 **사용 하 여** 모듈의 cmdlet 및 함수를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-161">The third command uses the *Module*  parameter of **Import-PSSession** to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="15fe1-162">예제 6: 임시 파일에 모듈 만들기</span><span class="sxs-lookup"><span data-stu-id="15fe1-162">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="15fe1-163">이 예제에서는 **Import-PSSession** 이 디스크의 임시 파일에 모듈을 만드는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-163">This example shows that **Import-PSSession** creates a module in a temporary file on disk.</span></span>
<span data-ttu-id="15fe1-164">또한 현재 세션으로 가져오기 전에 모든 명령이 함수로 변환됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-164">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="15fe1-165">이 명령은 **가져오기-PSSession** cmdlet을 사용 하 여 Get-Date Cmdlet 및 searchhelp 함수를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-165">The command uses the **Import-PSSession** cmdlet to import a Get-Date cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="15fe1-166">**Import-PSSession** cmdlet은 임시 모듈을 나타내는 **PSModuleInfo** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-166">The **Import-PSSession** cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span>
<span data-ttu-id="15fe1-167">**Path** 속성 값은 **Import-PSSession** 이 임시 위치에 스크립트 모듈(.psm1) 파일을 만들었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-167">The value of the **Path** property shows that **Import-PSSession** created a script module (.psm1) file in a temporary location.</span></span>
<span data-ttu-id="15fe1-168">**ExportedFunctions** 속성은 **Get-Date** cmdlet과 SearchHelp 함수를 둘 다 함수로 가져왔음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-168">The **ExportedFunctions** property shows that the **Get-Date** cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="15fe1-169">예 7: 가져온 명령에 의해 숨겨진 명령 실행</span><span class="sxs-lookup"><span data-stu-id="15fe1-169">Example 7: Run a command that is hidden by an imported command</span></span>

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

<span data-ttu-id="15fe1-170">이 예제에서는 가져온 명령에서 숨기는 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-170">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="15fe1-171">첫 번째 명령은 $S 변수의 PSSession에서 Get-Date cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-171">The first command imports a Get-Date cmdlet from the PSSession in the $S variable.</span></span>
<span data-ttu-id="15fe1-172">현재 세션에 **Get-Date** cmdlet이 포함되어 있으므로 명령에 *AllowClobber* 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-172">Because the current session includes a **Get-Date** cmdlet, the *AllowClobber* parameter is required in the command.</span></span>

<span data-ttu-id="15fe1-173">두 번째 명령은 Get-Command cmdlet의 **all** 매개 변수를 사용 하 여 현재 세션의 모든 **get Date** 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-173">The second command uses the **All** parameter of the Get-Command cmdlet to get all **Get-Date** commands in the current session.</span></span>
<span data-ttu-id="15fe1-174">출력은 세션에 원래 **Get-Date** cmdlet 및 **Get-Date** 함수가 포함되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-174">The output shows that the session includes the original **Get-Date** cmdlet and a **Get-Date** function.</span></span>
<span data-ttu-id="15fe1-175">**Get date** 함수는 $S의 PSSession에서 가져온 **가져오기 날짜** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-175">The **Get-Date** function runs the imported **Get-Date** cmdlet in the PSSession in $S.</span></span>

<span data-ttu-id="15fe1-176">세 번째 명령은 **Get-Date** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-176">The third command runs a **Get-Date** command.</span></span>
<span data-ttu-id="15fe1-177">함수는 cmdlet 보다 우선적으로 사용 되므로 PowerShell에서 율리우스 날짜를 반환 하는 가져온 **가져오기 날짜** 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-177">Because functions take precedence over cmdlets, PowerShell runs the imported **Get-Date** function, which returns a Julian date.</span></span>

<span data-ttu-id="15fe1-178">네 번째 및 다섯 번째 명령은 가져온 명령에서 숨기는 명령을 실행하는 데 정규화된 이름을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-178">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="15fe1-179">네 번째 명령은 원래 **Get Date** cmdlet을 현재 세션에 추가 하는 PowerShell 스냅인의 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-179">The fourth command gets the name of the PowerShell snap-in that added the original **Get-Date** cmdlet to the current session.</span></span>

<span data-ttu-id="15fe1-180">다섯 번째 명령은 스냅인으로 정규화된 **Get-Date** cmdlet 이름을 사용하여 **Get-Date** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-180">The fifth command uses the snap-in-qualified name of the **Get-Date** cmdlet to run a **Get-Date** command.</span></span>

<span data-ttu-id="15fe1-181">명령 우선 순위 및 숨겨진 명령에 대한 자세한 내용은 about_Command_Precedence를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-181">For more information about command precedence and hidden commands, see about_Command_Precedence.</span></span>

### <span data-ttu-id="15fe1-182">예 8: 이름에 특정 문자열이 있는 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="15fe1-182">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName *Item* -AllowClobber
```

<span data-ttu-id="15fe1-183">이 명령은 $S의 PSSession에 있는 항목의 이름을 포함 하는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-183">This command imports commands whose names include Item from the PSSession in $S.</span></span>
<span data-ttu-id="15fe1-184">명령에는 *CommandName* 매개 변수는 포함 되지만 *FormatTypeData* 매개 변수는 포함 되어 있지 않으므로 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-184">Because the command includes the *CommandName* parameter but not the *FormatTypeData* parameter, only the command is imported.</span></span>

<span data-ttu-id="15fe1-185">**Import-PSSession** 을 사용하여 원격 컴퓨터에서 명령을 실행하며 현재 세션의 명령에 대한 형식 지정 데이터가 이미 있을 경우 이 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-185">Use this command when you are using **Import-PSSession** to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="15fe1-186">예 9: Module 매개 변수를 사용 하 여 세션으로 가져온 명령 검색</span><span class="sxs-lookup"><span data-stu-id="15fe1-186">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

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

<span data-ttu-id="15fe1-187">이 명령은 **Get 명령의** *Module* 매개 변수를 사용 하 여 **가져오기 PSSession** 명령에 의해 세션으로 가져온 명령을 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-187">This command shows how to use the *Module* parameter of **Get-Command** to find out which commands were imported into the session by an **Import-PSSession** command.</span></span>

<span data-ttu-id="15fe1-188">첫 번째 명령은 **import-module** cmdlet을 사용 하 여 이름이 $S 변수의 PSSession에서 "bits"를 포함 하는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-188">The first command uses the **Import-PSSession** cmdlet to import commands whose names include "bits" from the PSSession in the $S variable.</span></span>
<span data-ttu-id="15fe1-189">**Import-PSSession** 명령은 임시 모듈을 반환하고 $m 변수에 모듈을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-189">The **Import-PSSession** command returns a temporary module, and the command saves the module in the $m variable.</span></span>

<span data-ttu-id="15fe1-190">두 번째 명령은 Get-Command cmdlet을 사용 하 여 $M 변수에 모듈에서 내보낸 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-190">The second command uses the Get-Command cmdlet to get the commands that are exported by the module in the $M variable.</span></span>

<span data-ttu-id="15fe1-191">*Module* 매개 변수는 모듈 이름에 사용되는 문자열 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-191">The *Module* parameter takes a string value, which is designed for the module name.</span></span>
<span data-ttu-id="15fe1-192">그러나 모듈 개체를 제출 하는 경우 PowerShell은 모듈 개체에서 **ToString** 메서드를 사용 하 여 모듈 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-192">However, when you submit a module object, PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="15fe1-193">**Get 명령** 명령은 "와 동일 합니다 `Get-Command $M.Name` .</span><span class="sxs-lookup"><span data-stu-id="15fe1-193">The **Get-Command** command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="15fe1-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="15fe1-194">PARAMETERS</span></span>

### <span data-ttu-id="15fe1-195">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="15fe1-195">-AllowClobber</span></span>

<span data-ttu-id="15fe1-196">현재 세션에 있는 명령과 이름이 동일한 경우에도이 cmdlet이 지정 된 명령을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-196">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="15fe1-197">현재 세션에 있는 명령과 이름이 같은 명령을 가져오는 경우 가져온 명령이 원래 명령을 숨기거나 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-197">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span>
<span data-ttu-id="15fe1-198">자세한 내용은 about_Command_Precedence를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-198">For more information, see about_Command_Precedence.</span></span>

<span data-ttu-id="15fe1-199">기본적으로 **Import-PSSession** 은 현재 세션에 있는 명령과 이름이 같은 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-199">By default, **Import-PSSession** does not import commands that have the same name as commands in the current session.</span></span>

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

### <span data-ttu-id="15fe1-200">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="15fe1-200">-ArgumentList</span></span>

<span data-ttu-id="15fe1-201">지정 된 인수 (매개 변수 값)를 사용 하 여 생성 되는 명령 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-201">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="15fe1-202">예를 들어 인증서 (Cert:)에서 Get-Item 명령의 변형을 가져오려면 $S의 PSSession에 있는 드라이브를 입력 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-202">For instance, to import the variant of the Get-Item command in the certificate (Cert:) drive in the PSSession in $S, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="15fe1-203">-인증서</span><span class="sxs-lookup"><span data-stu-id="15fe1-203">-Certificate</span></span>

<span data-ttu-id="15fe1-204">**Import-PSSession** 에서 만드는 임시 모듈의 형식 파일(\*.Format.ps1xml) 또는 스크립트 모듈 파일(.psm1)에 서명하는 데 사용되는 클라이언트 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-204">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that **Import-PSSession** creates.</span></span>

<span data-ttu-id="15fe1-205">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-205">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="15fe1-206">인증서를 찾으려면 Get-PfxCertificate cmdlet을 사용 하거나 인증서 (Cert:)에서 Get-ChildItem cmdlet을 사용 합니다. 드라이브나.</span><span class="sxs-lookup"><span data-stu-id="15fe1-206">To find a certificate, use the Get-PfxCertificate cmdlet or use the Get-ChildItem cmdlet in the Certificate (Cert:) drive.</span></span>
<span data-ttu-id="15fe1-207">인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-207">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="15fe1-208">-CommandName</span><span class="sxs-lookup"><span data-stu-id="15fe1-208">-CommandName</span></span>

<span data-ttu-id="15fe1-209">지정 된 이름이 나 이름 패턴을 사용 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-209">Specifies commands with the specified names or name patterns.</span></span>
<span data-ttu-id="15fe1-210">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-210">Wildcards are permitted.</span></span>
<span data-ttu-id="15fe1-211">*CommandName* 또는 별칭, *이름* 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-211">Use *CommandName* or its alias, *Name* .</span></span>

<span data-ttu-id="15fe1-212">기본적으로 **Import-PSSession** 은 현재 세션에 있는 명령과 이름이 같은 명령을 제외한 모든 명령을 세션에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-212">By default, **Import-PSSession** imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="15fe1-213">이렇게 하면 가져온 명령이 세션의 명령을 숨기거나 바꾸지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-213">This prevents imported commands from hiding or replacing commands in the session.</span></span>
<span data-ttu-id="15fe1-214">다른 명령을 숨기거나 바꾸는 명령을 포함하여 모든 명령을 가져오려면 *AllowClobber* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-214">To import all commands, even those that hide or replace other commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="15fe1-215">*CommandName* 매개 변수를 사용 하는 경우 *formattypename* 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-215">If you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>
<span data-ttu-id="15fe1-216">마찬가지로, *FormatTypeName* 매개 변수를 사용할 경우 *CommandName* 매개 변수를 사용하지 않으면 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-216">Similarly, if you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

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

### <span data-ttu-id="15fe1-217">-CommandType</span><span class="sxs-lookup"><span data-stu-id="15fe1-217">-CommandType</span></span>

<span data-ttu-id="15fe1-218">명령 개체의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-218">Specifies the type of command objects.</span></span>
<span data-ttu-id="15fe1-219">기본값은 Cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-219">The default value is Cmdlet.</span></span>
<span data-ttu-id="15fe1-220">*CommandType* 또는 별칭 *Type* 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-220">Use *CommandType* or its alias, *Type* .</span></span>
<span data-ttu-id="15fe1-221">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="15fe1-222">앤티앨리어스.</span><span class="sxs-lookup"><span data-stu-id="15fe1-222">Alias.</span></span>
<span data-ttu-id="15fe1-223">원격 세션의 PowerShell 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-223">The PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="15fe1-224">모두.</span><span class="sxs-lookup"><span data-stu-id="15fe1-224">All.</span></span>
<span data-ttu-id="15fe1-225">원격 세션에 있는 cmdlet 및 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-225">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="15fe1-226">애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-226">Application.</span></span>
<span data-ttu-id="15fe1-227">Path 환경 변수 ($env:p a)에 나열 된 경로에 있는 모든 파일 (.txt, .exe 및 .dll 파일 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-227">All the files other than PowerShell files in the paths that are listed in the Path environment variable ($env:path) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="15fe1-228">#A0.</span><span class="sxs-lookup"><span data-stu-id="15fe1-228">Cmdlet.</span></span>
<span data-ttu-id="15fe1-229">원격 세션에 있는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-229">The cmdlets in the remote session.</span></span>
<span data-ttu-id="15fe1-230">기본값은 "Cmdlet"입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-230">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="15fe1-231">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="15fe1-231">ExternalScript.</span></span>
<span data-ttu-id="15fe1-232">원격 세션의 Path 환경 변수($env:path)에 나열된 경로에 있는 .ps1 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-232">The .ps1 files in the paths listed in the Path environment variable ($env:path) in the remote session.</span></span>
- <span data-ttu-id="15fe1-233">필터 및 함수</span><span class="sxs-lookup"><span data-stu-id="15fe1-233">Filter and Function.</span></span>
<span data-ttu-id="15fe1-234">원격 세션의 PowerShell 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-234">The PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="15fe1-235">스크립트.</span><span class="sxs-lookup"><span data-stu-id="15fe1-235">Script.</span></span>
<span data-ttu-id="15fe1-236">원격 세션에 있는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-236">The script blocks in the remote session.</span></span>

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

### <span data-ttu-id="15fe1-237">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="15fe1-237">-DisableNameChecking</span></span>

<span data-ttu-id="15fe1-238">이 cmdlet은 이름에 승인 되지 않은 동사 나 금지 된 문자가 포함 된 cmdlet 또는 함수를 가져올 때 경고 메시지를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-238">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="15fe1-239">기본적으로 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 PowerShell은 다음 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-239">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the PowerShell displays the following warning message:</span></span>

<span data-ttu-id="15fe1-240">"경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-240">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span>
<span data-ttu-id="15fe1-241">자세한 내용을 보려면 Verbose 매개 변수를 사용하거나 승인된 동사 목록을 보려면 Get-Verb를 입력하세요."</span><span class="sxs-lookup"><span data-stu-id="15fe1-241">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs."</span></span>

<span data-ttu-id="15fe1-242">이 메시지는 경고일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-242">This message is only a warning.</span></span>
<span data-ttu-id="15fe1-243">비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-243">The complete module is still imported, including the non-conforming commands.</span></span>
<span data-ttu-id="15fe1-244">메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-244">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="15fe1-245">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="15fe1-245">-FormatTypeName</span></span>

<span data-ttu-id="15fe1-246">지정 된 Microsoft .NET Framework 형식에 대 한 형식 지정 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-246">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="15fe1-247">유형 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-247">Enter the type names.</span></span>
<span data-ttu-id="15fe1-248">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-248">Wildcards are permitted.</span></span>

<span data-ttu-id="15fe1-249">이 매개 변수 값은 명령을 가져오는 원본 세션의 Get-FormatData 명령에서 반환된 유형의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-249">The value of this parameter must be the name of a type that is returned by a Get-FormatData command in the session from which the commands are being imported.</span></span>
<span data-ttu-id="15fe1-250">원격 세션의 형식 지정 데이터를 모두 가져오려면 \*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-250">To get all of the formatting data in the remote session, type \*.</span></span>

<span data-ttu-id="15fe1-251">명령에 *CommandName* 또는 *formattypename* 매개 변수가 포함 되어 있지 않으면 **Import-module** 은 원격 세션의 **Get formattypename** 명령에서 반환 하는 모든 .NET Framework 형식에 대 한 형식 지정 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-251">If the command does not include either the *CommandName* or *FormatTypeName* parameter, **Import-PSSession** imports formatting instructions for all .NET Framework types returned by a **Get-FormatData** command in the remote session.</span></span>

<span data-ttu-id="15fe1-252">*FormatTypeName* 매개 변수를 사용할 경우 *CommandName* 매개 변수를 사용하지 않으면 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-252">If you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

<span data-ttu-id="15fe1-253">마찬가지로, *CommandName* 매개 변수를 사용 하는 경우 *formattypename* 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-253">Similarly, if you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>

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

### <span data-ttu-id="15fe1-254">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="15fe1-254">-FullyQualifiedModule</span></span>

<span data-ttu-id="15fe1-255">**ModuleSpecification** 개체 형식으로 지정 된 이름의 모듈을 지정 합니다 (MSDN 라이브러리의 [ModuleSpecification 생성자 (Hashtable)](https://msdn.microsoft.com/library/jj136290) 의 설명 섹션 참조).</span><span class="sxs-lookup"><span data-stu-id="15fe1-255">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library).</span></span>
<span data-ttu-id="15fe1-256">예를 들어 *변수인 fullyqualifiedmodule* 매개 변수는 @ {ModuleName = "ModuleName" 형식으로 지정 된 모듈 이름을 허용 합니다. ModuleVersion = "version_number"} 또는 @ {ModuleName = "ModuleName"; ModuleVersion = "version_number"; Guid = "GUID"}.</span><span class="sxs-lookup"><span data-stu-id="15fe1-256">For example, the *FullyQualifiedModule* parameter accepts a module name that is specified in the format @{ModuleName = "modulename"; ModuleVersion = "version_number"} or @{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.</span></span>
<span data-ttu-id="15fe1-257">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-257">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="15fe1-258">*모듈* 매개 변수와 동일한 명령에 *변수인 fullyqualifiedmodule* 매개 변수를 지정할 수 없습니다. 두 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-258">You cannot specify the *FullyQualifiedModule* parameter in the same command as a *Module* parameter; the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="15fe1-259">-모듈</span><span class="sxs-lookup"><span data-stu-id="15fe1-259">-Module</span></span>

<span data-ttu-id="15fe1-260">PowerShell 스냅인 및 모듈에서 명령의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-260">Specifies and array of commands in the PowerShell snap-ins and modules.</span></span>
<span data-ttu-id="15fe1-261">스냅인 및 모듈 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-261">Enter the snap-in and module names.</span></span>
<span data-ttu-id="15fe1-262">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-262">Wildcards are not permitted.</span></span>

<span data-ttu-id="15fe1-263">**가져오기-PSSession** 은 스냅인에서 공급자를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-263">**Import-PSSession** cannot import providers from a snap-in.</span></span>

<span data-ttu-id="15fe1-264">자세한 내용은 about_PSSnapins 및 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-264">For more information, see about_PSSnapins and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

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

### <span data-ttu-id="15fe1-265">-접두사</span><span class="sxs-lookup"><span data-stu-id="15fe1-265">-Prefix</span></span>

<span data-ttu-id="15fe1-266">가져온 명령 이름의 명사에 대 한 접두사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-266">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="15fe1-267">이 매개 변수를 사용하면 세션에 있는 서로 다른 명령의 이름이 같은 경우 발생할 수 있는 이름 충돌을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-267">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="15fe1-268">예를 들어, 접두사 원격을 지정 하 고 Get-Date cmdlet을 가져오는 경우이 cmdlet은 세션에서 Get RemoteDate로 알려져 있으며 원래 **Get date** cmdlet과는 혼동 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-268">For instance, if you specify the prefix Remote and then import a Get-Date cmdlet, the cmdlet is known in the session as Get-RemoteDate, and it is not confused with the original **Get-Date** cmdlet.</span></span>

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

### <span data-ttu-id="15fe1-269">-Session</span><span class="sxs-lookup"><span data-stu-id="15fe1-269">-Session</span></span>

<span data-ttu-id="15fe1-270">Cmdlet을 가져올 **PSSession** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-270">Specifies the **PSSession** from which the cmdlets are imported.</span></span>
<span data-ttu-id="15fe1-271">세션 개체를 포함 하는 변수를 입력 하거나 세션 개체를 가져오는 명령 (예: New-PSSession 또는 Get-PSSession 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-271">Enter a variable that contains a session object or a command that gets a session object, such as a New-PSSession or Get-PSSession command.</span></span>
<span data-ttu-id="15fe1-272">세션은 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-272">You can specify only one session.</span></span>
<span data-ttu-id="15fe1-273">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-273">This parameter is required.</span></span>

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

### <span data-ttu-id="15fe1-274">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15fe1-274">CommonParameters</span></span>

<span data-ttu-id="15fe1-275">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15fe1-275">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15fe1-276">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-276">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15fe1-277">입력</span><span class="sxs-lookup"><span data-stu-id="15fe1-277">INPUTS</span></span>

### <span data-ttu-id="15fe1-278">없음</span><span class="sxs-lookup"><span data-stu-id="15fe1-278">None</span></span>

<span data-ttu-id="15fe1-279">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-279">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="15fe1-280">출력</span><span class="sxs-lookup"><span data-stu-id="15fe1-280">OUTPUTS</span></span>

### <span data-ttu-id="15fe1-281">System.object..</span><span class="sxs-lookup"><span data-stu-id="15fe1-281">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="15fe1-282">**Import-module** 은 New-Module 및 Get-Module cmdlet이 반환 하는 것과 동일한 모듈 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-282">**Import-PSSession** returns the same module object that New-Module and Get-Module cmdlets return.</span></span>
<span data-ttu-id="15fe1-283">그러나 가져온 모듈은 임시 모듈이며 현재 세션에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-283">However, the imported module is temporary and exists only in the current session.</span></span>
<span data-ttu-id="15fe1-284">디스크에 영구 모듈을 만들려면 Export-PSSession cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-284">To create a permanent module on disk, use the Export-PSSession cmdlet.</span></span>

## <span data-ttu-id="15fe1-285">참고</span><span class="sxs-lookup"><span data-stu-id="15fe1-285">NOTES</span></span>

* <span data-ttu-id="15fe1-286">**가져오기-PSSession** 은 PowerShell 원격 인프라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-286">**Import-PSSession** relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="15fe1-287">이 cmdlet을 사용하려면 WS-Management 원격 기능을 사용하도록 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-287">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="15fe1-288">자세한 내용은 about_Remote 및 about_Remote_Requirements를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-288">For more information, see about_Remote and about_Remote_Requirements.</span></span>
* <span data-ttu-id="15fe1-289">**가져오기-PSSession** 은 변수 또는 PowerShell 공급자를 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-289">**Import-PSSession** does not import variables or PowerShell providers.</span></span>
* <span data-ttu-id="15fe1-290">현재 세션에 있는 명령과 이름이 같은 명령을 가져오는 경우 가져온 명령은 세션에 있는 별칭, 함수 및 cmdlet을 숨길 수 있으며 세션에 있는 함수 및 변수를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-290">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="15fe1-291">이름 충돌을 방지하려면 *Prefix* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-291">To prevent name conflicts, use the *Prefix* parameter.</span></span> <span data-ttu-id="15fe1-292">자세한 내용은 about_Command_Precedence를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-292">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="15fe1-293">**가져오기-PSSession은** 가져오기 전에 모든 명령을 함수로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-293">**Import-PSSession** converts all commands into functions before it imports them.</span></span> <span data-ttu-id="15fe1-294">그 결과 가져온 명령은 원래 명령 유형을 유지할 때의 동작과 다소 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-294">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="15fe1-295">예를 들어 PSSession에서 cmdlet을 가져온 다음 모듈 또는 스냅인에서 같은 이름의 cmdlet을 가져오는 경우 함수가 cmdlet보다 우선적으로 적용되기 때문에 항상 PSSession에서 가져온 cmdlet이 기본적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-295">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="15fe1-296">반대로 별칭을 같은 이름의 별칭이 있는 세션으로 가져오는 경우 별칭이 함수보다 우선적으로 적용되기 때문에 항상 원래 별칭이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-296">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="15fe1-297">자세한 내용은 about_Command_Precedence를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15fe1-297">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="15fe1-298">**가져오기-PSSession** 은 Write-Progress cmdlet을 사용 하 여 명령 진행률을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-298">**Import-PSSession** uses the Write-Progress cmdlet to display the progress of the command.</span></span> <span data-ttu-id="15fe1-299">명령이 실행되는 동안 진행률 표시줄을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-299">You might see the progress bar while the command is running.</span></span>
* <span data-ttu-id="15fe1-300">가져올 명령을 찾기 위해 **가져오기-pssession** 은 Invoke-Command cmdlet을 사용 하 여 PSSession에서 Get-Command 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-300">To find the commands to import, **Import-PSSession** uses the Invoke-Command cmdlet to run a Get-Command command in the PSSession.</span></span> <span data-ttu-id="15fe1-301">명령에 대 한 형식 지정 데이터를 가져오기 위해 Get-FormatData cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-301">To get formatting data for the commands, it uses the Get-FormatData cmdlet.</span></span> <span data-ttu-id="15fe1-302">이러한 cmdlet의 오류 메시지는 **가져오기-PSSession** 명령을 실행할 때 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-302">You might see error messages from these cmdlets when you run an **Import-PSSession** command.</span></span> <span data-ttu-id="15fe1-303">또한 **가져오기-pssession** 은 get 명령, Formatformatdata, Select-Object 및 Get-Help cmdlet이 포함 되지 않은 PSSession에서 명령을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-303">Also, **Import-PSSession** cannot import commands from a PSSession that does not include the Get-Command, Get-FormatData, Select-Object, and Get-Help cmdlets.</span></span>
* <span data-ttu-id="15fe1-304">가져온 명령의 경우 사용자 인터페이스를 통해 메모장 등의 프로그램을 시작할 수 없다는 점을 포함하여 다른 원격 명령과 동일한 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-304">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
* <span data-ttu-id="15fe1-305">PowerShell 프로필은 pssession에서 실행 되지 않으므로 프로필을 통해 세션에 추가 하는 명령은 **가져오기-PSSession** 에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-305">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to **Import-PSSession** .</span></span> <span data-ttu-id="15fe1-306">프로필에서 명령을 가져오려면 명령을 가져오기 전에 Invoke-Command 명령을 사용하여 PSSession에서 프로필을 수동으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-306">To import commands from a profile, use an Invoke-Command command to run the profile in the PSSession manually before importing commands.</span></span>
* <span data-ttu-id="15fe1-307">명령이 형식 지정 데이터를 가져오지 않아도 **Import-PSSession** 에서 만든 임시 모듈이 형식 지정 파일을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-307">The temporary module that **Import-PSSession** creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="15fe1-308">명령이 형식 지정 데이터를 가져오지 않는 경우 만든 형식 지정 파일에 형식 지정 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-308">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
* <span data-ttu-id="15fe1-309">**Import-PSSession** 을 사용하려면 현재 세션의 실행 정책이 Restricted 또는 AllSigned일 수 없습니다. **Import-PSSession** 에서 만든 임시 모듈이 이러한 정책에서 차단되는 서명되지 않은 스크립트 파일을 포함하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-309">To use **Import-PSSession** , the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that **Import-PSSession** creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="15fe1-310">로컬 컴퓨터에 대 한 실행 정책을 변경 하지 않고 **가져오기 PSSession** 을 사용 하려면 Set-ExecutionPolicy의 *Scope* 매개 변수를 사용 하 여 단일 프로세스에 대 한 덜 제한적인 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-310">To use **Import-PSSession** without changing the execution policy for the local computer, use the *Scope* parameter of Set-ExecutionPolicy to set a less restrictive execution policy for a single process.</span></span>
* <span data-ttu-id="15fe1-311">Windows PowerShell 2.0에서는 다른 세션에서 가져온 명령에 대한 도움말 항목에 *Prefix* 매개 변수를 사용하여 할당한 접두사가 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-311">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the *Prefix* parameter.</span></span> <span data-ttu-id="15fe1-312">Windows PowerShell 2.0에서 가져온 명령에 대한 도움말을 가져오려면 접두사가 없는 원래 명령 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15fe1-312">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="15fe1-313">관련 링크</span><span class="sxs-lookup"><span data-stu-id="15fe1-313">RELATED LINKS</span></span>

[<span data-ttu-id="15fe1-314">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="15fe1-314">Export-PSSession</span></span>](Export-PSSession.md)
