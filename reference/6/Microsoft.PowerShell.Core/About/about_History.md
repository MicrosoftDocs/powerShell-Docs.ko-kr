---
description: 명령 기록에서 명령을 가져오고 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: e009b6d1ecd739c321bdc45e5b043cbdea392db0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221562"
---
# <a name="about-history"></a><span data-ttu-id="69b29-104">기록 정보</span><span class="sxs-lookup"><span data-stu-id="69b29-104">About History</span></span>

## <a name="short-description"></a><span data-ttu-id="69b29-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="69b29-105">Short Description</span></span>
<span data-ttu-id="69b29-106">명령 기록에서 명령을 가져오고 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-106">Describes how to get and run commands in the command history.</span></span>

## <a name="long-description"></a><span data-ttu-id="69b29-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="69b29-107">Long Description</span></span>

<span data-ttu-id="69b29-108">명령 프롬프트에서 명령을 입력 하면 PowerShell에서 명령 기록에 명령을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-108">When you enter a command at the command prompt, PowerShell saves the command in the command history.</span></span> <span data-ttu-id="69b29-109">기록의 명령을 작업 레코드로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-109">You can use the commands in the history as a record of your work.</span></span> <span data-ttu-id="69b29-110">명령 기록에서 명령을 회수 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-110">And, you can recall and run the commands from the command history.</span></span>

<span data-ttu-id="69b29-111">PowerShell에는 기본 제공 기록과 **Psreadline** 모듈에서 관리 하는 기록과 같은 두 가지 기록 공급자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-111">PowerShell has two different history providers: the built-in history and the history managed by the **PSReadLine** module.</span></span> <span data-ttu-id="69b29-112">기록은 별도로 관리 되지만 **Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-112">The histories are managed separately, but both histories are available in sessions where **PSReadLine** is loaded.</span></span>

## <a name="using-the-psreadline-history"></a><span data-ttu-id="69b29-113">PSReadLine 기록 사용</span><span class="sxs-lookup"><span data-stu-id="69b29-113">Using the PSReadLine history</span></span>

<span data-ttu-id="69b29-114">PSReadLine 기록은 모든 PowerShell 세션에서 사용 되는 명령을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-114">The PSReadLine history tracks the commands used in all PowerShell sessions.</span></span>
<span data-ttu-id="69b29-115">기록은 호스트 당 중앙 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-115">The history is written to a central file per host.</span></span> <span data-ttu-id="69b29-116">모든 세션에서 기록 파일을 사용할 수 있으며 모든 과거 기록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-116">That history file is available to all sessions and contains all past history.</span></span> <span data-ttu-id="69b29-117">세션이 종료 되 면 기록이 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-117">The history is not deleted when the session ends.</span></span> <span data-ttu-id="69b29-118">또한 cmdlet으로 해당 기록을 관리할 수 없습니다 `*-History` .</span><span class="sxs-lookup"><span data-stu-id="69b29-118">Also, that history cannot be managed by the `*-History` cmdlets.</span></span> <span data-ttu-id="69b29-119">자세한 내용은 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69b29-119">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

## <a name="using-the-built-in-session-history"></a><span data-ttu-id="69b29-120">기본 제공 세션 기록 사용</span><span class="sxs-lookup"><span data-stu-id="69b29-120">Using the built-in session history</span></span>

<span data-ttu-id="69b29-121">기본 제공 기록은 현재 세션에 사용 된 명령만 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-121">The built-in history only tracks the commands used in the current session.</span></span> <span data-ttu-id="69b29-122">다른 세션에서 기록을 사용할 수 없으며 세션이 종료 될 때 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-122">The history is not available to other sessions and is deleted when the session ends.</span></span>

### <a name="history-cmdlets"></a><span data-ttu-id="69b29-123">기록 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69b29-123">History Cmdlets</span></span>

<span data-ttu-id="69b29-124">PowerShell에는 명령 기록을 관리 하는 cmdlet 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-124">PowerShell has a set of cmdlets that manage the command history.</span></span>

| <span data-ttu-id="69b29-125">cmdlet</span><span class="sxs-lookup"><span data-stu-id="69b29-125">Cmdlet</span></span>           | <span data-ttu-id="69b29-126">Alias</span><span class="sxs-lookup"><span data-stu-id="69b29-126">Alias</span></span>  | <span data-ttu-id="69b29-127">설명</span><span class="sxs-lookup"><span data-stu-id="69b29-127">Description</span></span>                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | <span data-ttu-id="69b29-128">명령 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-128">Gets the command history.</span></span>                  |
| `Invoke-History` | `r`    | <span data-ttu-id="69b29-129">명령 기록에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-129">Runs a command in the command history.</span></span>     |
| `Add-History`    |        | <span data-ttu-id="69b29-130">명령 기록에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-130">Adds a command to the command history.</span></span>     |
| `Clear-History`  | `clhy` | <span data-ttu-id="69b29-131">명령 기록에서 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-131">Deletes commands from the command history.</span></span> |

### <a name="keyboard-shortcuts-for-managing-history"></a><span data-ttu-id="69b29-132">기록 관리를 위한 바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="69b29-132">Keyboard Shortcuts for Managing History</span></span>

<span data-ttu-id="69b29-133">PowerShell 콘솔에서 다음 바로 가기를 사용 하 여 명령 기록을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-133">In the PowerShell console, you can use the following shortcuts to manage the command history.</span></span>

- <span data-ttu-id="69b29-134"><kbd>Uparrow</kbd> -이전 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-134"><kbd>UpArrow</kbd> - Displays the previous command.</span></span>
- <span data-ttu-id="69b29-135"><kbd>아래쪽 화살표</kbd> -다음 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-135"><kbd>DownArrow</kbd> - Displays the next command.</span></span>
- <span data-ttu-id="69b29-136"><kbd>F7</kbd> -명령 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-136"><kbd>F7</kbd> - Displays the command history.</span></span>
- <span data-ttu-id="69b29-137"><kbd>ESC</kbd> -기록을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-137"><kbd>ESC</kbd> - To hide the history.</span></span>
- <span data-ttu-id="69b29-138"><kbd>F8</kbd> -명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-138"><kbd>F8</kbd> - Finds a command.</span></span> <span data-ttu-id="69b29-139">하나 이상의 문자를 입력 한 다음 <kbd>f8</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-139">Type one or more characters then press <kbd>F8</kbd>.</span></span> <span data-ttu-id="69b29-140">다음 인스턴스로 <kbd>F8</kbd> 키를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-140">Press <kbd>F8</kbd> again the next instance.</span></span>
- <span data-ttu-id="69b29-141"><kbd>F9</kbd> -기록 ID로 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-141"><kbd>F9</kbd> - Find a command by history ID.</span></span> <span data-ttu-id="69b29-142">기록 ID를 입력 하 고 <kbd>f9</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-142">Type the history ID then press <kbd>F9</kbd>.</span></span> <span data-ttu-id="69b29-143"><kbd>F7</kbd> 키를 눌러 ID를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-143">Press <kbd>F7</kbd> to find the ID.</span></span>
- <span data-ttu-id="69b29-144"><kbd>#</kbd>`<string>`</kbd>의 기록을 <kbd>탭</kbd> 하 여 검색 `*<string>*` 하 고 가장 최근의 일치 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-144"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> - Search the history for `*<string>*` and returns the most recent match.</span></span> <span data-ttu-id="69b29-145"><kbd>Tab</kbd> 키를 반복 해 서 누르면 기록에서 일치 하는 항목을 순환 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-145">If you press <kbd>Tab</kbd> repeatedly, it cycles through the matching items in your history.</span></span>

> [!NOTE]
> <span data-ttu-id="69b29-146">이러한 키 바인딩은 콘솔 호스트 응용 프로그램에 의해 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-146">These key bindings are implemented by the console host application.</span></span> <span data-ttu-id="69b29-147">Visual Studio Code 또는 Windows Terminal와 같은 다른 응용 프로그램은 다른 키 바인딩을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-147">Other applications, such as Visual Studio Code or Windows Terminal, can have different key bindings.</span></span> <span data-ttu-id="69b29-148">이 바인딩은 PSReadLine 모듈에 의해 재정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-148">The bindings can be overridden by the PSReadLine module.</span></span> <span data-ttu-id="69b29-149">PSReadLine은 PowerShell 세션을 시작할 때 자동으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-149">PSReadLine loads automatically when you start a PowerShell session.</span></span>
> <span data-ttu-id="69b29-150">PSReadLine이 로드 된 상태에서 <kbd>F7</kbd> 및 <kbd>F9</kbd> 는 함수에 바인딩되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-150">With PSReadLine loaded, <kbd>F7</kbd> and <kbd>F9</kbd> are not bound to any function.</span></span> <span data-ttu-id="69b29-151">PSReadLine은 동등한 기능을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-151">PSReadLine does not provide equivalent functionality.</span></span> <span data-ttu-id="69b29-152">자세한 내용은 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69b29-152">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="69b29-153">MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="69b29-153">MaximumHistoryCount</span></span>

<span data-ttu-id="69b29-154">`$MaximumHistoryCount`기본 설정 변수는 PowerShell이 명령 기록에 저장 하는 최대 명령 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-154">The `$MaximumHistoryCount` preference variable determines the maximum number of commands that PowerShell saves in the command history.</span></span> <span data-ttu-id="69b29-155">기본값</span><span class="sxs-lookup"><span data-stu-id="69b29-155">The default value is</span></span>
4096.

<span data-ttu-id="69b29-156">예를 들어 다음 명령은 `$MaximumHistoryCount` 를 100 명령으로 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-156">For example, the following command lowers the `$MaximumHistoryCount` to 100 commands:</span></span>

```powershell
$MaximumHistoryCount = 100
```

<span data-ttu-id="69b29-157">설정을 적용 하려면 PowerShell을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-157">To apply the setting, restart PowerShell.</span></span>

<span data-ttu-id="69b29-158">모든 PowerShell 세션에 대 한 새 변수 값을 저장 하려면 PowerShell 프로필에 할당 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-158">To save the new variable value for all your PowerShell sessions, add the assignment statement to a PowerShell profile.</span></span> <span data-ttu-id="69b29-159">프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b29-159">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="69b29-160">기본 설정 변수에 대 한 자세한 내용은 `$MaximumHistoryCount` [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69b29-160">For more information about the `$MaximumHistoryCount` preference variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="order-of-commands-in-the-history"></a><span data-ttu-id="69b29-161">기록의 명령 순서</span><span class="sxs-lookup"><span data-stu-id="69b29-161">Order of Commands in the History</span></span>

<span data-ttu-id="69b29-162">명령을 입력 하는 경우가 아니라 명령이 실행을 완료 하면 기록에 명령이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-162">Commands are added to the history when the command finishes executing, not when the command is entered.</span></span> <span data-ttu-id="69b29-163">명령을 완료 하는 데 시간이 오래 걸리고 명령이 중첩 된 프롬프트에서 실행 되는 경우 해당 명령은 기록에서 순서가 잘못 된 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-163">If commands take some time to be completed, or if the commands are executing in a nested prompt, the commands might appear to be out of order in the history.</span></span> <span data-ttu-id="69b29-164">중첩 된 프롬프트에서 실행 되는 명령은 프롬프트 수준을 종료 하는 경우에만 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b29-164">Commands that are executing in a nested prompt are completed only when you exit the prompt level.</span></span>

## <a name="see-also"></a><span data-ttu-id="69b29-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69b29-165">See Also</span></span>

- [<span data-ttu-id="69b29-166">about_Line_Editing</span><span class="sxs-lookup"><span data-stu-id="69b29-166">about_Line_Editing</span></span>](about_Line_Editing.md)
- [<span data-ttu-id="69b29-167">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="69b29-167">about_Preference_Variables</span></span>](about_Preference_Variables.md)
- [<span data-ttu-id="69b29-168">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="69b29-168">about_Profiles</span></span>](about_Profiles.md)
- [<span data-ttu-id="69b29-169">about_Variables</span><span class="sxs-lookup"><span data-stu-id="69b29-169">about_Variables</span></span>](about_Variables.md)
- [<span data-ttu-id="69b29-170">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="69b29-170">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)
