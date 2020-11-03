---
description: 함수에 대해 설명 하 `Prompt` 고 사용자 지정 함수를 만드는 방법을 보여 줍니다 `Prompt` .
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 15746fe1ce2c79189dd604b5b6244e337ad389a1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222626"
---
# <a name="about-prompts"></a><span data-ttu-id="0def4-104">프롬프트 정보</span><span class="sxs-lookup"><span data-stu-id="0def4-104">About Prompts</span></span>

## <a name="short-description"></a><span data-ttu-id="0def4-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="0def4-105">Short description</span></span>
<span data-ttu-id="0def4-106">함수에 대해 설명 하 `Prompt` 고 사용자 지정 함수를 만드는 방법을 보여 줍니다 `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="0def4-106">Describes the `Prompt` function and demonstrates how to create a custom `Prompt` function.</span></span>

## <a name="long-description"></a><span data-ttu-id="0def4-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-107">Long description</span></span>

<span data-ttu-id="0def4-108">PowerShell 명령 프롬프트는 PowerShell이 명령을 실행할 준비가 되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-108">The PowerShell command prompt indicates that PowerShell is ready to run a command:</span></span>

```
PS C:\>
```

<span data-ttu-id="0def4-109">PowerShell 프롬프트는 기본 제공 함수에 의해 결정 됩니다 `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="0def4-109">The PowerShell prompt is determined by the built-in `Prompt` function.</span></span> <span data-ttu-id="0def4-110">사용자 고유의 함수를 만들고 `Prompt` PowerShell 프로필에 저장 하 여 프롬프트를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-110">You can customize the prompt by creating your own `Prompt` function and saving it in your PowerShell profile.</span></span>

## <a name="about-the-prompt-function"></a><span data-ttu-id="0def4-111">Prompt 함수 정보</span><span class="sxs-lookup"><span data-stu-id="0def4-111">About the Prompt function</span></span>

<span data-ttu-id="0def4-112">`Prompt`함수는 PowerShell 프롬프트의 모양을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-112">The `Prompt` function determines the appearance of the PowerShell prompt.</span></span>
<span data-ttu-id="0def4-113">PowerShell은 기본 제공 함수와 함께 제공 `Prompt` 되지만 사용자 고유의 함수를 정의 하 여 재정의할 수 있습니다 `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="0def4-113">PowerShell comes with a built-in `Prompt` function, but you can override it by defining your own `Prompt` function.</span></span>

<span data-ttu-id="0def4-114">함수에는 `Prompt` 다음 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-114">The `Prompt` function has the following syntax:</span></span>

```powershell
function Prompt { <function-body> }
```

<span data-ttu-id="0def4-115">`Prompt`함수는 개체를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-115">The `Prompt` function must return an object.</span></span> <span data-ttu-id="0def4-116">문자열 또는 문자열로 형식이 지정 된 개체를 반환 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-116">As a best practice, return a string or an object that is formatted as a string.</span></span> <span data-ttu-id="0def4-117">권장 되는 최대 길이는 80 자입니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-117">The maximum recommended length is 80 characters.</span></span>

<span data-ttu-id="0def4-118">예를 들어 다음 `Prompt` 함수는 "Hello, 세계" 문자열, 오른쪽 꺾쇠 괄호 ()를 차례로 반환 합니다 `>` .</span><span class="sxs-lookup"><span data-stu-id="0def4-118">For example, the following `Prompt` function returns a "Hello, World" string followed by a  right angle bracket (`>`).</span></span>

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a><span data-ttu-id="0def4-119">프롬프트 함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="0def4-119">Getting the Prompt function</span></span>

<span data-ttu-id="0def4-120">함수를 가져오려면 `Prompt` cmdlet을 사용 `Get-Command` 하거나 `Get-Item` 함수 드라이브에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-120">To get the `Prompt` function, use the `Get-Command` cmdlet or use the `Get-Item` cmdlet in the Function drive.</span></span>

<span data-ttu-id="0def4-121">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="0def4-121">For example:</span></span>

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

<span data-ttu-id="0def4-122">프롬프트의 값을 설정 하는 스크립트를 가져오려면 점 메서드를 사용 하 여 함수의 **ScriptBlock** 속성을 가져옵니다 `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="0def4-122">To get the script that sets the value of the prompt, use the dot method to get the **ScriptBlock** property of the `Prompt` function.</span></span>

<span data-ttu-id="0def4-123">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="0def4-123">For example:</span></span>

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

<span data-ttu-id="0def4-124">모든 함수와 마찬가지로 함수는 `Prompt` 드라이브에 저장 됩니다 `Function:` .</span><span class="sxs-lookup"><span data-stu-id="0def4-124">Like all functions, the `Prompt` function is stored in the `Function:` drive.</span></span>
<span data-ttu-id="0def4-125">현재 함수를 만드는 스크립트를 표시 하려면 `Prompt` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-125">To display the script that creates the current `Prompt` function, type:</span></span>

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a><span data-ttu-id="0def4-126">기본 프롬프트</span><span class="sxs-lookup"><span data-stu-id="0def4-126">The default prompt</span></span>

<span data-ttu-id="0def4-127">기본 프롬프트는 `Prompt` 함수가 오류를 생성 하거나 개체를 반환 하지 않는 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-127">The default prompt appears only when the `Prompt` function generates an error or does not return an object.</span></span>

<span data-ttu-id="0def4-128">기본 PowerShell 프롬프트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-128">The default PowerShell prompt is:</span></span>

```
PS>
```

<span data-ttu-id="0def4-129">예를 들어 다음 명령은 함수를 잘못 된로 설정 합니다 `Prompt` `$null` .</span><span class="sxs-lookup"><span data-stu-id="0def4-129">For example, the following command sets the `Prompt` function to `$null`, which is invalid.</span></span> <span data-ttu-id="0def4-130">따라서 기본 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-130">As a result, the default prompt appears.</span></span>

```powershell
PS C:\> function prompt {$null}
PS>
```

<span data-ttu-id="0def4-131">PowerShell에는 기본 제공 프롬프트가 제공 되므로 일반적으로 기본 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-131">Because PowerShell comes with a built-in prompt, you usually do not see the default prompt.</span></span>

### <a name="built-in-prompt"></a><span data-ttu-id="0def4-132">기본 제공 프롬프트</span><span class="sxs-lookup"><span data-stu-id="0def4-132">Built-in prompt</span></span>

<span data-ttu-id="0def4-133">PowerShell에는 기본 제공 함수가 포함 되어 있습니다 `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="0def4-133">PowerShell includes a built-in `Prompt` function.</span></span>

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="0def4-134">함수는 cmdlet을 사용 하 여 `Test-Path` 자동 변수가 채워졌는지 여부를 확인 합니다 `$PSDebugContext` .</span><span class="sxs-lookup"><span data-stu-id="0def4-134">The function uses the `Test-Path` cmdlet to determine whether the `$PSDebugContext` automatic variable is populated.</span></span> <span data-ttu-id="0def4-135">`$PSDebugContext`가 채워지면 디버깅 모드에 있으며 다음과 `[DBG]:` 같이 프롬프트에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-135">If `$PSDebugContext` is populated, you are in debugging mode, and `[DBG]:` is added to the prompt, as follows:</span></span>

```Output
[DBG]: PS C:\ps-test>
```

<span data-ttu-id="0def4-136">`$PSDebugContext`가 채워지지 않은 경우 함수는 `PS` 프롬프트에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-136">If `$PSDebugContext` is not populated, the function adds `PS` to the prompt.</span></span>
<span data-ttu-id="0def4-137">그리고 함수는 cmdlet을 사용 하 여 `Get-Location` 현재 파일 시스템 디렉터리 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-137">And, the function uses the `Get-Location` cmdlet to get the current file system directory location.</span></span> <span data-ttu-id="0def4-138">그런 다음 오른쪽 꺾쇠 괄호 ()를 추가 `>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-138">Then, it adds a right angle bracket (`>`).</span></span>

<span data-ttu-id="0def4-139">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="0def4-139">For example:</span></span>

```Output
PS C:\ps-test>
```

<span data-ttu-id="0def4-140">중첩 된 프롬프트에 있는 경우 함수는 두 개의 꺾쇠 괄호 ( `>>` )를 프롬프트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-140">If you are in a nested prompt, the function adds two angle brackets (`>>`) to the prompt.</span></span> <span data-ttu-id="0def4-141">`$NestedPromptLevel`자동 변수 값이 1 보다 크면 중첩 된 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-141">(You are in a nested prompt if the value of the `$NestedPromptLevel` automatic variable is greater than 1.)</span></span>

<span data-ttu-id="0def4-142">예를 들어, 중첩 된 프롬프트에서 디버깅 하는 경우 프롬프트는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-142">For example, when you are debugging in a nested prompt, the prompt resembles the following prompt:</span></span>

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a><span data-ttu-id="0def4-143">프롬프트에 대 한 변경 내용</span><span class="sxs-lookup"><span data-stu-id="0def4-143">Changes to the prompt</span></span>

<span data-ttu-id="0def4-144">`Enter-PSSession`Cmdlet은 원격 컴퓨터의 이름을 현재 함수 앞에 앞에 추가할 수 `Prompt` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-144">The `Enter-PSSession` cmdlet prepends the name of the remote computer to the current `Prompt` function.</span></span> <span data-ttu-id="0def4-145">Cmdlet을 사용 하 여 `Enter-PSSession` 원격 컴퓨터에서 세션을 시작 하는 경우 명령 프롬프트는 원격 컴퓨터의 이름을 포함 하도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-145">When you use the `Enter-PSSession` cmdlet to start a session with a remote computer, the command prompt changes to include the name of the remote computer.</span></span> <span data-ttu-id="0def4-146">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="0def4-146">For example:</span></span>

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

<span data-ttu-id="0def4-147">다른 PowerShell 호스트 응용 프로그램 및 대체 셸에는 고유한 사용자 지정 명령 프롬프트가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-147">Other PowerShell host applications and alternate shells might have their own custom command prompts.</span></span>

<span data-ttu-id="0def4-148">및 자동 변수에 대 한 자세한 내용은 `$PSDebugContext` `$NestedPromptLevel` [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0def4-148">For more information about the `$PSDebugContext` and `$NestedPromptLevel` automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

### <a name="how-to-customize-the-prompt"></a><span data-ttu-id="0def4-149">프롬프트를 사용자 지정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0def4-149">How to customize the prompt</span></span>

<span data-ttu-id="0def4-150">프롬프트를 사용자 지정 하려면 새 함수를 작성 `Prompt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-150">To customize the prompt, write a new `Prompt` function.</span></span> <span data-ttu-id="0def4-151">함수는 보호 되지 않으므로 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-151">The function is not protected, so you can overwrite it.</span></span>

<span data-ttu-id="0def4-152">함수를 작성 하려면 `Prompt` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-152">To write a `Prompt` function, type the following:</span></span>

```powershell
function prompt { }
```

<span data-ttu-id="0def4-153">그런 다음 중괄호 사이에 프롬프트를 생성 하는 문자열이 나 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-153">Then, between the braces, enter the commands or the string that creates your prompt.</span></span>

<span data-ttu-id="0def4-154">예를 들어 다음 프롬프트에는 컴퓨터 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-154">For example, the following prompt includes your computer name:</span></span>

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

<span data-ttu-id="0def4-155">Server01 컴퓨터에서 프롬프트는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-155">On the Server01 computer, the prompt resembles the following prompt:</span></span>

```Output
PS [Server01] >
```

<span data-ttu-id="0def4-156">다음 `Prompt` 함수는 현재 날짜 및 시간을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-156">The following `Prompt` function includes the current date and time:</span></span>

```powershell
function prompt {"$(Get-Date)> "}
```

<span data-ttu-id="0def4-157">프롬프트는 다음 프롬프트와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-157">The prompt resembles the following prompt:</span></span>

```Output
03/15/2012 17:49:47>
```

<span data-ttu-id="0def4-158">또한 기본 함수를 변경할 수 있습니다 `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="0def4-158">You can also change the default `Prompt` function:</span></span>

<span data-ttu-id="0def4-159">예를 들어 다음 수정 된 `Prompt` 함수는 `[ADMIN]:` **관리자 권한으로 실행** 옵션을 사용 하 여 powershell을 열 때 기본 제공 powershell 프롬프트에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-159">For example, the following modified `Prompt` function adds `[ADMIN]:` to the built-in PowerShell prompt when PowerShell is opened by using the **Run as administrator** option:</span></span>

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="0def4-160">**관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 하는 경우 다음과 같은 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-160">When you start PowerShell by using the **Run as administrator** option, a prompt that resembles the following prompt appears:</span></span>

```Output
[ADMIN]: PS C:\ps-test>
```

<span data-ttu-id="0def4-161">다음 `Prompt` 함수는 다음 명령의 기록 ID를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-161">The following `Prompt` function displays the history ID of the next command.</span></span> <span data-ttu-id="0def4-162">명령 기록을 보려면 cmdlet을 사용 합니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="0def4-162">To view the command history, use the `Get-History` cmdlet.</span></span>

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

<span data-ttu-id="0def4-163">다음 프롬프트는 및 cmdlet을 사용 하 여 `Write-Host` `Get-Random` 색을 임의로 변경 하는 프롬프트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-163">The following prompt uses the `Write-Host` and `Get-Random` cmdlets to create a prompt that changes color randomly.</span></span> <span data-ttu-id="0def4-164">는 `Write-Host` 현재 호스트 응용 프로그램에 기록 하지만 개체를 반환 하지 않기 때문에이 함수에는 문이 포함 됩니다 `Return` .</span><span class="sxs-lookup"><span data-stu-id="0def4-164">Because `Write-Host` writes to the current host application but does not return an object, this function includes a `Return` statement.</span></span> <span data-ttu-id="0def4-165">없는 경우 PowerShell은 기본 프롬프트를 사용 `PS>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-165">Without it, PowerShell uses the default prompt, `PS>`.</span></span>

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a><span data-ttu-id="0def4-166">프롬프트 함수 저장</span><span class="sxs-lookup"><span data-stu-id="0def4-166">Saving the Prompt function</span></span>

<span data-ttu-id="0def4-167">함수와 마찬가지로 `Prompt` 함수는 현재 세션에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-167">Like any function, the `Prompt` function exists only in the current session.</span></span> <span data-ttu-id="0def4-168">`Prompt`이후 세션을 위해 함수를 저장 하려면 PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0def4-168">To save the `Prompt` function for future sessions, add it to your PowerShell profiles.</span></span> <span data-ttu-id="0def4-169">프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0def4-169">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0def4-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0def4-170">See also</span></span>

[<span data-ttu-id="0def4-171">Get-Location</span><span class="sxs-lookup"><span data-stu-id="0def4-171">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)

[<span data-ttu-id="0def4-172">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="0def4-172">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="0def4-173">Get-History</span><span class="sxs-lookup"><span data-stu-id="0def4-173">Get-History</span></span>](xref:Microsoft.PowerShell.Core.Get-History)

[<span data-ttu-id="0def4-174">Get-Random</span><span class="sxs-lookup"><span data-stu-id="0def4-174">Get-Random</span></span>](xref:Microsoft.PowerShell.Utility.Get-Random)

[<span data-ttu-id="0def4-175">Write-Host</span><span class="sxs-lookup"><span data-stu-id="0def4-175">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)

[<span data-ttu-id="0def4-176">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="0def4-176">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="0def4-177">about_Functions</span><span class="sxs-lookup"><span data-stu-id="0def4-177">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="0def4-178">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="0def4-178">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="0def4-179">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="0def4-179">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="0def4-180">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="0def4-180">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
