---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: d3e3ee1dcde36ac09f8441aff7ce48797cf48b5f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214897"
---
# <span data-ttu-id="60f78-103">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="60f78-103">Set-PSReadLineOption</span></span>

## <span data-ttu-id="60f78-104">개요</span><span class="sxs-lookup"><span data-stu-id="60f78-104">Synopsis</span></span>
<span data-ttu-id="60f78-105">**Psreadline** 에서 명령줄 편집의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-105">Customizes the behavior of command line editing in **PSReadLine** .</span></span>

## <span data-ttu-id="60f78-106">구문</span><span class="sxs-lookup"><span data-stu-id="60f78-106">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="60f78-107">Description</span><span class="sxs-lookup"><span data-stu-id="60f78-107">Description</span></span>

<span data-ttu-id="60f78-108">`Set-PSReadLineOption`Cmdlet은 명령줄을 편집 하는 동안 **psreadline** 모듈의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-108">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="60f78-109">**Psreadline** 설정을 보려면를 사용 `Get-PSReadLineOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-109">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="60f78-110">예</span><span class="sxs-lookup"><span data-stu-id="60f78-110">Examples</span></span>

### <span data-ttu-id="60f78-111">예제 1: 전경색 및 배경색 설정</span><span class="sxs-lookup"><span data-stu-id="60f78-111">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="60f78-112">이 예제에서는 **Psreadline** 을 설정 하 여 녹색 전경 텍스트가 있는 **주석** 토큰을 회색 배경에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-112">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="60f78-113">예제에서 사용 된 이스케이프 시퀀스에서 **32** 은 전경색을 나타내고 **47** 은 배경색을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-113">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="60f78-114">전경 텍스트 색만 설정 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-114">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="60f78-115">예를 들어 **주석** 토큰의 밝은 녹색 전경 텍스트 색은입니다. ``"Comment"="`e[92m"``</span><span class="sxs-lookup"><span data-stu-id="60f78-115">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="60f78-116">예제 2: 벨 스타일 설정</span><span class="sxs-lookup"><span data-stu-id="60f78-116">Example 2: Set bell style</span></span>

<span data-ttu-id="60f78-117">이 예제에서 **Psreadline** 은 사용자 주의가 필요한 오류나 조건에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-117">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="60f78-118">**BellStyle** 는 60 밀리초 동안 1221 Hz에서 가청 경고음을 내보내도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-118">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="60f78-119">이 기능은 플랫폼의 모든 호스트에서 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-119">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="60f78-120">예제 3: 여러 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="60f78-120">Example 3: Set multiple options</span></span>

<span data-ttu-id="60f78-121">`Set-PSReadLineOption` 해시 테이블을 사용 하 여 여러 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-121">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

<span data-ttu-id="60f78-122">`$PSReadLineOptions`해시 테이블은 키와 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-122">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="60f78-123">`Set-PSReadLineOption` 에서 키와 값을 사용 하 여 `@PSReadLineOptions` **psreadline** 옵션을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-123">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="60f78-124">PowerShell 명령줄에서 해시 테이블 이름을 입력 하는 키와 값을 볼 수 있습니다 `$PSReadLineOptions` .</span><span class="sxs-lookup"><span data-stu-id="60f78-124">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="60f78-125">예제 4: 여러 색 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="60f78-125">Example 4: Set multiple color options</span></span>

<span data-ttu-id="60f78-126">이 예제에서는 단일 명령에서 두 개 이상의 색 값을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-126">This example shows how to set more than one color value in a single command.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### <span data-ttu-id="60f78-127">예 5: 여러 형식에 대 한 색 값 설정</span><span class="sxs-lookup"><span data-stu-id="60f78-127">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="60f78-128">이 예제에서는 **Psreadline** 에 표시 되는 토큰의 색을 설정 하는 방법에 대 한 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-128">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine** .</span></span>

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### <span data-ttu-id="60f78-129">예제 6: ViModeChangeHandler를 사용 하 여 Vi 모드 변경 내용 표시</span><span class="sxs-lookup"><span data-stu-id="60f78-129">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="60f78-130">이 예제에서는 **Vi** 모드 변경에 대 한 응답으로 커서 변경 VT 이스케이프를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-130">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="60f78-131">**OnViModeChange** 함수는 **Vi** 모드: insert 및 command에 대 한 커서 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-131">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="60f78-132">**ViModeChangeHandler** 는 공급자를 사용 하 여 `Function:` **OnViModeChange** 를 스크립트 블록 개체로 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-132">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="60f78-133">자세한 내용은 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60f78-133">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="60f78-134">매개 변수</span><span class="sxs-lookup"><span data-stu-id="60f78-134">Parameters</span></span>

### <span data-ttu-id="60f78-135">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="60f78-135">-AddToHistoryHandler</span></span>

<span data-ttu-id="60f78-136">**Psreadline** 기록에 추가 되는 명령을 제어 하는 **ScriptBlock** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-136">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="60f78-137">**ScriptBlock** 은 명령줄을 입력으로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-137">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="60f78-138">**ScriptBlock** 이를 반환 하는 경우 `$True` 명령줄이 기록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-138">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-139">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="60f78-139">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="60f78-140">이 옵션은 또는에서 실행 되는 경우와 같이 입력이 리디렉션되는 경우에만 Windows에 해당 `tmux` `screen` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-140">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="60f78-141">Windows에서 리디렉션된 입력을 사용 하면 많은 키가 이스케이프 문자에서 시작 하는 문자 시퀀스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-141">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="60f78-142">단일 이스케이프 문자 다음에 더 많은 문자와 유효한 이스케이프 시퀀스를 구분 하는 것은 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-142">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="60f78-143">터미널에서 사용자 유형 보다 더 빠르게 문자를 보낼 수 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-143">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="60f78-144">**Psreadline** 은 전체 이스케이프 시퀀스를 수신 하기 전에이 시간 제한 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-144">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="60f78-145">입력할 때 무작위 또는 예기치 않은 문자가 표시 되는 경우이 시간 제한을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-145">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-146">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="60f78-146">-BellStyle</span></span>

<span data-ttu-id="60f78-147">**Psreadline** 이 다양 한 오류 및 모호한 조건에 응답 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-147">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="60f78-148">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-148">The valid values are as follows:</span></span>

- <span data-ttu-id="60f78-149">**가청** : 짧은 경고음.</span><span class="sxs-lookup"><span data-stu-id="60f78-149">**Audible** : A short beep.</span></span>
- <span data-ttu-id="60f78-150">**시각적 개체** : 텍스트가 잠시 깜박입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-150">**Visual** : Text flashes briefly.</span></span>
- <span data-ttu-id="60f78-151">**없음** : 피드백이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-151">**None** : No feedback.</span></span>

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-152">-색</span><span class="sxs-lookup"><span data-stu-id="60f78-152">-Colors</span></span>

<span data-ttu-id="60f78-153">**Colors** 매개 변수는 **psreadline** 에서 사용 되는 다양 한 색을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-153">The **Colors** parameter specifies various colors used by **PSReadLine** .</span></span>

<span data-ttu-id="60f78-154">인수는 키에서 색을 지정 하는 요소와 값을 지정 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-154">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="60f78-155">자세한 내용은 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f78-155">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="60f78-156">색은 **ConsoleColor** 의 값 (예: `[ConsoleColor]::Red` 또는 유효한 ANSI 이스케이프 시퀀스) 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-156">Colors can be either a value from **ConsoleColor** , for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="60f78-157">유효한 이스케이프 시퀀스는 터미널에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-157">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="60f78-158">PowerShell 5.0에서 빨강 텍스트에 대 한 예제 이스케이프 시퀀스는 `$([char]0x1b)[91m` 입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-158">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="60f78-159">PowerShell 6 이상에서 같은 이스케이프 시퀀스는 `` `e[91m`` 입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-159">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="60f78-160">다음 형식을 포함 하 여 다른 이스케이프 시퀀스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-160">You can specify other escape sequences including the following types:</span></span>

- <span data-ttu-id="60f78-161">256 색</span><span class="sxs-lookup"><span data-stu-id="60f78-161">256 color</span></span>
- <span data-ttu-id="60f78-162">24 비트 색</span><span class="sxs-lookup"><span data-stu-id="60f78-162">24-bit color</span></span>
- <span data-ttu-id="60f78-163">전경, 배경 또는 둘 다</span><span class="sxs-lookup"><span data-stu-id="60f78-163">Foreground, background, or both</span></span>
- <span data-ttu-id="60f78-164">반전, 굵게</span><span class="sxs-lookup"><span data-stu-id="60f78-164">Inverse, bold</span></span>

<span data-ttu-id="60f78-165">ANSI 색 코드에 대 한 자세한 내용은 위키백과의 [ansi 이스케이프 코드](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f78-165">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="60f78-166">유효한 키는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-166">The valid keys include:</span></span>

- <span data-ttu-id="60f78-167">**ContinuationPrompt** : 연속 프롬프트의 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-167">**ContinuationPrompt** : The color of the continuation prompt.</span></span>
- <span data-ttu-id="60f78-168">**강조** : 강조 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-168">**Emphasis** : The emphasis color.</span></span> <span data-ttu-id="60f78-169">예를 들어 기록을 검색할 때 일치 하는 텍스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-169">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="60f78-170">**오류** : 오류 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-170">**Error** : The error color.</span></span> <span data-ttu-id="60f78-171">예를 들어 프롬프트에서을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-171">For example, in the prompt.</span></span>
- <span data-ttu-id="60f78-172">**Selection** : 메뉴 선택 영역이 나 선택 된 텍스트를 강조 표시 하는 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-172">**Selection** : The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="60f78-173">**기본값** : 기본 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-173">**Default** : The default token color.</span></span>
- <span data-ttu-id="60f78-174">**Comment** : 주석 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-174">**Comment** : The comment token color.</span></span>
- <span data-ttu-id="60f78-175">**키워드** : 키워드 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-175">**Keyword** : The keyword token color.</span></span>
- <span data-ttu-id="60f78-176">**문자열** : 문자열 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-176">**String** : The string token color.</span></span>
- <span data-ttu-id="60f78-177">**Operator** : 연산자 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-177">**Operator** : The operator token color.</span></span>
- <span data-ttu-id="60f78-178">**Variable** : 변수 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-178">**Variable** : The variable token color.</span></span>
- <span data-ttu-id="60f78-179">**Command** : 명령 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-179">**Command** : The command token color.</span></span>
- <span data-ttu-id="60f78-180">**매개 변수** : 매개 변수 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-180">**Parameter** : The parameter token color.</span></span>
- <span data-ttu-id="60f78-181">**형식** : 형식 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-181">**Type** : The type token color.</span></span>
- <span data-ttu-id="60f78-182">**Number** : 숫자 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-182">**Number** : The number token color.</span></span>
- <span data-ttu-id="60f78-183">**Member** : 구성원 이름 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-183">**Member** : The member name token color.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-184">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="60f78-184">-CommandValidationHandler</span></span>

<span data-ttu-id="60f78-185">**Validateandacceptline** 에서 호출 되는 **ScriptBlock** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-185">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine** .</span></span> <span data-ttu-id="60f78-186">예외가 throw 되 면 유효성 검사가 실패 하 고 오류가 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-186">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="60f78-187">예외를 throw 하기 전에 유효성 검사 처리기는 오류 발생 지점에 커서를 놓고 쉽게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-187">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="60f78-188">유효성 검사 처리기는 일반적인 철자 오류를 수정 하기 위해와 같은 명령줄을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-188">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="60f78-189">**Validateandacceptline** 은 작업을 수행할 수 없는 명령을 사용 하 여 기록의 복잡 한 문제를 방지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-189">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-190">-전체 Queryitems</span><span class="sxs-lookup"><span data-stu-id="60f78-190">-CompletionQueryItems</span></span>

<span data-ttu-id="60f78-191">메시지를 표시 하지 않고 표시 되는 최대 완료 항목 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-191">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="60f78-192">표시할 항목 수가이 값 보다 크면 **Psreadline** 은 완료 항목을 표시 하기 전에 **예/아니요** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-192">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-193">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="60f78-193">-ContinuationPrompt</span></span>

<span data-ttu-id="60f78-194">여러 줄 입력을 입력할 때 다음 줄의 시작 부분에 표시 되는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-194">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="60f78-195">기본값은 이중 보다 큼 기호 ( `>>` )입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-195">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="60f78-196">빈 문자열이 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-196">An empty string is valid.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-197">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="60f78-197">-DingDuration</span></span>

<span data-ttu-id="60f78-198">**BellStyle** 가 **가청** 으로 설정 된 경우 경고음의 기간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-198">Specifies the duration of the beep when **BellStyle** is set to **Audible** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-199">-DingTone</span><span class="sxs-lookup"><span data-stu-id="60f78-199">-DingTone</span></span>

<span data-ttu-id="60f78-200">**BellStyle** 가 **가청** 으로 설정 된 경우 경고음의 톤 (hz)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-200">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-201">-EditMode</span><span class="sxs-lookup"><span data-stu-id="60f78-201">-EditMode</span></span>

<span data-ttu-id="60f78-202">명령줄 편집 모드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-202">Specifies the command line editing mode.</span></span> <span data-ttu-id="60f78-203">이 매개 변수를 사용 하면에 의해 설정 된 모든 키 바인딩이 다시 설정 `Set-PSReadLineKeyHandler` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-203">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="60f78-204">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-204">The valid values are as follows:</span></span>

- <span data-ttu-id="60f78-205">**Windows** : 키 바인딩은 PowerShell, Cmd 및 Visual Studio를 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-205">**Windows** : Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="60f78-206">**Emacs** : 키 바인딩은 Bash 또는 Emacs을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-206">**Emacs** : Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="60f78-207">**Vi** : 키 바인딩은 Vi를 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-207">**Vi** : Key bindings emulate Vi.</span></span>

<span data-ttu-id="60f78-208">`Get-PSReadLineKeyHandler`현재 구성 된 **EditMode** 의 키 바인딩을 보려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-208">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode** .</span></span>

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-209">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="60f78-209">-ExtraPromptLineCount</span></span>

<span data-ttu-id="60f78-210">추가 줄의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-210">Specifies the number of extra lines.</span></span>

<span data-ttu-id="60f78-211">프롬프트가 두 줄 이상으로 확장 되는 경우이 매개 변수의 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-211">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="60f78-212">**Psreadline** 에서 일부 출력을 표시 한 후에 프롬프트가 표시 될 때 추가 줄을 사용 하려면이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-212">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="60f78-213">예를 들어 **Psreadline** 은 완료 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-213">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="60f78-214">이 옵션은 이전 버전의 **Psreadline** 에서 보다 더 필요 하지만 함수를 사용 하는 경우에 유용 `InvokePrompt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-214">This option is needed less than in previous versions of **PSReadLine** , but is useful when the `InvokePrompt` function is used.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-215">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="60f78-215">-HistoryNoDuplicates</span></span>

<span data-ttu-id="60f78-216">이 옵션은 회수 동작을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-216">This option controls the recall behavior.</span></span> <span data-ttu-id="60f78-217">중복 된 명령은 여전히 기록 파일에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-217">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="60f78-218">이 옵션을 설정 하면 명령을 회수할 때 가장 최근의 호출만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-218">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="60f78-219">회수 하는 동안 순서를 유지 하기 위해 기록에 반복 명령이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-219">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="60f78-220">그러나 기록을 회수 하거나 검색할 때 일반적으로 명령을 여러 번 표시 하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-220">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="60f78-221">기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistoryNoDuplicates** 속성은로 설정 됩니다 `True` .</span><span class="sxs-lookup"><span data-stu-id="60f78-221">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="60f78-222">이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-222">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="60f78-223">속성 값을 변경 하려면 다음과 같이 **Switchparameter** 값을 지정 해야 합니다 `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="60f78-223">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="60f78-224">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-224">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-225">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="60f78-225">-HistorySavePath</span></span>

<span data-ttu-id="60f78-226">기록이 저장 되는 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-226">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="60f78-227">Windows 또는 Windows 이외의 플랫폼을 실행 하는 컴퓨터는 다른 위치에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-227">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="60f78-228">파일 이름은 변수에 저장 됩니다 `$($host.Name)_history.txt` (예:) `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="60f78-228">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="60f78-229">이 매개 변수를 사용 하지 않는 경우 기본 경로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-229">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="60f78-230">**Windows**</span><span class="sxs-lookup"><span data-stu-id="60f78-230">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="60f78-231">**비 Windows**</span><span class="sxs-lookup"><span data-stu-id="60f78-231">**non-Windows**</span></span>

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-232">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="60f78-232">-HistorySaveStyle</span></span>

<span data-ttu-id="60f78-233">**Psreadline** 에서 기록을 저장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-233">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="60f78-234">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-234">Valid values are as follows:</span></span>

- <span data-ttu-id="60f78-235">**Saveincrementally** : 각 명령이 실행 된 후 기록을 저장 하 고 PowerShell의 여러 인스턴스 간에 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-235">**SaveIncrementally** : Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="60f78-236">**SaveAtExit** : PowerShell이 종료 될 때 기록 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-236">**SaveAtExit** : Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="60f78-237">**SaveNothing** : 기록 파일을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-237">**SaveNothing** : Don't use a history file.</span></span>

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-238">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="60f78-238">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="60f78-239">**ReverseSearchHistory** 또는 **HistorySearchBackward** 와 같은 함수에서 기록 검색에서 대/소문자를 구분 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-239">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward** .</span></span>

<span data-ttu-id="60f78-240">기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistorySearchCaseSensitive** 속성은로 설정 됩니다 `False` .</span><span class="sxs-lookup"><span data-stu-id="60f78-240">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="60f78-241">이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-241">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="60f78-242">속성 값을 다시 변경 하려면 **Switchparameter** 의 값을 다음과 같이 지정 해야 합니다 `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="60f78-242">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="60f78-243">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-243">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-244">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="60f78-244">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="60f78-245">검색을 사용 하 여 기록에서 로드 하는 명령의 끝으로 커서를 이동 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-245">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="60f78-246">이 매개 변수를로 설정 하면 `$False` 위로 또는 아래로 화살표를 누를 때 커서가 있던 위치에 커서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-246">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="60f78-247">기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistorySearchCursorMovesToEnd** 속성은로 설정 됩니다 `False` .</span><span class="sxs-lookup"><span data-stu-id="60f78-247">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="60f78-248">이 **Switchparameter** 를 사용 하 여 속성 값을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-248">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="60f78-249">속성 값을 다시 변경 하려면 **Switchparameter** 의 값을 다음과 같이 지정 해야 합니다 `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="60f78-249">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="60f78-250">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-250">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-251">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="60f78-251">-MaximumHistoryCount</span></span>

<span data-ttu-id="60f78-252">**Psreadline** 기록에 저장할 최대 명령 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-252">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="60f78-253">**Psreadline** 기록은 PowerShell 기록과 별개입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-253">**PSReadLine** history is separate from PowerShell history.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-254">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="60f78-254">-MaximumKillRingCount</span></span>

<span data-ttu-id="60f78-255">Kill 링에 저장 된 최대 항목 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-255">Specifies the maximum number of items stored in the kill ring.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-256">-PromptText</span><span class="sxs-lookup"><span data-stu-id="60f78-256">-PromptText</span></span>

<span data-ttu-id="60f78-257">구문 분석 오류가 발생 하는 경우 **Psreadline** 은 프롬프트의 일부를 빨간색으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-257">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="60f78-258">**Psreadline** 은 프롬프트 함수를 분석 하 여 프롬프트 부분의 색만 변경 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-258">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="60f78-259">이 분석은 100% 안정적이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-259">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="60f78-260">**Psreadline** 에서 예기치 않은 방법으로 프롬프트를 변경 하는 경우이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-260">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="60f78-261">후행 공백을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-261">Include any trailing whitespace.</span></span>

<span data-ttu-id="60f78-262">예를 들어, 프롬프트 함수는 다음 예제와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-262">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="60f78-263">그런 다음 다음을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-263">Then set:</span></span>

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-264">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="60f78-264">-ShowToolTips</span></span>

<span data-ttu-id="60f78-265">가능한 완료를 표시 하면 도구 설명이 완성 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-265">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="60f78-266">기본적으로 이 옵션은 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-266">This option is enabled by default.</span></span> <span data-ttu-id="60f78-267">이 옵션은 이전 버전의 **Psreadline** 에서 기본적으로 사용 하도록 설정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-267">This option wasn't enabled by default in prior versions of **PSReadLine** .</span></span> <span data-ttu-id="60f78-268">사용 하지 않도록 설정 하려면이 옵션을로 설정 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-268">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="60f78-269">기본적으로 전역 **PSConsoleReadLineOptions** 개체의 **showtooltips** 속성은로 설정 됩니다 `True` .</span><span class="sxs-lookup"><span data-stu-id="60f78-269">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="60f78-270">이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-270">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="60f78-271">속성 값을 변경 하려면 다음과 같이 **Switchparameter** 값을 지정 해야 합니다 `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="60f78-271">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="60f78-272">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-272">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-273">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="60f78-273">-ViModeChangeHandler</span></span>

<span data-ttu-id="60f78-274">**Vimodeindicator** 로 설정 된 경우 `Script` 모드가 변경 될 때마다 제공 된 스크립트 블록이 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-274">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="60f78-275">스크립트 블록은 형식의 인수 하나를 제공 합니다 `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="60f78-275">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="60f78-276">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-276">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-277">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="60f78-277">-ViModeIndicator</span></span>

<span data-ttu-id="60f78-278">이 옵션은 현재 **Vi** 모드의 시각적 표시를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-278">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="60f78-279">삽입 모드 또는 명령 모드 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-279">Either insert mode or command mode.</span></span>

<span data-ttu-id="60f78-280">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-280">The valid values are as follows:</span></span>

- <span data-ttu-id="60f78-281">**없음** : 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-281">**None** : There's no indication.</span></span>
- <span data-ttu-id="60f78-282">**Prompt** : 프롬프트에서 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-282">**Prompt** : The prompt changes color.</span></span>
- <span data-ttu-id="60f78-283">**Cursor** : 커서 크기가 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-283">**Cursor** : The cursor changes size.</span></span>
- <span data-ttu-id="60f78-284">**스크립트** : 사용자 지정 텍스트가 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-284">**Script** : User-specified text is printed.</span></span>

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-285">-WordDelimiters 기호</span><span class="sxs-lookup"><span data-stu-id="60f78-285">-WordDelimiters</span></span>

<span data-ttu-id="60f78-286">**Forwardword** 또는 **KillWord** 같은 함수의 단어를 구분 하는 문자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-286">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f78-287">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="60f78-287">CommonParameters</span></span>

<span data-ttu-id="60f78-288">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="60f78-288">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="60f78-289">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60f78-289">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="60f78-290">입력</span><span class="sxs-lookup"><span data-stu-id="60f78-290">Inputs</span></span>

### <span data-ttu-id="60f78-291">없음</span><span class="sxs-lookup"><span data-stu-id="60f78-291">None</span></span>

<span data-ttu-id="60f78-292">개체를 파이프로 사용할 수 없습니다. `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="60f78-292">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="60f78-293">outputs</span><span class="sxs-lookup"><span data-stu-id="60f78-293">Outputs</span></span>

### <span data-ttu-id="60f78-294">없음</span><span class="sxs-lookup"><span data-stu-id="60f78-294">None</span></span>

<span data-ttu-id="60f78-295">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60f78-295">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="60f78-296">메모</span><span class="sxs-lookup"><span data-stu-id="60f78-296">Notes</span></span>

## <span data-ttu-id="60f78-297">관련 링크</span><span class="sxs-lookup"><span data-stu-id="60f78-297">Related links</span></span>

[<span data-ttu-id="60f78-298">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="60f78-298">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="60f78-299">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="60f78-299">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="60f78-300">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="60f78-300">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="60f78-301">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="60f78-301">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="60f78-302">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="60f78-302">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
