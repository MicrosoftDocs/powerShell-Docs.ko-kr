---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 5bc474883029f59eda199a5d93ef8a229c0f887e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389218"
---
# <span data-ttu-id="7f214-103">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f214-103">Export-PSSession</span></span>

## <span data-ttu-id="7f214-104">개요</span><span class="sxs-lookup"><span data-stu-id="7f214-104">SYNOPSIS</span></span>

<span data-ttu-id="7f214-105">다른 세션에서 명령을 내보내고 PowerShell 모듈에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-105">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="7f214-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f214-106">SYNTAX</span></span>

### <span data-ttu-id="7f214-107">모두</span><span class="sxs-lookup"><span data-stu-id="7f214-107">All</span></span>

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## <span data-ttu-id="7f214-108">설명</span><span class="sxs-lookup"><span data-stu-id="7f214-108">DESCRIPTION</span></span>

<span data-ttu-id="7f214-109">`Export-PSSession`Cmdlet은 로컬 또는 원격 컴퓨터의 다른 PowerShell 세션 (PSSession)에서 cmdlet, 함수, 별칭 및 기타 명령 유형을 가져온 후 PowerShell 모듈에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-109">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="7f214-110">모듈의 명령을 현재 세션에 추가 하려면 cmdlet을 사용 `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-110">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="7f214-111">`Import-PSSession`다른 PSSession의 명령을 현재 세션으로 가져오는와 달리는 `Export-PSSession` 모듈에 명령을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-111">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="7f214-112">현재 세션으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-112">The commands are not imported into the current session.</span></span>

<span data-ttu-id="7f214-113">명령을 내보내려면 cmdlet을 사용 `New-PSSession` 하 여 내보낼 명령이 포함 된 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-113">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="7f214-114">그런 다음 cmdlet을 사용 `Export-PSSession` 하 여 명령을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-114">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="7f214-115">명령 이름 충돌을 방지 하기 위해의 기본값은 `Export-PSSession` 현재 세션에 있는 명령을 제외한 모든 명령을 내보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-115">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="7f214-116">**CommandName** 매개 변수를 사용 하 여 내보낼 명령을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-116">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="7f214-117">`Export-PSSession`Cmdlet은 PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-117">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="7f214-118">명령을 현재 세션으로 가져올 때 원래 세션이 나 원래 컴퓨터의 유사한 세션에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-118">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="7f214-119">예제</span><span class="sxs-lookup"><span data-stu-id="7f214-119">EXAMPLES</span></span>

### <span data-ttu-id="7f214-120">예제 1: PSSession에서 명령 내보내기</span><span class="sxs-lookup"><span data-stu-id="7f214-120">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="7f214-121">이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 새 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-121">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="7f214-122">현재 세션에 있는 명령을 제외한 모든 명령을 로컬 컴퓨터의 Server01 라는 모듈로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-122">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="7f214-123">내보내기에는 명령에 대 한 형식 지정 데이터가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-123">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="7f214-124">`New-PSSession`명령은 Server01 컴퓨터에 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-124">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="7f214-125">PSSession은 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="7f214-125">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="7f214-126">`Export-PSSession`명령은 `$S` 변수의 명령과 형식 지정 데이터를 Server01 모듈로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-126">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="7f214-127">예제 2: Get 및 Set 명령 내보내기</span><span class="sxs-lookup"><span data-stu-id="7f214-127">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="7f214-128">이 예에서는 `Get` `Set` 서버에서 및 명령을 모두 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-128">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="7f214-129">이러한 명령은 `Get` `Set` 원격 컴퓨터에 있는 Microsoft exchange Server 스냅인의 및 명령을 `$PSHOME\Modules` 로컬 컴퓨터의 디렉터리에 있는 Exchange 모듈로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-129">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="7f214-130">모듈을 디렉터리에 배치 `$PSHOME\Modules` 하면 컴퓨터의 모든 사용자가 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-130">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="7f214-131">예 3: 원격 컴퓨터에서 명령 내보내기</span><span class="sxs-lookup"><span data-stu-id="7f214-131">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="7f214-132">이 예제에서는 원격 컴퓨터의 PSSession에서 cmdlet을 내보내 로컬 컴퓨터의 모듈에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-132">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="7f214-133">모듈의 cmdlet을 사용할 수 있도록 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-133">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="7f214-134">`New-PSSession`이 명령은 Server01 컴퓨터에 PSSession을 만들어 변수에 저장 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="7f214-134">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="7f214-135">`Export-PSSession`명령은의 PSSession에서 이름이 테스트로 시작 하는 cmdlet을 `$S` 로컬 컴퓨터의 testcmdlets 모듈로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-135">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="7f214-136">`Remove-PSSession`Cmdlet은 `$S` 현재 세션에서 PSSession을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-136">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="7f214-137">이 명령은 세션에서 가져온 명령을 사용 하기 위해 PSSession이 활성화 되지 않아도 됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-137">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="7f214-138">`Import-Module`Cmdlet은 testcmdlets 모듈의 cmdlet을 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-138">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="7f214-139">언제 든 지 모든 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-139">The command can be run in any session at any time.</span></span>

<span data-ttu-id="7f214-140">`Get-Help`Cmdlet은 이름이 Test로 시작 하는 cmdlet에 대 한 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-140">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="7f214-141">모듈의 명령이 현재 세션에 추가 된 후에는 및 cmdlet을 사용 하 여 `Get-Help` `Get-Command` 가져온 명령에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-141">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="7f214-142">`Test-Files`Cmdlet을 Server01 컴퓨터에서 내보낸 후 세션에 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-142">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="7f214-143">`Test-Files`Cmdlet은 명령을 가져온 컴퓨터의 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-143">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="7f214-144">PowerShell은 TestCmdlets 모듈에 저장 된 정보를 통해 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-144">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="7f214-145">예 4: 현재 세션의 Export 및 변경이 명령</span><span class="sxs-lookup"><span data-stu-id="7f214-145">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="7f214-146">이 예에서는 변수에 저장 된 명령을 현재 세션으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-146">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="7f214-147">이 `Export-PSSession` 명령은 변수의 PSSession에 있는 모든 명령과 형식 지정 데이터를 `$S` 현재 세션으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-147">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="7f214-148">**AllowClobber** 매개 변수는 현재 세션에 있는 명령과 이름이 같은 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-148">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="7f214-149">예 5: 닫힌 PSSession에서 명령 내보내기</span><span class="sxs-lookup"><span data-stu-id="7f214-149">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="7f214-150">이 예제에서는 내보낸 명령을 만든 PSSession을 닫을 때 특별 한 옵션을 사용 하 여 내보낸 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-150">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="7f214-151">모듈을 가져올 때 원래 원격 세션이 닫히면 모듈은 원래 컴퓨터에 연결 되는 열려 있는 원격 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-151">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="7f214-152">원본 컴퓨터에 대 한 현재 세션이 없는 경우 모듈은 세션을 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-152">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="7f214-153">원격 세션에서 특수 한 옵션을 사용 하 여 내보낸 명령을 실행 하려면 모듈을 가져오기 전에 이러한 옵션으로 원격 세션을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-153">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="7f214-154">Cmdlet에 `New-PSSession` **sessionoption** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-154">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="7f214-155">`New-PSSessionOption`Cmdlet은 **Pssessionoption** 개체를 만든 다음이 개체를 `$Options` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-155">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="7f214-156">`New-PSSession`명령은 Server01 컴퓨터에 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-156">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="7f214-157">**Sessionoption** 매개 변수는에 저장 된 개체를 사용 합니다 `$Options` .</span><span class="sxs-lookup"><span data-stu-id="7f214-157">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="7f214-158">세션은 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="7f214-158">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="7f214-159">`Export-PSSession`Cmdlet은의 PSSession에서 `$S` Server01 모듈로 명령을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-159">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="7f214-160">`Remove-PSSession`Cmdlet은 변수의 PSSession을 삭제 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="7f214-160">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="7f214-161">`New-PSSession`Cmdlet은 Server01 컴퓨터에 연결 하는 새 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-161">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="7f214-162">**Sessionoption** 매개 변수는에 저장 된 개체를 사용 합니다 `$Options` .</span><span class="sxs-lookup"><span data-stu-id="7f214-162">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="7f214-163">`Import-Module`Cmdlet은 Server01 모듈에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-163">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="7f214-164">모듈의 명령은 Server01 컴퓨터의 PSSession에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-164">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="7f214-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7f214-165">PARAMETERS</span></span>

### <span data-ttu-id="7f214-166">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="7f214-166">-AllowClobber</span></span>

<span data-ttu-id="7f214-167">현재 세션에 있는 명령과 이름이 같더라도 지정한 명령을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-167">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="7f214-168">현재 세션에 있는 명령과 이름이 같은 명령을 내보내는 경우 내보낸 명령은 원래 명령을 숨기 거 나 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-168">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="7f214-169">자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-169">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="7f214-170">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="7f214-170">-ArgumentList</span></span>

<span data-ttu-id="7f214-171">지정한 인수(매개 변수 값)를 사용하여 생성된 명령 변형을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-171">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="7f214-172">예를 들어 `Get-Item` 인증서 (Cert:)에서 명령의 변형을 내보내려면 드라이브의 PSSession에 `$S` 를 입력 `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-172">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="7f214-173">-인증서</span><span class="sxs-lookup"><span data-stu-id="7f214-173">-Certificate</span></span>

<span data-ttu-id="7f214-174">에서 만드는 모듈의 형식 파일 (\* .Format.ps1xml) 또는 스크립트 모듈 파일 (. .psm1)에 서명 하는 데 사용 되는 클라이언트 인증서를 지정 합니다 `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f214-174">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="7f214-175">인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-175">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="7f214-176">인증서를 찾으려면 cmdlet을 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 (Cert:)에서 cmdlet을 사용 합니다. 드라이브나.</span><span class="sxs-lookup"><span data-stu-id="7f214-176">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="7f214-177">인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-177">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="7f214-178">-CommandName</span><span class="sxs-lookup"><span data-stu-id="7f214-178">-CommandName</span></span>

<span data-ttu-id="7f214-179">지정한 이름 또는 이름 패턴을 가진 명령만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-179">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="7f214-180">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-180">Wildcards are permitted.</span></span> <span data-ttu-id="7f214-181">**CommandName** 또는 별칭, **이름** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-181">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="7f214-182">기본적으로는 `Export-PSSession` 현재 세션에 있는 명령과 이름이 같은 명령을 제외한 모든 명령을 PSSession에서 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-182">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="7f214-183">그러면 명령이 현재 세션의 명령으로 숨겨지거나 대체 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-183">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="7f214-184">다른 명령을 숨기 거 나 바꾸는 명령을 포함 하 여 모든 명령을 내보내려면 **AllowClobber** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-184">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="7f214-185">**CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-185">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="7f214-186">마찬가지로, **Formattypename** 매개 변수를 사용 하는 경우 **CommandName** 매개 변수를 사용 하지 않으면 명령을 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-186">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7f214-187">-CommandType</span><span class="sxs-lookup"><span data-stu-id="7f214-187">-CommandType</span></span>

<span data-ttu-id="7f214-188">지정한 유형의 명령 개체만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-188">Exports only the specified types of command objects.</span></span> <span data-ttu-id="7f214-189">**CommandType** 또는 별칭 **Type** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-189">Use **CommandType** or its alias, **Type**.</span></span>

<span data-ttu-id="7f214-190">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-190">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="7f214-191">앤티앨리어스.</span><span class="sxs-lookup"><span data-stu-id="7f214-191">Alias.</span></span> <span data-ttu-id="7f214-192">현재 세션의 모든 PowerShell 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-192">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="7f214-193">모두.</span><span class="sxs-lookup"><span data-stu-id="7f214-193">All.</span></span> <span data-ttu-id="7f214-194">모든 명령 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-194">All command types.</span></span> <span data-ttu-id="7f214-195">와 동일 합니다 `Get-Command -Name *` .</span><span class="sxs-lookup"><span data-stu-id="7f214-195">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="7f214-196">애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-196">Application.</span></span> <span data-ttu-id="7f214-197">`$env:path`.Txt, .exe 및 .dll 파일을 비롯 하 여 Path 환경 변수 ()에 나열 된 경로에 있는 PowerShell 파일 이외의 모든 파일</span><span class="sxs-lookup"><span data-stu-id="7f214-197">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="7f214-198">#A0.</span><span class="sxs-lookup"><span data-stu-id="7f214-198">Cmdlet.</span></span> <span data-ttu-id="7f214-199">현재 세션에 있는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-199">The cmdlets in the current session.</span></span> <span data-ttu-id="7f214-200">기본값은 Cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-200">Cmdlet is the default.</span></span>
- <span data-ttu-id="7f214-201">구성</span><span class="sxs-lookup"><span data-stu-id="7f214-201">Configuration.</span></span> <span data-ttu-id="7f214-202">PowerShell 구성.</span><span class="sxs-lookup"><span data-stu-id="7f214-202">A PowerShell configuration.</span></span> <span data-ttu-id="7f214-203">자세한 내용은 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-203">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="7f214-204">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="7f214-204">ExternalScript.</span></span> <span data-ttu-id="7f214-205">Path 환경 변수 ()에 나열 된 경로에 있는 모든 ps1 파일 `$env:path`</span><span class="sxs-lookup"><span data-stu-id="7f214-205">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="7f214-206">필터 및 함수</span><span class="sxs-lookup"><span data-stu-id="7f214-206">Filter and Function.</span></span> <span data-ttu-id="7f214-207">모든 PowerShell 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-207">All PowerShell functions.</span></span>
- <span data-ttu-id="7f214-208">스크립트.</span><span class="sxs-lookup"><span data-stu-id="7f214-208">Script.</span></span> <span data-ttu-id="7f214-209">현재 세션에 있는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-209">Script blocks in the current session.</span></span>
- <span data-ttu-id="7f214-210">워크플로.</span><span class="sxs-lookup"><span data-stu-id="7f214-210">Workflow.</span></span> <span data-ttu-id="7f214-211">PowerShell 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-211">A PowerShell workflow.</span></span> <span data-ttu-id="7f214-212">자세한 내용은 [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-212">For more information, see [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows.md).</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f214-213">-Encoding</span><span class="sxs-lookup"><span data-stu-id="7f214-213">-Encoding</span></span>

<span data-ttu-id="7f214-214">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-214">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="7f214-215">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-215">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="7f214-216">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-216">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="7f214-217">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-217">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="7f214-218">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-218">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="7f214-219">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-219">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="7f214-220">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-220">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="7f214-221">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-221">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="7f214-222">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-222">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="7f214-223">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-223">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="7f214-224">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-224">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="7f214-225">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-225">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="7f214-226">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="7f214-226">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="7f214-227">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-227">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f214-228">-Force</span><span class="sxs-lookup"><span data-stu-id="7f214-228">-Force</span></span>

<span data-ttu-id="7f214-229">파일에 읽기 전용 특성이 있어도 하나 이상의 기존 출력 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-229">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="7f214-230">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="7f214-230">-FormatTypeName</span></span>

<span data-ttu-id="7f214-231">지정한 Microsoft .NET Framework 유형에 대한 형식 지정 명령만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-231">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="7f214-232">유형 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-232">Enter the type names.</span></span> <span data-ttu-id="7f214-233">기본적으로는 `Export-PSSession` **system.object** 네임 스페이스에 없는 모든 .NET Framework 형식에 대 한 형식 지정 명령을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-233">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="7f214-234">이 매개 변수 값은 `Get-FormatData` 명령을 가져올 세션의 명령에서 반환 하는 형식의 이름 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-234">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="7f214-235">원격 세션의 모든 형식 지정 데이터를 가져오려면를 입력 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-235">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="7f214-236">**Formattypename** 매개 변수를 사용 하는 경우 **CommandName** 매개 변수를 사용 하지 않으면 명령을 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-236">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="7f214-237">**CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-237">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

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

### <span data-ttu-id="7f214-238">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="7f214-238">-FullyQualifiedModule</span></span>

<span data-ttu-id="7f214-239">**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-239">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="7f214-240">[ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-240">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="7f214-241">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-241">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="7f214-242">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-242">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="7f214-243">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-243">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="7f214-244">두 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-244">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="7f214-245">-모듈</span><span class="sxs-lookup"><span data-stu-id="7f214-245">-Module</span></span>

<span data-ttu-id="7f214-246">지정 된 PowerShell 스냅인 및 모듈의 명령만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-246">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="7f214-247">스냅인 및 모듈 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-247">Enter the snap-in and module names.</span></span> <span data-ttu-id="7f214-248">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-248">Wildcards are not permitted.</span></span>

<span data-ttu-id="7f214-249">자세한 내용은 `Import-Module` 및 [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-249">For more information, see `Import-Module` and [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f214-250">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="7f214-250">-OutputModule</span></span>

<span data-ttu-id="7f214-251">에서 만든 모듈의 선택적 경로와 이름을 지정 합니다 `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f214-251">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="7f214-252">기본 경로는 `$home\Documents\WindowsPowerShell\Modules`입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-252">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="7f214-253">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-253">This parameter is required.</span></span>

<span data-ttu-id="7f214-254">모듈 하위 디렉터리 또는를 만드는 파일이 이미 있는 경우 `Export-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-254">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="7f214-255">기존 파일을 덮어쓰려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-255">To overwrite existing files, use the **Force** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f214-256">-Session</span><span class="sxs-lookup"><span data-stu-id="7f214-256">-Session</span></span>

<span data-ttu-id="7f214-257">명령을 내보낼 원본 PSSession을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-257">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="7f214-258">세션 개체 또는 세션 개체를 가져오는 명령 (예: 명령)을 포함 하는 변수를 입력 `Get-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-258">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="7f214-259">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-259">This parameter is required.</span></span>

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

### <span data-ttu-id="7f214-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f214-260">CommonParameters</span></span>

<span data-ttu-id="7f214-261">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f214-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f214-262">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f214-263">입력</span><span class="sxs-lookup"><span data-stu-id="7f214-263">INPUTS</span></span>

### <span data-ttu-id="7f214-264">없음</span><span class="sxs-lookup"><span data-stu-id="7f214-264">None</span></span>

<span data-ttu-id="7f214-265">개체를에 연결할 수 없습니다 `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f214-265">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="7f214-266">출력</span><span class="sxs-lookup"><span data-stu-id="7f214-266">OUTPUTS</span></span>

### <span data-ttu-id="7f214-267">System.object</span><span class="sxs-lookup"><span data-stu-id="7f214-267">System.IO.FileInfo</span></span>

<span data-ttu-id="7f214-268">`Export-PSSession` 만든 모듈을 구성 하는 파일 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-268">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="7f214-269">참고</span><span class="sxs-lookup"><span data-stu-id="7f214-269">NOTES</span></span>

<span data-ttu-id="7f214-270">`Export-PSSession` 은 PowerShell 원격 인프라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-270">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="7f214-271">이 cmdlet을 사용하려면 원격 기능을 사용하도록 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-271">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="7f214-272">자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f214-272">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="7f214-273">`Export-PSSession`를 사용 하 여 PowerShell 공급자를 내보낼 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-273">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="7f214-274">내보낸 명령은 명령을 내보낸 원본 PSSession에서 암시적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-274">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="7f214-275">원격으로 명령을 실행 하는 방법에 대 한 자세한 내용은 PowerShell에서 전체적으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-275">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="7f214-276">내보낸 명령은 로컬 명령과 동일한 방식으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-276">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="7f214-277">`Export-ModuleMember` 내보내는 모듈에서 PSSession에 대 한 정보를 캡처하고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-277">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="7f214-278">모듈을 가져올 때 명령이 내보내진 PSSession이 닫혀 있고 동일한 컴퓨터에 대 한 활성 PSSession이 없을 경우 모듈의 명령에서 PSSession을 다시 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-278">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="7f214-279">PSSession을 다시 만들지 못한 경우 내보낸 명령이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-279">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="7f214-280">모듈에서 캡처 및 저장 하는 세션 정보에는 `Export-ModuleMember` `$PSSessionOption` 기본 설정 변수에 지정 하거나, 또는 Cmdlet의 **sessionoption** 매개 변수를 사용 하는 것과 같은 세션 옵션이 포함 되어 있지 않습니다 `New-PSSession` `Enter-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="7f214-280">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="7f214-281">모듈을 가져올 때 원본 PSSession이 닫혀 있을 경우 모듈은 동일한 컴퓨터에 대한 다른 PSSession을 사용합니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="7f214-281">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="7f214-282">가져온 명령을 올바르게 구성된 세션에서 실행하려면 모듈을 가져오기 전에 원하는 옵션으로 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-282">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="7f214-283">내보낼 명령을 찾기 위해는 cmdlet을 `Export-PSSession` 사용 하 여 `Invoke-Command` `Get-Command` PSSession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-283">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="7f214-284">명령에 대 한 형식 지정 데이터를 가져오고 저장 하기 위해 `Get-FormatData` 및 cmdlet을 사용 `Export-FormatData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-284">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="7f214-285">`Invoke-Command` `Get-Command` `Get-FormatData` 명령을 실행할 때,, 및의 `Export-FormatData` 오류 메시지가 표시 될 수 있습니다 `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f214-285">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="7f214-286">또한는,, `Export-PSSession` 및 cmdlet을 포함 하지 않는 세션에서 명령을 내보낼 수 없습니다 `Get-Command` `Get-FormatData` `Select-Object` `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="7f214-286">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="7f214-287">`Export-PSSession` cmdlet을 사용 하 여 `Write-Progress` 명령 진행률을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-287">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="7f214-288">명령이 실행되는 동안 진행률 표시줄을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-288">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="7f214-289">내보낸 명령의 경우 사용자 인터페이스를 통해 메모장 등의 프로그램을 시작할 수 없다는 점을 포함하여 다른 원격 명령과 동일한 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-289">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="7f214-290">PowerShell 프로필은 pssession에서 실행 되지 않으므로 프로필을 통해 세션에 추가 하는 명령은에서 사용할 수 없습니다 `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f214-290">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="7f214-291">프로필에서 명령을 내보내려면 명령을 사용 하 여 명령을 `Invoke-Command` 내보내기 전에 PSSession에서 프로필을 수동으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-291">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="7f214-292">`Export-PSSession`명령에서 형식 지정 데이터를 가져오지 않는 경우에도에서 만드는 모듈에 서식 파일이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-292">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="7f214-293">명령이 형식 지정 데이터를 가져오지 않는 경우 만든 형식 지정 파일에 형식 지정 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f214-293">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="7f214-294">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7f214-294">RELATED LINKS</span></span>

[<span data-ttu-id="7f214-295">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="7f214-295">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="7f214-296">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="7f214-296">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="7f214-297">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="7f214-297">about_PSSnapins</span></span>](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[<span data-ttu-id="7f214-298">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="7f214-298">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="7f214-299">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="7f214-299">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="7f214-300">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f214-300">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="7f214-301">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7f214-301">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="7f214-302">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f214-302">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="7f214-303">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="7f214-303">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="7f214-304">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f214-304">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)
