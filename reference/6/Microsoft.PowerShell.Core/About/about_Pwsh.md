---
description: 명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `pwsh` . 명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.
keywords: powershell,cmdlet
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: 549c99fa618e2e53aed8945d95e92f97117aa6c9
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224657"
---
# <a name="about-pwsh"></a><span data-ttu-id="a68f7-105">Pwsh 정보</span><span class="sxs-lookup"><span data-stu-id="a68f7-105">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="a68f7-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a68f7-106">Short Description</span></span>
<span data-ttu-id="a68f7-107">명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-107">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="a68f7-108">명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="a68f7-109">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="a68f7-109">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="a68f7-110">구문</span><span class="sxs-lookup"><span data-stu-id="a68f7-110">Syntax</span></span>

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="a68f7-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a68f7-111">Parameters</span></span>

<span data-ttu-id="a68f7-112">모든 매개 변수는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-112">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="a68f7-113">-File | -f</span><span class="sxs-lookup"><span data-stu-id="a68f7-113">-File | -f</span></span>

<span data-ttu-id="a68f7-114">의 값이 이면 `File` `-` 표준 입력에서 명령 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-114">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="a68f7-115">`pwsh -File -`리디렉션된 표준 입력 없이 실행 하면 일반 세션이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-115">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="a68f7-116">이는 매개 변수를 지정 하지 않는 것과 같습니다 `File` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-116">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="a68f7-117">매개 변수가 없지만 명령줄에 값이 있는 경우이 매개 변수는 기본 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-117">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="a68f7-118">지정 된 스크립트는 로컬 범위 ("점 원본")에서 실행 되므로 스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-118">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="a68f7-119">스크립트 파일의 경로와 매개 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-119">Enter the script file path and any parameters.</span></span> <span data-ttu-id="a68f7-120">파일 매개 변수 이름 뒤에 입력 된 모든 문자는 스크립트 파일 경로 다음에 스크립트 매개 변수로 해석 되기 때문에 file은 명령의 마지막 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-120">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="a68f7-121">일반적으로 스크립트의 스위치 매개 변수는 포함되거나 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-121">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="a68f7-122">예를 들어 다음 명령은 Get-Script.ps1 스크립트 파일의 All 매개 변수를 사용 합니다. `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="a68f7-122">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="a68f7-123">드문 경우 지만 스위치 매개 변수에 대해 **부울** 값을 제공 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-123">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="a68f7-124">**File** 매개 변수의 값에 스위치 매개 변수에 대 한 **부울** 값을 제공 하려면 일반적으로 매개 변수를 즉시 콜론 및 부울 값 (예:)으로 사용 `-File .\Get-Script.ps1 -All:$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-124">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="a68f7-125">스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후).</span><span class="sxs-lookup"><span data-stu-id="a68f7-125">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="a68f7-126">예를 들어를 `cmd.exe` 사용 하 고 환경 변수 값을 전달 하려는 경우 `cmd.exe` 다음 구문을 사용 합니다. `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="a68f7-126">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="a68f7-127">이와 달리 `pwsh -File .\test.ps1 -TestParam $env:windir` 에서를 실행 하면 `cmd.exe` `$env:windir` 현재 셸에 대 한 특별 한 의미가 없기 때문에 스크립트에서 리터럴 문자열을 받습니다 `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-127">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="a68f7-128">`$env:windir`환경 변수 참조의 스타일은 PowerShell 코드로 해석 되기 때문에 **명령** 매개 변수 내에서 사용할 _수 있습니다_ .</span><span class="sxs-lookup"><span data-stu-id="a68f7-128">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="a68f7-129">마찬가지로 _일괄 처리 스크립트_ 에서 동일한 명령을 실행 하려는 경우 또는 대신를 사용 하 여 `%~dp0` `.\` `$PSScriptRoot` 현재 실행 디렉터리인를 나타냅니다 `pwsh -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-129">Similarly, if you want to execute the same command from a _Batch script_ , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="a68f7-130">대신를 사용 하는 경우 `.\test.ps1` 리터럴 경로를 찾을 수 없으므로 PowerShell에서 오류를 throw 합니다. `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="a68f7-130">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="a68f7-131">명령을 사용 하 여 스크립트 파일이 종료 되 면 `exit` 프로세스 종료 코드는 명령에 사용 되는 숫자 인수로 설정 됩니다 `exit` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-131">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="a68f7-132">정상적인 종료를 사용 하는 경우 종료 코드는 항상 `0` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-132">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="a68f7-133">와 마찬가지로 `-Command` , 스크립트 종료 오류가 발생할 때 종료 코드는로 설정 됩니다 `1` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-133">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="a68f7-134">그러나와는 달리 `-Command` , <kbd>Ctrl</kbd>C를 사용 하 여 실행이 중단 되는 경우 - <kbd>C</kbd> 종료 코드는 `0` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-134">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="a68f7-135">-Command | -c</span><span class="sxs-lookup"><span data-stu-id="a68f7-135">-Command | -c</span></span>

<span data-ttu-id="a68f7-136">지정 된 명령 (및 매개 변수)을 PowerShell 명령 프롬프트에서 입력 한 것 처럼 실행 한 다음 매개 변수가 지정 되지 않은 경우 종료 합니다 `NoExit` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-136">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="a68f7-137">**명령의** 값은 `-` , 스크립트 블록 또는 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-137">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="a68f7-138">**Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-138">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="a68f7-139">명령 **매개 변수** 는 **명령** 에 **ScriptBlock** 형식으로 전달 된 값을 인식할 수 있는 경우에만 실행할 스크립트 블록을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-139">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="a68f7-140">이는 다른 PowerShell 호스트에서 실행 하는 경우에 _만_ 가능 `pwsh` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-140">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="a68f7-141">**ScriptBlock** 형식은 `{}` 에 전달 되기 전에 기존 변수에 포함 되거나 식에서 반환 되거나 중괄호 ()로 묶인 리터럴 스크립트 블록으로 PowerShell 호스트에 의해 구문 분석 될 수 있습니다 `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-141">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="a68f7-142">에서는 `cmd.exe` 스크립트 블록 (또는 **ScriptBlock** 형식)이 없으므로 **명령** 에 전달 되는 값은 _항상_ 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-142">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="a68f7-143">문자열 내부에 스크립트 블록을 작성할 수 있지만, 실행되지 않고 정확히 일반 PowerShell 프롬프트에 입력한 것처럼 동작하여 스크립트 블록의 콘텐츠를 다시 사용자에게 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-143">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="a68f7-144">**명령** 에 전달 된 문자열은 여전히 PowerShell 코드로 실행 되므로에서 실행할 때 스크립트 블록 중괄호는 처음에는 필요 하지 않습니다 `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-144">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="a68f7-145">문자열 내부에 정의된 인라인 스크립트 블록을 실행하려면 [호출 연산자](about_operators.md#special-operators) `&`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-145">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="a68f7-146">**명령의** 값이 문자열인 경우 명령 뒤의 모든 인수가 실행할 명령의 일부로 해석 되기 때문에 **command** 는 pwsh의 마지막 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-146">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="a68f7-147">기존 PowerShell 세션 내에서 호출 되는 경우 결과는 라이브 개체가 아니라 역직렬화 된 XML 개체로 부모 셸에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-147">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="a68f7-148">다른 셸에서는 결과가 문자열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-148">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="a68f7-149">**Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-149">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="a68f7-150">표준 입력으로 **Command** 매개 변수를 사용 하는 경우 표준 입력을 리디렉션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-150">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="a68f7-151">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a68f7-151">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="a68f7-152">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-152">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="a68f7-153">프로세스 종료 코드는 스크립트 블록 내의 마지막 (실행 됨) 명령의 상태에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-153">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="a68f7-154">가 이거나가 인 경우 종료 코드는입니다 `0` `$?` `$true` `1` `$?` `$false` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-154">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="a68f7-155">마지막 명령이 또는 이외의 종료 코드를 명시적으로 설정 하는 외부 프로그램 또는 PowerShell 스크립트인 경우 `0` `1` 해당 종료 코드는 `1` 프로세스 종료 코드의로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-155">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="a68f7-156">특정 종료 코드를 유지 하려면 `exit $LASTEXITCODE` 명령 문자열 또는 스크립트 블록에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-156">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="a68f7-157">마찬가지로, 또는와 같은 스크립트 종료 (runspace 종료) 오류가 `throw` `-ErrorAction Stop` 발생 하거나 실행이 <kbd>Ctrl</kbd>C를 사용 하 여 중단 되 면 값 1이 반환 됩니다 - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a68f7-157">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="a68f7-158">-ConfigurationName | -config</span><span class="sxs-lookup"><span data-stu-id="a68f7-158">-ConfigurationName | -config</span></span>

<span data-ttu-id="a68f7-159">PowerShell이 실행 되는 구성 끝점을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-159">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="a68f7-160">이는 기본 PowerShell 원격 끝점 또는 특정 사용자 역할 기능이 있는 사용자 지정 끝점을 포함 하 여 로컬 컴퓨터에 등록 된 모든 끝점이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-160">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="a68f7-161">예: `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="a68f7-161">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="a68f7-162">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="a68f7-162">-CustomPipeName</span></span>

<span data-ttu-id="a68f7-163">디버깅 및 기타 프로세스 간 통신에 사용 되는 추가 IPC 서버 (명명 된 파이프)에 사용할 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-163">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="a68f7-164">이는 다른 PowerShell 인스턴스에 연결 하는 데 사용할 수 있는 예측 가능한 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-164">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="a68f7-165">일반적으로의 **CustomPipeName** 매개 변수와 함께 사용 `Enter-PSHostProcess` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-165">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="a68f7-166">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-166">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="a68f7-167">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a68f7-167">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="a68f7-168">-EncodedCommand | -e | -ec</span><span class="sxs-lookup"><span data-stu-id="a68f7-168">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="a68f7-169">명령의 b a s e 64로 인코드된 문자열 버전을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-169">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="a68f7-170">이 매개 변수를 사용 하 여 복잡 하 고 중첩 된 따옴표를 필요로 하는 명령을 PowerShell에 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-170">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="a68f7-171">Base64 표현은 u t f-16으로 인코딩된 문자열 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-171">The Base64 representation must be a UTF-16 encoded string.</span></span>

<span data-ttu-id="a68f7-172">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a68f7-172">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="a68f7-173">-Set-executionpolicy | -ex | -ep</span><span class="sxs-lookup"><span data-stu-id="a68f7-173">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="a68f7-174">현재 세션에 대 한 기본 실행 정책을 설정 하 고 `$env:PSExecutionPolicyPreference` 환경 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-174">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="a68f7-175">이 매개 변수는 영구적으로 구성 된 실행 정책을 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-175">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="a68f7-176">이 매개 변수는 Windows 컴퓨터에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-176">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="a68f7-177">`$env:PSExecutionPolicyPreference`Windows가 아닌 플랫폼에 환경 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-177">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---in---if"></a><span data-ttu-id="a68f7-178">-InputFormat | -in | -if</span><span class="sxs-lookup"><span data-stu-id="a68f7-178">-InputFormat | -in | -if</span></span>

<span data-ttu-id="a68f7-179">PowerShell로 전송되는 데이터 형식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-179">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="a68f7-180">유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-180">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="a68f7-181">-Interactive | -i</span><span class="sxs-lookup"><span data-stu-id="a68f7-181">-Interactive | -i</span></span>

<span data-ttu-id="a68f7-182">사용자에 게 대화형 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-182">Present an interactive prompt to the user.</span></span> <span data-ttu-id="a68f7-183">비 대화형 매개 변수의 역함수입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-183">Inverse for NonInteractive parameter.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="a68f7-184">-NoExit | -noe</span><span class="sxs-lookup"><span data-stu-id="a68f7-184">-NoExit | -noe</span></span>

<span data-ttu-id="a68f7-185">시작 명령을 실행한 후 종료하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-185">Does not exit after running startup commands.</span></span>

<span data-ttu-id="a68f7-186">예: `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="a68f7-186">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="a68f7-187">-NoLogo | -nol</span><span class="sxs-lookup"><span data-stu-id="a68f7-187">-NoLogo | -nol</span></span>

<span data-ttu-id="a68f7-188">대화형 세션 시작 시 저작권 배너를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-188">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="a68f7-189">-비 대화형 | -비 i</span><span class="sxs-lookup"><span data-stu-id="a68f7-189">-NonInteractive | -noni</span></span>

<span data-ttu-id="a68f7-190">사용자에게 대화형 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-190">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="a68f7-191">또는 확인 프롬프트와 같은 대화형 기능을 사용 하려고 하면 `Read-Host` 문 종료 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-191">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="a68f7-192">-NoProfile | -nop</span><span class="sxs-lookup"><span data-stu-id="a68f7-192">-NoProfile | -nop</span></span>

<span data-ttu-id="a68f7-193">PowerShell 프로필을 로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-193">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="a68f7-194">-OutputFormat | -o | -/</span><span class="sxs-lookup"><span data-stu-id="a68f7-194">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="a68f7-195">PowerShell의 출력 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-195">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="a68f7-196">유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-196">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="a68f7-197">예: `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="a68f7-197">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="a68f7-198">PowerShell 세션을 트 내의 호출 하면 deserialize 된 개체를 일반 문자열 대신 출력으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-198">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="a68f7-199">다른 셸에서 호출 된 경우 출력은 EXPORT-CLIXML 텍스트로 형식이 지정 된 문자열 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-199">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="a68f7-200">-SettingsFile | -설정</span><span class="sxs-lookup"><span data-stu-id="a68f7-200">-SettingsFile | -settings</span></span>

<span data-ttu-id="a68f7-201">`powershell.config.json`세션에 대 한 시스템 차원 설정 파일을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-201">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="a68f7-202">기본적으로 시스템 차원의 설정은 `powershell.config.json` 디렉터리의에서 읽습니다 `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-202">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="a68f7-203">이러한 설정은 인수로 지정 된 끝점에서 사용 되지 않습니다 `-ConfigurationName` .</span><span class="sxs-lookup"><span data-stu-id="a68f7-203">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="a68f7-204">예: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="a68f7-204">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="a68f7-205">-SSHServerMode | -sshs</span><span class="sxs-lookup"><span data-stu-id="a68f7-205">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="a68f7-206">PowerShell을 SSH 하위 시스템으로 실행 하기 위해 sshd_config에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-206">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="a68f7-207">다른 용도로 사용 하거나 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-207">It is not intended or supported for any other use.</span></span>

### <a name="-version---v"></a><span data-ttu-id="a68f7-208">-Version | -v</span><span class="sxs-lookup"><span data-stu-id="a68f7-208">-Version | -v</span></span>

<span data-ttu-id="a68f7-209">PowerShell의 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-209">Displays the version of PowerShell.</span></span> <span data-ttu-id="a68f7-210">추가 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-210">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="a68f7-211">-System.windows.window.windowstyle | -w</span><span class="sxs-lookup"><span data-stu-id="a68f7-211">-WindowStyle | -w</span></span>

<span data-ttu-id="a68f7-212">세션에 대한 창 스타일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-212">Sets the window style for the session.</span></span> <span data-ttu-id="a68f7-213">유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-213">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="a68f7-214">-WorkingDirectory | -wd</span><span class="sxs-lookup"><span data-stu-id="a68f7-214">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="a68f7-215">시작 시를 실행 하 여 초기 작업 디렉터리를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-215">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="a68f7-216">유효한 PowerShell 파일 경로가 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-216">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="a68f7-217">홈 디렉터리에서 PowerShell을 시작 하려면 다음을 사용 합니다. `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="a68f7-217">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="a68f7-218">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="a68f7-218">-Help, -?, /?</span></span>

<span data-ttu-id="a68f7-219">에 대 한 도움말을 표시 `pwsh` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-219">Displays help for `pwsh`.</span></span> <span data-ttu-id="a68f7-220">PowerShell에서 pwsh 명령을 입력 하는 경우 슬래시 ()가 아닌 하이픈 ()을 사용 하 여 명령 매개 변수 앞에 추가 `-` `/` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68f7-220">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
