---
description: 명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `powershell.exe` . 명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223330"
---
# <a name="about-powershellexe"></a><span data-ttu-id="352d1-105">PowerShell.exe 정보</span><span class="sxs-lookup"><span data-stu-id="352d1-105">About PowerShell.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="352d1-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="352d1-106">Short Description</span></span>
<span data-ttu-id="352d1-107">명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="352d1-107">Explains how to use the `powershell.exe` command-line interface.</span></span> <span data-ttu-id="352d1-108">명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="352d1-109">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="352d1-109">Long Description</span></span>

### <a name="syntax"></a><span data-ttu-id="352d1-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="352d1-110">SYNTAX</span></span>

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a><span data-ttu-id="352d1-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="352d1-111">Parameters</span></span>

#### <a name="-psconsolefile-filepath"></a><span data-ttu-id="352d1-112">-PSConsoleFile \<FilePath\></span><span class="sxs-lookup"><span data-stu-id="352d1-112">-PSConsoleFile \<FilePath\></span></span>

<span data-ttu-id="352d1-113">지정된 PowerShell 콘솔 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-113">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="352d1-114">콘솔 파일의 경로와 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-114">Enter the path and name of the console file.</span></span> <span data-ttu-id="352d1-115">콘솔 파일을 만들려면 PowerShell에서 Export-Console cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-115">To create a console file, use the Export-Console cmdlet in PowerShell.</span></span>

#### <a name="-version-powershell-version"></a><span data-ttu-id="352d1-116">버전 \<PowerShell Version\></span><span class="sxs-lookup"><span data-stu-id="352d1-116">-Version \<PowerShell Version\></span></span>

<span data-ttu-id="352d1-117">지정된 버전의 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-117">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="352d1-118">유효한 값은 2.0 및 3.0입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-118">Valid values are 2.0 and 3.0.</span></span> <span data-ttu-id="352d1-119">지정한 버전이 시스템에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-119">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="352d1-120">컴퓨터에 Windows PowerShell 3.0이 설치 되어 있는 경우 "3.0"이 기본 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-120">If Windows PowerShell 3.0 is installed on the computer, "3.0" is the default version.</span></span>
<span data-ttu-id="352d1-121">그렇지 않으면 "2.0"이 기본 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-121">Otherwise, "2.0" is the default version.</span></span> <span data-ttu-id="352d1-122">자세한 내용은 [PowerShell 설치](/powershell/scripting/install/installing-windows-powershell)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="352d1-122">For more information, see [Installing PowerShell](/powershell/scripting/install/installing-windows-powershell).</span></span>

#### <a name="-nologo"></a><span data-ttu-id="352d1-123">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="352d1-123">-NoLogo</span></span>

<span data-ttu-id="352d1-124">시작 시 저작권 배너를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-124">Hides the copyright banner at startup.</span></span>

#### <a name="-noexit"></a><span data-ttu-id="352d1-125">-NoExit</span><span class="sxs-lookup"><span data-stu-id="352d1-125">-NoExit</span></span>

<span data-ttu-id="352d1-126">시작 명령을 실행한 후 종료하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-126">Does not exit after running startup commands.</span></span>

#### <a name="-sta"></a><span data-ttu-id="352d1-127">-Sta</span><span class="sxs-lookup"><span data-stu-id="352d1-127">-Sta</span></span>

<span data-ttu-id="352d1-128">단일 스레드 아파트를 사용하여 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-128">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="352d1-129">Windows PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-129">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="352d1-130">Windows PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-130">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-mta"></a><span data-ttu-id="352d1-131">-Mta</span><span class="sxs-lookup"><span data-stu-id="352d1-131">-Mta</span></span>

<span data-ttu-id="352d1-132">다중 스레드 아파트를 사용하여 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-132">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="352d1-133">이 매개 변수는 PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-133">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="352d1-134">PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-134">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="352d1-135">PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-135">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-noprofile"></a><span data-ttu-id="352d1-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="352d1-136">-NoProfile</span></span>

<span data-ttu-id="352d1-137">PowerShell 프로필을 로드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-137">Does not load the PowerShell profile.</span></span>

#### <a name="-noninteractive"></a><span data-ttu-id="352d1-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="352d1-138">-NonInteractive</span></span>

<span data-ttu-id="352d1-139">사용자에게 대화형 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-139">Does not present an interactive prompt to the user.</span></span>

#### <a name="-inputformat-text--xml"></a><span data-ttu-id="352d1-140">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="352d1-140">-InputFormat {Text | XML}</span></span>

<span data-ttu-id="352d1-141">PowerShell로 전송되는 데이터 형식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-141">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="352d1-142">유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-outputformat-text--xml"></a><span data-ttu-id="352d1-143">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="352d1-143">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="352d1-144">PowerShell의 출력 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-144">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="352d1-145">유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-145">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-windowstyle-window-style"></a><span data-ttu-id="352d1-146">-WindowStyle \<Window style\></span><span class="sxs-lookup"><span data-stu-id="352d1-146">-WindowStyle \<Window style\></span></span>

<span data-ttu-id="352d1-147">세션에 대한 창 스타일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-147">Sets the window style for the session.</span></span> <span data-ttu-id="352d1-148">유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-148">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

#### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="352d1-149">-EncodedCommand \<Base64EncodedCommand\></span><span class="sxs-lookup"><span data-stu-id="352d1-149">-EncodedCommand \<Base64EncodedCommand\></span></span>

<span data-ttu-id="352d1-150">명령의 Base 64로 인코드된 문자열 버전을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-150">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="352d1-151">이 매개 변수를 사용하여 명령을 큰따옴표 또는 중괄호가 필요한 PowerShell로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-151">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span> <span data-ttu-id="352d1-152">UTF-16LE 문자 인코딩을 사용 하 여 문자열의 서식을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-152">The string must be formatted using UTF-16LE character encoding.</span></span>

#### <a name="-configurationname-string"></a><span data-ttu-id="352d1-153">-ConfigurationName \<string\></span><span class="sxs-lookup"><span data-stu-id="352d1-153">-ConfigurationName \<string\></span></span>

<span data-ttu-id="352d1-154">PowerShell이 실행 되는 구성 끝점을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-154">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="352d1-155">이는 기본 PowerShell 원격 끝점 또는 특정 사용자 역할 기능이 있는 사용자 지정 끝점을 포함 하 여 로컬 컴퓨터에 등록 된 모든 끝점이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-155">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

#### <a name="-file----filepath-args"></a><span data-ttu-id="352d1-156">-File-| \<filePath\>\<args\></span><span class="sxs-lookup"><span data-stu-id="352d1-156">-File - | \<filePath\> \<args\></span></span>

<span data-ttu-id="352d1-157">**File** 값이 "-" 이면 표준 입력에서 명령 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-157">If the value of **File** is "-", the command text is read from standard input.</span></span>
<span data-ttu-id="352d1-158">`powershell -File -`리디렉션된 표준 입력 없이 실행 하면 일반 세션이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-158">Running `powershell -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="352d1-159">이는 **파일** 매개 변수를 지정 하지 않는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-159">This is the same as not specifying the **File** parameter at all.</span></span>

<span data-ttu-id="352d1-160">**파일** 의 값이 파일 경로인 경우 스크립트는 로컬 범위 ("점 원본")에서 실행 되므로 스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-160">If the value of **File** is a file path, the script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="352d1-161">스크립트 파일의 경로와 매개 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-161">Enter the script file path and any parameters.</span></span> <span data-ttu-id="352d1-162">**File** 은 명령의 마지막 매개 변수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-162">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="352d1-163">**File** 매개 변수 뒤에 입력 한 모든 값은 해당 스크립트에 전달 된 스크립트 파일 경로 및 매개 변수로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-163">All values typed after the **File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="352d1-164">스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후).</span><span class="sxs-lookup"><span data-stu-id="352d1-164">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="352d1-165">예를 들어 **cmd.exe** 에 있고 환경 변수 값을 전달 하려는 경우 **cmd.exe** 구문을 사용 합니다. `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="352d1-165">For example, if you are in **cmd.exe** and want to pass an environment variable value, you would use the **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="352d1-166">반면 `powershell.exe -File .\test.ps1 -TestParam $env:windir` **cmd.exe** 에서를 실행 하면 `$env:windir` 현재 **cmd.exe** 셸에 대 한 특별 한 의미가 없기 때문에 스크립트에서 리터럴 문자열을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-166">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** results in the script receiving the literal string `$env:windir` because it has no special meaning to the current **cmd.exe** shell.</span></span> <span data-ttu-id="352d1-167">`$env:windir`환경 변수 참조의 스타일은 PowerShell 코드로 해석 되기 때문에 **명령** 매개 변수 내에서 사용할 _수 있습니다_ .</span><span class="sxs-lookup"><span data-stu-id="352d1-167">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it will be interpreted as PowerShell code.</span></span>

<span data-ttu-id="352d1-168">마찬가지로 **일괄 처리 스크립트** 에서 동일한 명령을 실행 하려는 경우 또는 대신를 사용 하 여 `%~dp0` `.\` `$PSScriptRoot` 현재 실행 디렉터리인를 나타냅니다 `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="352d1-168">Similarly, if you want to execute the same command from a **Batch script** , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%`.</span></span>
<span data-ttu-id="352d1-169">대신를 사용 하는 경우 `.\test.ps1` 리터럴 경로를 찾을 수 없으므로 PowerShell에서 오류를 throw 합니다. `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="352d1-169">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="352d1-170">파일의 **값이 파일** 경로인 경우 **파일 매개 변수 이름 뒤에 입력** 한 문자는 스크립트 파일 경로, 스크립트 매개 변수 순으로 해석 되기 때문에 **file** 은 명령의 마지막 매개 변수 _여야 합니다_ .</span><span class="sxs-lookup"><span data-stu-id="352d1-170">When the value of **File** is a file path, **File** _must_ be the last parameter in the command because any characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="352d1-171">**File** 매개 변수의 값에 스크립트 매개 변수 및 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-171">You can include the script parameters and values in the value of the **File** parameter.</span></span> <span data-ttu-id="352d1-172">`-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="352d1-172">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="352d1-173">일반적으로 스크립트의 스위치 매개 변수는 포함되거나 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-173">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="352d1-174">예를 들어 다음 명령은 스크립트 파일의 **All** 매개 변수를 사용 합니다 `Get-Script.ps1` . `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="352d1-174">For example, the following command uses the **All** parameter of the `Get-Script.ps1` script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="352d1-175">드문 경우 지만 매개 변수에 **부울** 값을 제공 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-175">In rare cases, you might need to provide a **Boolean** value for a parameter.</span></span>
<span data-ttu-id="352d1-176">이러한 방식으로 스크립트를 실행 하는 경우 스위치 매개 변수에 대 한 명시적 부울 값을 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-176">It is not possible to pass an explicit boolean value for a switch parameter when running a script in this way.</span></span> <span data-ttu-id="352d1-177">이 제한은 PowerShell 6 ()에서 제거 되었습니다 `pwsh.exe` .</span><span class="sxs-lookup"><span data-stu-id="352d1-177">This limitation was removed in PowerShell 6 (`pwsh.exe`).</span></span>

#### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="352d1-178">-ExecutionPolicy \<ExecutionPolicy\></span><span class="sxs-lookup"><span data-stu-id="352d1-178">-ExecutionPolicy \<ExecutionPolicy\></span></span>

<span data-ttu-id="352d1-179">현재 세션에 대 한 기본 실행 정책을 설정 하 고 `$env:PSExecutionPolicyPreference` 환경 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-179">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="352d1-180">이 매개 변수는 레지스트리에 설정된 PowerShell 실행 정책을 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-180">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="352d1-181">유효한 값 목록을 비롯한 PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="352d1-181">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

#### <a name="-command"></a><span data-ttu-id="352d1-182">-Command</span><span class="sxs-lookup"><span data-stu-id="352d1-182">-Command</span></span>

<span data-ttu-id="352d1-183">지정 된 명령 (및 매개 변수)을 PowerShell 명령 프롬프트에서 입력 한 것 처럼 실행 한 다음 매개 변수가 지정 되지 않은 경우 종료 합니다 `NoExit` .</span><span class="sxs-lookup"><span data-stu-id="352d1-183">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="352d1-184">**명령의** 값은 `-` , 스크립트 블록 또는 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-184">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="352d1-185">**Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-185">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="352d1-186">명령 **매개 변수** 는 **명령** 에 **ScriptBlock** 형식으로 전달 된 값을 인식할 수 있는 경우에만 실행할 스크립트 블록을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-186">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="352d1-187">이는 다른 PowerShell 호스트에서 실행 하는 경우에 _만_ 가능 `powershell.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-187">This is _only_ possible when running `powershell.exe` from another PowerShell host.</span></span> <span data-ttu-id="352d1-188">**ScriptBlock** 형식은 `{}` 에 전달 되기 전에 기존 변수에 포함 되거나 식에서 반환 되거나 중괄호 ()로 묶인 리터럴 스크립트 블록으로 PowerShell 호스트에 의해 구문 분석 될 수 있습니다 `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="352d1-188">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `powershell.exe`.</span></span>

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="352d1-189">에서는 `cmd.exe` 스크립트 블록 (또는 **ScriptBlock** 형식)이 없으므로 **명령** 에 전달 되는 값은 _항상_ 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-189">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="352d1-190">문자열 내부에 스크립트 블록을 작성할 수 있지만, 실행되지 않고 정확히 일반 PowerShell 프롬프트에 입력한 것처럼 동작하여 스크립트 블록의 콘텐츠를 다시 사용자에게 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-190">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="352d1-191">**명령** 에 전달 된 문자열은 여전히 PowerShell 코드로 실행 되므로에서 실행할 때 스크립트 블록 중괄호는 처음에는 필요 하지 않습니다 `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="352d1-191">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="352d1-192">문자열 내부에 정의된 인라인 스크립트 블록을 실행하려면 [호출 연산자](about_operators.md#special-operators) `&`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-192">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="352d1-193">**명령의** 값이 문자열인 경우 명령 뒤의 모든 인수가 실행할 명령의 일부로 해석 되기 때문에 **command** 는 pwsh의 마지막 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-193">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="352d1-194">기존 PowerShell 세션 내에서 호출 되는 경우 결과는 라이브 개체가 아니라 역직렬화 된 XML 개체로 부모 셸에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-194">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="352d1-195">다른 셸에서는 결과가 문자열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-195">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="352d1-196">**Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-196">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="352d1-197">표준 입력으로 **Command** 매개 변수를 사용 하는 경우 표준 입력을 리디렉션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-197">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="352d1-198">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="352d1-198">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="352d1-199">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-199">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="352d1-200">프로세스 종료 코드는 스크립트 블록 내의 마지막 (실행 됨) 명령의 상태에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-200">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="352d1-201">가 이거나가 인 경우 종료 코드는입니다 `0` `$?` `$true` `1` `$?` `$false` .</span><span class="sxs-lookup"><span data-stu-id="352d1-201">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="352d1-202">마지막 명령이 또는 이외의 종료 코드를 명시적으로 설정 하는 외부 프로그램 또는 PowerShell 스크립트인 경우 `0` `1` 해당 종료 코드는 `1` 프로세스 종료 코드의로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-202">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="352d1-203">특정 종료 코드를 유지 하려면 `exit $LASTEXITCODE` 명령 문자열 또는 스크립트 블록에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-203">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="352d1-204">마찬가지로, 또는와 같은 스크립트 종료 (runspace 종료) 오류가 `throw` `-ErrorAction Stop` 발생 하거나 실행이 <kbd>Ctrl</kbd>C를 사용 하 여 중단 되 면 값 1이 반환 됩니다 - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="352d1-204">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

<span data-ttu-id="352d1-205">다른 PowerShell 호스트에서 **PowerShell.exe** 를 실행 하는 경우에 _만_ 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-205">_only_ possible when running **PowerShell.exe** from another PowerShell host.</span></span>
<span data-ttu-id="352d1-206">**ScriptBlock** 형식은 기존 변수에 포함 되거나, 식에서 반환 되거나, `{}` **PowerShell.exe** 에 전달 되기 전에 중괄호로 묶인 리터럴 스크립트 블록으로 PowerShell 호스트에 의해 구문 분석 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-206">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to **PowerShell.exe**.</span></span>

<span data-ttu-id="352d1-207">**cmd.exe** 에는 스크립트 블록 (또는 **ScriptBlock** 형식)이 없으므로 **명령** 에 전달 되는 값은 _항상_ 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-207">In **cmd.exe** , there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="352d1-208">문자열 내부에 스크립트 블록을 작성할 수 있지만, 실행되지 않고 정확히 일반 PowerShell 프롬프트에 입력한 것처럼 동작하여 스크립트 블록의 콘텐츠를 다시 사용자에게 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-208">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="352d1-209">**명령** 에 전달 된 문자열은 PowerShell로 계속 실행 되므로 **cmd.exe** 에서 실행할 때 스크립트 블록 중괄호는 처음에는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-209">A string passed to **Command** will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from **cmd.exe**.</span></span> <span data-ttu-id="352d1-210">문자열 내에 정의 된 인라인 스크립트 블록을 실행 하려면 [call 연산자](about_operators.md#special-operators) 를 
 `&` 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-210">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators)
`&` can be used:</span></span>

```console
"& {<command>}"
```

#### <a name="-help---"></a><span data-ttu-id="352d1-211">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="352d1-211">-Help, -?, /?</span></span>

<span data-ttu-id="352d1-212">**PowerShell.exe** 에 대 한 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-212">Displays help for **PowerShell.exe**.</span></span> <span data-ttu-id="352d1-213">PowerShell 세션에 **PowerShell.exe** 명령을 입력 하는 경우 슬래시 (/)가 아닌 하이픈 (-)을 사용 하 여 명령 매개 변수 앞에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-213">If you are typing a **PowerShell.exe** command in a PowerShell session, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="352d1-214">**cmd.exe** 에서 하이픈 또는 슬래시 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-214">You can use either a hyphen or forward slash in **cmd.exe**.</span></span>

### <a name="remarks"></a><span data-ttu-id="352d1-215">REMARKS</span><span class="sxs-lookup"><span data-stu-id="352d1-215">REMARKS</span></span>

<span data-ttu-id="352d1-216">문제 해결 참고: PowerShell 2.0에서는 PowerShell 콘솔에서 일부 프로그램을 시작 하는 작업이 실패 하 고 **LastExitCode** 통해가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="352d1-216">Troubleshooting note: In PowerShell 2.0, starting some programs from the PowerShell console fails with a **LastExitCode** of 0xc0000142.</span></span>

### <a name="examples"></a><span data-ttu-id="352d1-217">예제</span><span class="sxs-lookup"><span data-stu-id="352d1-217">EXAMPLES</span></span>

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
