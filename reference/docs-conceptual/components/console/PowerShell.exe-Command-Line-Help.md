---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 명령줄 도움말
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402460"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="964b5-103">PowerShell.exe 명령줄 도움말</span><span class="sxs-lookup"><span data-stu-id="964b5-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="964b5-104">PowerShell.exe를 사용하여 Cmd.exe와 같은 다른 도구의 명령줄에서 PowerShell 세션을 시작하거나, PowerShell 명령줄에서 사용하여 새 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="964b5-105">매개 변수를 사용하여 세션을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="964b5-106">구문</span><span class="sxs-lookup"><span data-stu-id="964b5-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="964b5-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="964b5-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="964b5-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="964b5-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="964b5-109">명령의 Base 64로 인코드된 문자열 버전을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="964b5-110">이 매개 변수를 사용하여 명령을 큰따옴표 또는 중괄호가 필요한 PowerShell로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="964b5-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="964b5-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="964b5-112">현재 세션에 대한 기본 실행 정책을 설정하고 $env:PSExecutionPolicyPreference 환경 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="964b5-113">이 매개 변수는 레지스트리에 설정된 PowerShell 실행 정책을 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="964b5-114">유효한 값 목록을 비롯한 PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="964b5-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="964b5-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="964b5-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="964b5-116">스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있도록 지정한 스크립트를 로컬 범위("dot-sourced")에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="964b5-117">스크립트 파일의 경로와 매개 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="964b5-118">**File**은 명령의 마지막 매개 변수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="964b5-119">**-File** 매개 변수 다음에 입력하는 모든 값은 해당 스크립트에 전달되는 스크립트 파일 경로 및 매개 변수로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="964b5-120">스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후).</span><span class="sxs-lookup"><span data-stu-id="964b5-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="964b5-121">예를 들어 cmd.exe에 하는 환경 변수 값을 전달 하려는 경우 cmd.exe 구문을 사용 합니다. `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="964b5-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="964b5-122">이와 달리 실행 `powershell.exe -File .\test.ps1 -TestParam $env:windir` 리터럴 문자열을 수신 하는 스크립트에서 cmd.exe `$env:windir` 현재 cmd.exe 셸에서에 특별 한 의미가 없으며 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="964b5-123">합니다 `$env:windir` 환경 변수 참조의 스타일 _수 있습니다_ 내에서 사용할 수는 `-Command` 매개 변수를 이후 있습니다 PowerShell 코드로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="964b5-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="964b5-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="964b5-125">PowerShell로 전송되는 데이터 형식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="964b5-126">유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="964b5-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="964b5-127">-Mta</span></span>

<span data-ttu-id="964b5-128">다중 스레드 아파트를 사용하여 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="964b5-129">이 매개 변수는 PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="964b5-130">PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="964b5-131">PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="964b5-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="964b5-132">-NoExit</span></span>

<span data-ttu-id="964b5-133">시작 명령을 실행한 후 종료하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="964b5-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="964b5-134">-NoLogo</span></span>

<span data-ttu-id="964b5-135">시작 시 저작권 배너를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="964b5-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="964b5-136">-NonInteractive</span></span>

<span data-ttu-id="964b5-137">사용자에게 대화형 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="964b5-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="964b5-138">-NoProfile</span></span>

<span data-ttu-id="964b5-139">PowerShell 프로필을 로드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="964b5-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="964b5-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="964b5-141">PowerShell의 출력 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="964b5-142">유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="964b5-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="964b5-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="964b5-144">지정된 PowerShell 콘솔 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="964b5-145">콘솔 파일의 경로와 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="964b5-146">콘솔 파일을 만들려면 PowerShell에서 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="964b5-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="964b5-147">-Sta</span></span>

<span data-ttu-id="964b5-148">단일 스레드 아파트를 사용하여 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="964b5-149">PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="964b5-150">PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="964b5-151">버전 <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="964b5-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="964b5-152">지정된 버전의 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="964b5-153">지정한 버전이 시스템에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="964b5-154">컴퓨터에 PowerShell 3.0이 설치되어 있는 경우 유효한 값은 "2.0"과 "3.0"입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="964b5-155">기본값은 "3.0"입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-155">The default value is "3.0".</span></span>

<span data-ttu-id="964b5-156">PowerShell 3.0이 설치되지 않은 경우 유효한 값은 "2.0"뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="964b5-157">다른 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-157">Other values are ignored.</span></span>

<span data-ttu-id="964b5-158">자세한 내용은 [Windows PowerShell 설치](../../setup/installing-windows-powershell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="964b5-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="964b5-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="964b5-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="964b5-160">세션에 대한 창 스타일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-160">Sets the window style for the session.</span></span> <span data-ttu-id="964b5-161">유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="964b5-162">-Command</span><span class="sxs-lookup"><span data-stu-id="964b5-162">-Command</span></span>

<span data-ttu-id="964b5-163">지정된 명령(및 매개 변수)을 PowerShell 명령 프롬프트에서 입력된 것처럼 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="964b5-164">를 실행 한 후 PowerShell 종료 하지 않으면 합니다 **NoExit** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="964b5-165">`-Command` 다음의 모든 텍스트는 PowerShell에 단일 명령줄로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="964b5-166">이것은 `-File`이 스크립트에 전송된 매개 변수를 처리하는 방식과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="964b5-167">변수의 `-Command` 수 "-", 문자열 또는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="964b5-168">명령의 결과를 라이브 개체가 아니라 deserialize 된 XML 개체로 부모 셸에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="964b5-169">경우 변수의 `-Command` 은 "-", 표준 입력에서 명령 텍스트를 읽어옵니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="964b5-170">경우 값 `-Command` 는 문자열인 **명령** _해야_ 명령 인수로 해석 됩니다 명령 뒤에 입력 한 문자가 때문에 지정 된 마지막 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="964b5-171">합니다 **명령** 전달 되는 값을 인식할 수 있는 경우 매개 변수 실행에 대 한 스크립트 블록에만 허용 `-Command` ScriptBlock 형식으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="964b5-172">이것이 _만_ 가능한 다른 PowerShell 호스트에서 PowerShell.exe를 실행 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="964b5-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="964b5-173">중괄호로 묶인 리터럴 스크립트 블록으로 형식 변수나 식에서 반환 되는 PowerShell에서 구문 분석 된 기존의 포함 될 수 있습니다 ScriptBlock 호스트 `{}`PowerShell.exe에 전달 되 고 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="964b5-174">Cmd.exe에 있는 것은 없습니다 스크립트 블록 (또는 ScriptBlock 형식)으로 하므로 전달 되는 값 **명령** 됩니다 _항상_ 문자열 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="964b5-175">문자열 내에서 스크립트 블록을 작성할 수 있지만 실행 되는 대신 동작 정확 하 게 일반적인 PowerShell 프롬프트에서 입력, 처럼 다시 할 차단 스크립트의 내용을 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="964b5-176">문자열을 전달 `-Command` 되므로 스크립트 블록 중괄호 대개 필요한 애초에 cmd.exe에서 실행 하는 경우 PowerShell로 실행 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="964b5-177">문자열 내에 정의 된 인라인 스크립트 블록을 실행 하는 [호출 연산자](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="964b5-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="964b5-178">-Help, -?, /?</span></span>

<span data-ttu-id="964b5-179">powershell.exe의 구문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="964b5-180">PowerShell에서 PowerShell.exe 명령을 입력하는 경우 명령 매개 변수 앞에 슬래시(/)가 아니라 하이픈(-)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="964b5-181">Cmd.exe에서는 하이픈 또는 슬래시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="964b5-182">문제 해결 참고: PowerShell 2.0에서 Windows powershell 콘솔에 실패 하면 일부 프로그램을 고 LastExitCode 0xc0000142가 표시 됩니다부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="964b5-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="964b5-183">예제</span><span class="sxs-lookup"><span data-stu-id="964b5-183">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
