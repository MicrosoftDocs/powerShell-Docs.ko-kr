---
description: PowerShell에서 스크립트를 실행 하 고 작성 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: 2fc81d1d43b8cdddaacb917deaa5d58536a541cb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600859"
---
# <a name="about-scripts"></a><span data-ttu-id="616a0-103">스크립트 정보</span><span class="sxs-lookup"><span data-stu-id="616a0-103">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="616a0-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="616a0-104">Short description</span></span>
<span data-ttu-id="616a0-105">PowerShell에서 스크립트를 실행 하 고 작성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-105">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="616a0-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-106">Long description</span></span>

<span data-ttu-id="616a0-107">스크립트는 하나 이상의 PowerShell 명령을 포함 하는 일반 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-107">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="616a0-108">PowerShell 스크립트에는 `.ps1` 파일 확장명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-108">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="616a0-109">스크립트를 실행 하는 것은 cmdlet 실행과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-109">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="616a0-110">스크립트의 경로와 파일 이름을 입력 하 고 매개 변수를 사용 하 여 데이터를 전송 하 고 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-110">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="616a0-111">컴퓨터 또는 다른 컴퓨터의 원격 세션에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-111">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="616a0-112">스크립트를 작성 하면 나중에 사용할 수 있도록 명령을 저장 하 고 다른 사용자와 쉽게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-112">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="616a0-113">가장 중요 한 점은 스크립트 경로와 파일 이름을 입력 하 여 명령을 실행할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-113">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="616a0-114">스크립트는 파일의 단일 명령 처럼 간단할 수도 있고 복잡 한 프로그램의 경우에만 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-114">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="616a0-115">스크립트에는 `#Requires` 특수 주석, 매개 변수 사용, 데이터 섹션 지원, 보안을 위한 디지털 서명 등의 추가 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-115">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="616a0-116">스크립트 및 스크립트의 함수에 대 한 도움말 항목을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-116">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="616a0-117">스크립트를 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="616a0-117">How to run a script</span></span>

<span data-ttu-id="616a0-118">Windows에서 스크립트를 실행 하려면 먼저 기본 PowerShell 실행 정책을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-118">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="616a0-119">실행 정책은 비 Windows 플랫폼에서 실행 되는 PowerShell에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-119">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="616a0-120">기본 실행 정책 인은 `Restricted` 로컬 컴퓨터에서 작성 하는 스크립트를 포함 하 여 모든 스크립트가 실행 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-120">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="616a0-121">자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-121">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="616a0-122">실행 정책은 레지스트리에 저장 되므로 각 컴퓨터에서 한 번만 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-122">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="616a0-123">실행 정책을 변경 하려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="616a0-123">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="616a0-124">명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-124">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="616a0-125">or</span><span class="sxs-lookup"><span data-stu-id="616a0-125">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="616a0-126">변경 내용은 즉시 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-126">The change is effective immediately.</span></span>

<span data-ttu-id="616a0-127">스크립트를 실행 하려면 스크립트 파일의 전체 이름 및 전체 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-127">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="616a0-128">예를 들어 C:\Scripts 디렉터리에서 Get-ServiceLog.ps1 스크립트를 실행 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-128">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="616a0-129">현재 디렉터리에서 스크립트를 실행 하려면 현재 디렉터리에 대 한 경로를 입력 하거나, 점을 사용 하 여 현재 디렉터리를 표시 한 다음 경로 백슬래시 ()를 사용 `.\` 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-129">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="616a0-130">예를 들어 로컬 디렉터리에서 ServicesLog.ps1 스크립트를 실행 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-130">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="616a0-131">스크립트에 매개 변수가 있는 경우 스크립트 파일 이름 뒤에 매개 변수 및 매개 변수 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-131">If the script has parameters, type the parameters and parameter values after the script filename.</span></span>

<span data-ttu-id="616a0-132">예를 들어 다음 명령은 Get-ServiceLog 스크립트의 ServiceName 매개 변수를 사용 하 여 WinRM 서비스 활동의 로그를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-132">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="616a0-133">보안 기능인 PowerShell은 파일 탐색기에서 스크립트 아이콘을 두 번 클릭 하거나 스크립트가 현재 디렉터리에 있는 경우에도 전체 경로 없이 스크립트 이름을 입력할 때 스크립트를 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-133">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="616a0-134">PowerShell에서 명령 및 스크립트를 실행 하는 방법에 대 한 자세한 내용은 [about_Command_Precedence](about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-134">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="616a0-135">PowerShell을 사용하여 실행</span><span class="sxs-lookup"><span data-stu-id="616a0-135">Run with PowerShell</span></span>

<span data-ttu-id="616a0-136">PowerShell 3.0부터 파일 탐색기에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-136">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="616a0-137">"PowerShell에서 실행" 기능을 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-137">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="616a0-138">파일 탐색기를 실행 하 고 스크립트 파일 이름을 마우스 오른쪽 단추로 클릭 한 다음 "PowerShell에서 실행"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-138">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="616a0-139">"PowerShell에서 실행" 기능은 필수 매개 변수가 없는 스크립트를 실행 하 고 출력을 명령 프롬프트로 반환 하지 않도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-139">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="616a0-140">자세한 내용은 [about_Run_With_PowerShell](about_Run_With_PowerShell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-140">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="616a0-141">다른 컴퓨터에서 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="616a0-141">Running scripts on other computers</span></span>

<span data-ttu-id="616a0-142">하나 이상의 원격 컴퓨터에서 스크립트를 실행 하려면 cmdlet의 **FilePath** 매개 변수를 사용 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="616a0-142">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="616a0-143">**FilePath** 매개 변수 값으로 스크립트의 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-143">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="616a0-144">스크립트는 로컬 컴퓨터나 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-144">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="616a0-145">다음 명령은 `Get-ServiceLog.ps1` Server01 및 Server02 라는 원격 컴퓨터에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-145">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="616a0-146">스크립트에 대 한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="616a0-146">Get help for scripts</span></span>

<span data-ttu-id="616a0-147">Get-Help cmdlet은 스크립트와 cmdlet 및 다른 유형의 명령에 대 한 도움말 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-147">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="616a0-148">스크립트에 대 한 도움말 항목을 보려면를 입력 한 `Get-Help` 다음 스크립트의 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-148">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="616a0-149">스크립트 경로가 `Path` 환경 변수에 있는 경우 경로를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-149">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="616a0-150">예를 들어 ServicesLog.ps1 스크립트에 대 한 도움말을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-150">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="616a0-151">스크립트를 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="616a0-151">How to write a script</span></span>

<span data-ttu-id="616a0-152">스크립트에는 단일 명령, 파이프라인을 사용 하는 명령, 함수 및 If 문과 For 루프와 같은 제어 구조를 포함 하는 모든 유효한 PowerShell 명령이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-152">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="616a0-153">스크립트를 작성 하려면 텍스트 편집기에서 새 파일을 열고 명령을 입력 한 다음 파일 확장명이 올바른 파일 이름으로 파일에 저장 `.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-153">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="616a0-154">다음 예에서는 현재 시스템에서 실행 되는 서비스를 가져와서 로그 파일에 저장 하는 간단한 스크립트를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-154">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="616a0-155">현재 날짜에서 로그 파일 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-155">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="616a0-156">이 스크립트를 만들려면 텍스트 편집기나 스크립트 편집기를 열고 다음 명령을 입력 한 다음 이라는 파일에 저장 `ServiceLog.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-156">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="616a0-157">스크립트의 매개 변수</span><span class="sxs-lookup"><span data-stu-id="616a0-157">Parameters in scripts</span></span>

<span data-ttu-id="616a0-158">스크립트에서 매개 변수를 정의 하려면 Param 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-158">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="616a0-159">`Param`문은 주석과 문을 제외 하 고 스크립트의 첫 번째 문 이어야 합니다 `#Require` .</span><span class="sxs-lookup"><span data-stu-id="616a0-159">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="616a0-160">스크립트 매개 변수는 함수 매개 변수 처럼 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-160">Script parameters work like function parameters.</span></span> <span data-ttu-id="616a0-161">매개 변수 값은 스크립트의 모든 명령에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-161">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="616a0-162">매개 변수 특성 및 명명 된 인수를 포함 하 여 함수 매개 변수의 모든 기능을 스크립트 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-162">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="616a0-163">스크립트를 실행할 때 스크립트 사용자는 스크립트 이름 뒤에 매개 변수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-163">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="616a0-164">다음 예에서는 `Test-Remote.ps1` **ComputerName** 매개 변수가 있는 스크립트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-164">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="616a0-165">두 스크립트 함수는 모두 **ComputerName** 매개 변수 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-165">Both of the script functions can access the **ComputerName** parameter value.</span></span>

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

<span data-ttu-id="616a0-166">이 스크립트를 실행 하려면 스크립트 이름 뒤에 매개 변수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-166">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="616a0-167">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="616a0-167">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="616a0-168">Param 문과 함수 매개 변수에 대 한 자세한 내용은 [about_Functions](about_Functions.md) 및 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-168">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="616a0-169">스크립트에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="616a0-169">Writing help for scripts</span></span>

<span data-ttu-id="616a0-170">다음 두 가지 방법 중 하나를 사용 하 여 스크립트에 대 한 도움말 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-170">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="616a0-171">스크립트에 대 한 Comment-Based 도움말</span><span class="sxs-lookup"><span data-stu-id="616a0-171">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="616a0-172">주석에 특수 키워드를 사용 하 여 도움말 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-172">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="616a0-173">스크립트에 대 한 주석 기반 도움말을 만들려면 스크립트 파일의 시작 부분이 나 끝 부분에 주석을 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-173">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="616a0-174">주석 기반 도움말에 대 한 자세한 내용은 [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-174">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="616a0-175">스크립트에 대 한 XML-Based 도움말</span><span class="sxs-lookup"><span data-stu-id="616a0-175">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="616a0-176">일반적으로 cmdlet에 대해 생성 되는 형식과 같은 XML 기반 도움말 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-176">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="616a0-177">도움말 항목을 여러 언어로 번역 하는 경우 XML 기반 도움말이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-177">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="616a0-178">스크립트를 XML 기반 도움말 항목과 연결 하려면를 사용 합니다. ExternalHelp 도움말 주석 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-178">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="616a0-179">ExternalHelp 키워드에 대 한 자세한 내용은 [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-179">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="616a0-180">XML 기반 도움말에 대 한 자세한 내용은 [Cmdlet 도움말을 작성 하는 방법](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="616a0-180">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="616a0-181">종료 값 반환</span><span class="sxs-lookup"><span data-stu-id="616a0-181">Returning an exit value</span></span>

<span data-ttu-id="616a0-182">기본적으로 스크립트는 스크립트가 종료 될 때 종료 상태를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-182">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="616a0-183">문을 사용 하 여 `exit` 스크립트에서 종료 코드를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-183">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="616a0-184">기본적으로 문은를 `exit` 반환 `0` 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-184">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="616a0-185">숫자 값을 제공 하 여 다른 종료 상태를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-185">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="616a0-186">0이 아닌 종료 코드는 일반적으로 오류를 신호로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-186">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="616a0-187">Windows에서는와 사이의 숫자가 모두 `[int]::MinValue` `[int]::MaxValue` 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-187">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>

<span data-ttu-id="616a0-188">Unix에서는 `[byte]::MinValue` (0)에서 `[byte]::MaxValue` (255) 사이의 양수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-188">On Unix, only positive numbers between `[byte]::MinValue` (0) and `[byte]::MaxValue` (255) are allowed.</span></span> <span data-ttu-id="616a0-189">부터 까지의 음수는를 `-1` `-255` 추가 하 여 양수 값으로 자동 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-189">A negative number in the range of `-1` through `-255` is automatically translated into a positive number by adding</span></span>
256. <span data-ttu-id="616a0-190">예를 들어 `-2` 는로 변환 됩니다 `254` .</span><span class="sxs-lookup"><span data-stu-id="616a0-190">For example, `-2` is transformed to `254`.</span></span>

<span data-ttu-id="616a0-191">PowerShell에서 `exit` 문은 변수의 값을 설정 `$LASTEXITCODE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-191">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="616a0-192">Windows 명령 셸 (cmd.exe)에서 exit 문은 환경 변수의 값을 설정 합니다 `%ERRORLEVEL%` .</span><span class="sxs-lookup"><span data-stu-id="616a0-192">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="616a0-193">숫자가 아니거나 플랫폼별 범위를 벗어난 인수는의 값으로 변환 됩니다 `0` .</span><span class="sxs-lookup"><span data-stu-id="616a0-193">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="616a0-194">스크립트 범위 및 점 소싱</span><span class="sxs-lookup"><span data-stu-id="616a0-194">Script scope and dot sourcing</span></span>

<span data-ttu-id="616a0-195">각 스크립트는 자체 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-195">Each script runs in its own scope.</span></span> <span data-ttu-id="616a0-196">스크립트에 생성 된 함수, 변수, 별칭 및 드라이브는 스크립트 범위에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-196">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="616a0-197">이러한 항목이 나 스크립트를 실행 하는 범위에서 해당 값에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-197">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="616a0-198">다른 범위에서 스크립트를 실행 하려면 전역 또는 로컬과 같은 범위를 지정 하거나 스크립트를 원본으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-198">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="616a0-199">점 소싱 기능을 사용 하면 스크립트 범위 대신 현재 범위에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-199">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="616a0-200">점 소스인 스크립트를 실행 하는 경우 스크립트의 명령은 명령 프롬프트에서 입력 한 것 처럼 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-200">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="616a0-201">스크립트에서 만드는 함수, 변수, 별칭 및 드라이브는 작업 하는 범위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-201">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="616a0-202">스크립트를 실행 한 후에는 생성 된 항목을 사용 하 여 세션에서 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-202">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="616a0-203">스크립트를 원본으로 만들려면 스크립트 경로 앞에 점 (.)과 공백을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-203">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="616a0-204">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-204">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="616a0-205">또는</span><span class="sxs-lookup"><span data-stu-id="616a0-205">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="616a0-206">스크립트가 실행 된 후에는 `UtilityFunctions.ps1` 스크립트에서 만드는 함수와 변수가 현재 범위에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-206">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="616a0-207">예를 들어 `UtilityFunctions.ps1` 스크립트는 `New-Profile` 함수와 변수를 만듭니다 `$ProfileName` .</span><span class="sxs-lookup"><span data-stu-id="616a0-207">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

<span data-ttu-id="616a0-208">스크립트를 `UtilityFunctions.ps1` 자체 스크립트 범위에서 실행 하는 경우 스크립트를 `New-Profile` `$ProfileName` 실행 하는 동안에만 함수와 변수가 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-208">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="616a0-209">스크립트가 종료 되 면 다음 예제와 같이 함수와 변수가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-209">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

<span data-ttu-id="616a0-210">스크립트의 소스를 표시 하 고 실행 하면 스크립트는 `New-Profile` 범위에서 함수 및 변수를 `$ProfileName` 세션에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-210">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="616a0-211">스크립트를 실행 한 후에는 `New-Profile` 다음 예제와 같이 세션에서 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-211">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

<span data-ttu-id="616a0-212">범위에 대 한 자세한 내용은 about_Scopes를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-212">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="616a0-213">모듈의 스크립트</span><span class="sxs-lookup"><span data-stu-id="616a0-213">Scripts in modules</span></span>

<span data-ttu-id="616a0-214">모듈은 하나의 단위로 배포할 수 있는 관련 된 PowerShell 리소스 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-214">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="616a0-215">모듈을 사용 하 여 스크립트, 함수 및 기타 리소스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-215">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="616a0-216">모듈을 사용 하 여 코드를 다른 사람에 게 배포 하 고 신뢰할 수 있는 소스에서 코드를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-216">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="616a0-217">스크립트를 모듈에 포함 하거나 스크립트와 지원 리소스를 완전히 또는 주로 구성 하는 모듈인 스크립트 모듈을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-217">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="616a0-218">스크립트 모듈은 .psm1 파일 확장명을 사용 하는 스크립트 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-218">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="616a0-219">모듈에 대 한 자세한 내용은 [about_Modules](about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-219">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="616a0-220">기타 스크립트 기능</span><span class="sxs-lookup"><span data-stu-id="616a0-220">Other script features</span></span>

<span data-ttu-id="616a0-221">PowerShell에는 스크립트에서 사용할 수 있는 많은 유용한 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-221">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="616a0-222">`#Requires` -문을 사용 하 여 `#Requires` 지정 된 모듈 또는 스냅인과 지정 된 버전의 PowerShell 없이 스크립트가 실행 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-222">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="616a0-223">자세한 내용은 about_Requires를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-223">For more information, see about_Requires.</span></span>

- <span data-ttu-id="616a0-224">`$PSCommandPath` -실행 중인 스크립트의 전체 경로와 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-224">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="616a0-225">이 매개 변수는 모든 스크립트에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-225">This parameter is valid in all scripts.</span></span> <span data-ttu-id="616a0-226">이 자동 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-226">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="616a0-227">`$PSScriptRoot` -스크립트가 실행 되는 디렉터리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-227">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="616a0-228">PowerShell 2.0에서이 변수는 스크립트 모듈 () 에서만 사용할 수 `.psm1` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-228">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="616a0-229">PowerShell 3.0부터 모든 스크립트에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-229">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="616a0-230">`$MyInvocation` - `$MyInvocation` 자동 변수는 현재 스크립트에 대 한 정보를 포함 하 여 시작 또는 "호출"에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-230">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="616a0-231">이 변수와 해당 속성을 사용 하 여 스크립트를 실행 하는 동안 스크립트에 대 한 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-231">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="616a0-232">예를 들면 `$MyInvocation` 입니다. MyCommand. Path 변수는 스크립트의 경로와 파일 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-232">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="616a0-233">`$MyInvocation`. 줄에는 모든 매개 변수 및 값을 포함 하 여 스크립트를 시작 하는 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-233">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="616a0-234">PowerShell 3.0부터에는 `$MyInvocation` 현재 스크립트를 호출 하거나 호출 하는 스크립트에 대 한 정보를 제공 하는 두 개의 새 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-234">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="616a0-235">이러한 속성의 값은 호출자 또는 호출자가 스크립트인 경우에만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-235">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="616a0-236">**Pscommandpath** 에는 현재 스크립트를 호출 하거나 호출한 스크립트의 전체 경로 및 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-236">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="616a0-237">**Psscriptroot** 에는 현재 스크립트를 호출 하거나 호출한 스크립트의 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-237">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="616a0-238">`$PSCommandPath` `$PSScriptRoot` 현재 스크립트에 대 한 정보를 포함 하는 및 자동 변수와 달리, **pscommandpath** 및 해당 변수의 **pscommandpath** 속성은 `$MyInvocation` 현재 스크립트를 호출한 스크립트에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-238">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="616a0-239">데이터 섹션-키워드를 사용 `Data` 하 여 스크립트의 논리에서 데이터를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-239">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="616a0-240">데이터 섹션도 지역화를 용이 하 게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-240">Data sections can also make localization easier.</span></span> <span data-ttu-id="616a0-241">자세한 내용은 [about_Data_Sections](about_Data_Sections.md) 및 [about_Script_Internationalization](about_Script_Internationalization.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-241">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="616a0-242">스크립트 서명-스크립트에 디지털 서명을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-242">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="616a0-243">실행 정책에 따라 디지털 서명을 사용 하 여 안전 하지 않은 명령을 포함할 수 있는 스크립트 실행을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="616a0-243">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="616a0-244">자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md) 및 [about_Signing](about_Signing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="616a0-244">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="616a0-245">참고 항목</span><span class="sxs-lookup"><span data-stu-id="616a0-245">See also</span></span>

[<span data-ttu-id="616a0-246">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="616a0-246">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="616a0-247">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="616a0-247">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="616a0-248">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="616a0-248">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="616a0-249">about_Functions</span><span class="sxs-lookup"><span data-stu-id="616a0-249">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="616a0-250">about_Modules</span><span class="sxs-lookup"><span data-stu-id="616a0-250">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="616a0-251">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="616a0-251">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="616a0-252">about_Requires</span><span class="sxs-lookup"><span data-stu-id="616a0-252">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="616a0-253">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="616a0-253">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="616a0-254">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="616a0-254">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="616a0-255">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="616a0-255">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="616a0-256">about_Signing</span><span class="sxs-lookup"><span data-stu-id="616a0-256">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="616a0-257">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="616a0-257">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)