---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: cac2c2bb8ce1f3a28c0d91c7503b3ac4d038ccad
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "99601441"
---
# <span data-ttu-id="2562e-102">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2562e-102">Set-PSReadLineOption</span></span>

## <span data-ttu-id="2562e-103">개요</span><span class="sxs-lookup"><span data-stu-id="2562e-103">Synopsis</span></span>
<span data-ttu-id="2562e-104">**Psreadline** 에서 명령줄 편집의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-104">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="2562e-105">구문</span><span class="sxs-lookup"><span data-stu-id="2562e-105">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func`2[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action`1[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-PredictionSource <PredictionSource>]
 [-PredictionViewStyle <PredictionViewStyle>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="2562e-106">Description</span><span class="sxs-lookup"><span data-stu-id="2562e-106">Description</span></span>

<span data-ttu-id="2562e-107">`Set-PSReadLineOption`Cmdlet은 명령줄을 편집 하는 동안 **psreadline** 모듈의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-107">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="2562e-108">**Psreadline** 설정을 보려면를 사용 `Get-PSReadLineOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-108">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="2562e-109">예</span><span class="sxs-lookup"><span data-stu-id="2562e-109">Examples</span></span>

### <span data-ttu-id="2562e-110">예제 1: 전경색 및 배경색 설정</span><span class="sxs-lookup"><span data-stu-id="2562e-110">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="2562e-111">이 예제에서는 **Psreadline** 을 설정 하 여 녹색 전경 텍스트가 있는 **주석** 토큰을 회색 배경에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-111">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="2562e-112">예제에서 사용 된 이스케이프 시퀀스에서 **32** 은 전경색을 나타내고 **47** 은 배경색을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-112">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="2562e-113">전경 텍스트 색만 설정 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-113">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="2562e-114">예를 들어 **주석** 토큰의 밝은 녹색 전경 텍스트 색은입니다. ``"Comment"="`e[92m"``</span><span class="sxs-lookup"><span data-stu-id="2562e-114">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="2562e-115">예제 2: 벨 스타일 설정</span><span class="sxs-lookup"><span data-stu-id="2562e-115">Example 2: Set bell style</span></span>

<span data-ttu-id="2562e-116">이 예제에서 **Psreadline** 은 사용자 주의가 필요한 오류나 조건에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-116">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="2562e-117">**BellStyle** 는 60 밀리초 동안 1221 Hz에서 가청 경고음을 내보내도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-117">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="2562e-118">이 기능은 플랫폼의 모든 호스트에서 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-118">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="2562e-119">예제 3: 여러 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="2562e-119">Example 3: Set multiple options</span></span>

<span data-ttu-id="2562e-120">`Set-PSReadLineOption` 해시 테이블을 사용 하 여 여러 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-120">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

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

<span data-ttu-id="2562e-121">`$PSReadLineOptions`해시 테이블은 키와 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-121">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="2562e-122">`Set-PSReadLineOption` 에서 키와 값을 사용 하 여 `@PSReadLineOptions` **psreadline** 옵션을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-122">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="2562e-123">PowerShell 명령줄에서 해시 테이블 이름을 입력 하는 키와 값을 볼 수 있습니다 `$PSReadLineOptions` .</span><span class="sxs-lookup"><span data-stu-id="2562e-123">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="2562e-124">예제 4: 여러 색 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="2562e-124">Example 4: Set multiple color options</span></span>

<span data-ttu-id="2562e-125">이 예제에서는 단일 명령에서 두 개 이상의 색 값을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-125">This example shows how to set more than one color value in a single command.</span></span>

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

### <span data-ttu-id="2562e-126">예 5: 여러 형식에 대 한 색 값 설정</span><span class="sxs-lookup"><span data-stu-id="2562e-126">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="2562e-127">이 예제에서는 **Psreadline** 에 표시 되는 토큰의 색을 설정 하는 방법에 대 한 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-127">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

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

### <span data-ttu-id="2562e-128">예제 6: ViModeChangeHandler를 사용 하 여 Vi 모드 변경 내용 표시</span><span class="sxs-lookup"><span data-stu-id="2562e-128">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="2562e-129">이 예제에서는 **Vi** 모드 변경에 대 한 응답으로 커서 변경 VT 이스케이프를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-129">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

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

<span data-ttu-id="2562e-130">**OnViModeChange** 함수는 **Vi** 모드: insert 및 command에 대 한 커서 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-130">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="2562e-131">**ViModeChangeHandler** 는 공급자를 사용 하 여 `Function:` **OnViModeChange** 를 스크립트 블록 개체로 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-131">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="2562e-132">자세한 내용은 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2562e-132">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="2562e-133">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2562e-133">Parameters</span></span>

### <span data-ttu-id="2562e-134">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="2562e-134">-AddToHistoryHandler</span></span>

<span data-ttu-id="2562e-135">**Psreadline** 기록에 추가 되는 명령을 제어 하는 **ScriptBlock** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-135">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="2562e-136">**ScriptBlock** 은 명령줄을 입력으로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-136">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="2562e-137">**ScriptBlock** 이를 반환 하는 경우 `$True` 명령줄이 기록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-137">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

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

### <span data-ttu-id="2562e-138">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="2562e-138">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="2562e-139">이 옵션은 또는에서 실행 되는 경우와 같이 입력이 리디렉션되는 경우에만 Windows에 해당 `tmux` `screen` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-139">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="2562e-140">Windows에서 리디렉션된 입력을 사용 하면 많은 키가 이스케이프 문자에서 시작 하는 문자 시퀀스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-140">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="2562e-141">단일 이스케이프 문자 다음에 더 많은 문자와 유효한 이스케이프 시퀀스를 구분 하는 것은 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-141">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="2562e-142">터미널에서 사용자 유형 보다 더 빠르게 문자를 보낼 수 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-142">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="2562e-143">**Psreadline** 은 전체 이스케이프 시퀀스를 수신 하기 전에이 시간 제한 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-143">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="2562e-144">입력할 때 무작위 또는 예기치 않은 문자가 표시 되는 경우이 시간 제한을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-144">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

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

### <span data-ttu-id="2562e-145">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="2562e-145">-BellStyle</span></span>

<span data-ttu-id="2562e-146">**Psreadline** 이 다양 한 오류 및 모호한 조건에 응답 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-146">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="2562e-147">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-147">The valid values are as follows:</span></span>

- <span data-ttu-id="2562e-148">**가청**: 짧은 경고음.</span><span class="sxs-lookup"><span data-stu-id="2562e-148">**Audible**: A short beep.</span></span>
- <span data-ttu-id="2562e-149">**시각적 개체**: 텍스트가 잠시 깜박입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-149">**Visual**: Text flashes briefly.</span></span>
- <span data-ttu-id="2562e-150">**없음**: 피드백이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-150">**None**: No feedback.</span></span>

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

### <span data-ttu-id="2562e-151">-색</span><span class="sxs-lookup"><span data-stu-id="2562e-151">-Colors</span></span>

<span data-ttu-id="2562e-152">**Colors** 매개 변수는 **psreadline** 에서 사용 되는 다양 한 색을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-152">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="2562e-153">인수는 키에서 색을 지정 하는 요소와 값을 지정 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-153">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="2562e-154">자세한 내용은 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2562e-154">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="2562e-155">색은 **ConsoleColor** 의 값 (예: `[ConsoleColor]::Red` 또는 유효한 ANSI 이스케이프 시퀀스) 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-155">Colors can be either a value from **ConsoleColor**, for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="2562e-156">유효한 이스케이프 시퀀스는 터미널에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-156">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="2562e-157">PowerShell 5.0에서 빨강 텍스트에 대 한 예제 이스케이프 시퀀스는 `$([char]0x1b)[91m` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-157">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="2562e-158">PowerShell 6 이상에서 같은 이스케이프 시퀀스는 `` `e[91m`` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-158">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="2562e-159">다음 형식을 포함 하 여 다른 이스케이프 시퀀스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-159">You can specify other escape sequences including the following types:</span></span>

<span data-ttu-id="2562e-160">PSReadLine 2.2.0에서의 사용자 지정을 지원 하기 위해 두 가지 색 설정이 추가 되었습니다 `ListView` .</span><span class="sxs-lookup"><span data-stu-id="2562e-160">Two color settings were added to support customization of the `ListView` in PSReadLine 2.2.0:</span></span>

- <span data-ttu-id="2562e-161">**ListPredictionColor** -선행 `>` 문자 및 후행 소스 이름 (예:)에 대 한 색을 설정 `[History]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-161">**ListPredictionColor** - set color for the leading `>` character and the trailing source name, e.g. `[History]`.</span></span> <span data-ttu-id="2562e-162">기본적으로는를 `DarkYellow` 전경색으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-162">By default, it uses `DarkYellow` as the foreground color.</span></span>
- <span data-ttu-id="2562e-163">**ListPredictionSelectedColor** -목록 항목을 표시 하는 데 사용할 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-163">**ListPredictionSelectedColor** - set color for indicating a list item is selected.</span></span> <span data-ttu-id="2562e-164">기본적으로는를 `DarkBlack` 배경색으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-164">By default, it uses `DarkBlack` as the background color.</span></span>

- <span data-ttu-id="2562e-165">256 색</span><span class="sxs-lookup"><span data-stu-id="2562e-165">256 color</span></span>
- <span data-ttu-id="2562e-166">24 비트 색</span><span class="sxs-lookup"><span data-stu-id="2562e-166">24-bit color</span></span>
- <span data-ttu-id="2562e-167">전경, 배경 또는 둘 다</span><span class="sxs-lookup"><span data-stu-id="2562e-167">Foreground, background, or both</span></span>
- <span data-ttu-id="2562e-168">반전, 굵게</span><span class="sxs-lookup"><span data-stu-id="2562e-168">Inverse, bold</span></span>

<span data-ttu-id="2562e-169">ANSI 색 코드에 대 한 자세한 내용은 위키백과의 [ansi 이스케이프 코드](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2562e-169">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="2562e-170">유효한 키는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-170">The valid keys include:</span></span>

- <span data-ttu-id="2562e-171">**ContinuationPrompt**: 연속 프롬프트의 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-171">**ContinuationPrompt**: The color of the continuation prompt.</span></span>
- <span data-ttu-id="2562e-172">**강조**: 강조 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-172">**Emphasis**: The emphasis color.</span></span> <span data-ttu-id="2562e-173">예를 들어 기록을 검색할 때 일치 하는 텍스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-173">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="2562e-174">**오류**: 오류 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-174">**Error**: The error color.</span></span> <span data-ttu-id="2562e-175">예를 들어 프롬프트에서을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-175">For example, in the prompt.</span></span>
- <span data-ttu-id="2562e-176">**Selection**: 메뉴 선택 영역이 나 선택 된 텍스트를 강조 표시 하는 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-176">**Selection**: The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="2562e-177">**기본값**: 기본 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-177">**Default**: The default token color.</span></span>
- <span data-ttu-id="2562e-178">**Comment**: 주석 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-178">**Comment**: The comment token color.</span></span>
- <span data-ttu-id="2562e-179">**키워드**: 키워드 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-179">**Keyword**: The keyword token color.</span></span>
- <span data-ttu-id="2562e-180">**문자열**: 문자열 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-180">**String**: The string token color.</span></span>
- <span data-ttu-id="2562e-181">**Operator**: 연산자 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-181">**Operator**: The operator token color.</span></span>
- <span data-ttu-id="2562e-182">**Variable**: 변수 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-182">**Variable**: The variable token color.</span></span>
- <span data-ttu-id="2562e-183">**Command**: 명령 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-183">**Command**: The command token color.</span></span>
- <span data-ttu-id="2562e-184">**매개 변수**: 매개 변수 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-184">**Parameter**: The parameter token color.</span></span>
- <span data-ttu-id="2562e-185">**형식**: 형식 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-185">**Type**: The type token color.</span></span>
- <span data-ttu-id="2562e-186">**Number**: 숫자 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-186">**Number**: The number token color.</span></span>
- <span data-ttu-id="2562e-187">**Member**: 구성원 이름 토큰 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-187">**Member**: The member name token color.</span></span>
- <span data-ttu-id="2562e-188">**InlinePrediction**: 예측 제안의 인라인 뷰에 대 한 색입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-188">**InlinePrediction**: The color for the inline view of the predictive suggestion.</span></span>

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

### <span data-ttu-id="2562e-189">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="2562e-189">-CommandValidationHandler</span></span>

<span data-ttu-id="2562e-190">**Validateandacceptline** 에서 호출 되는 **ScriptBlock** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-190">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="2562e-191">예외가 throw 되 면 유효성 검사가 실패 하 고 오류가 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-191">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="2562e-192">예외를 throw 하기 전에 유효성 검사 처리기는 오류 발생 지점에 커서를 놓고 쉽게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-192">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="2562e-193">유효성 검사 처리기는 일반적인 철자 오류를 수정 하기 위해와 같은 명령줄을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-193">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="2562e-194">**Validateandacceptline** 은 작업을 수행할 수 없는 명령을 사용 하 여 기록의 복잡 한 문제를 방지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-194">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

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

### <span data-ttu-id="2562e-195">-전체 Queryitems</span><span class="sxs-lookup"><span data-stu-id="2562e-195">-CompletionQueryItems</span></span>

<span data-ttu-id="2562e-196">메시지를 표시 하지 않고 표시 되는 최대 완료 항목 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-196">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="2562e-197">표시할 항목 수가이 값 보다 크면 **Psreadline** 은 완료 항목을 표시 하기 전에 **예/아니요** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-197">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

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

### <span data-ttu-id="2562e-198">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="2562e-198">-ContinuationPrompt</span></span>

<span data-ttu-id="2562e-199">여러 줄 입력을 입력할 때 다음 줄의 시작 부분에 표시 되는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-199">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="2562e-200">기본값은 이중 보다 큼 기호 ( `>>` )입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-200">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="2562e-201">빈 문자열이 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-201">An empty string is valid.</span></span>

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

### <span data-ttu-id="2562e-202">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="2562e-202">-DingDuration</span></span>

<span data-ttu-id="2562e-203">**BellStyle** 가 **가청** 으로 설정 된 경우 경고음의 기간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-203">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="2562e-204">-DingTone</span><span class="sxs-lookup"><span data-stu-id="2562e-204">-DingTone</span></span>

<span data-ttu-id="2562e-205">**BellStyle** 가 **가청** 으로 설정 된 경우 경고음의 톤 (hz)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-205">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="2562e-206">-EditMode</span><span class="sxs-lookup"><span data-stu-id="2562e-206">-EditMode</span></span>

<span data-ttu-id="2562e-207">명령줄 편집 모드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-207">Specifies the command line editing mode.</span></span> <span data-ttu-id="2562e-208">이 매개 변수를 사용 하면에 의해 설정 된 모든 키 바인딩이 다시 설정 `Set-PSReadLineKeyHandler` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-208">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="2562e-209">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-209">The valid values are as follows:</span></span>

- <span data-ttu-id="2562e-210">**Windows**: 키 바인딩은 PowerShell, Cmd 및 Visual Studio를 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-210">**Windows**: Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="2562e-211">**Emacs**: 키 바인딩은 Bash 또는 Emacs을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-211">**Emacs**: Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="2562e-212">**Vi**: 키 바인딩은 Vi를 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-212">**Vi**: Key bindings emulate Vi.</span></span>

<span data-ttu-id="2562e-213">`Get-PSReadLineKeyHandler`현재 구성 된 **EditMode** 의 키 바인딩을 보려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-213">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

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

### <span data-ttu-id="2562e-214">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="2562e-214">-ExtraPromptLineCount</span></span>

<span data-ttu-id="2562e-215">추가 줄의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-215">Specifies the number of extra lines.</span></span>

<span data-ttu-id="2562e-216">프롬프트가 두 줄 이상으로 확장 되는 경우이 매개 변수의 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-216">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="2562e-217">**Psreadline** 에서 일부 출력을 표시 한 후에 프롬프트가 표시 될 때 추가 줄을 사용 하려면이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-217">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="2562e-218">예를 들어 **Psreadline** 은 완료 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-218">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="2562e-219">이 옵션은 이전 버전의 **Psreadline** 에서 보다 더 필요 하지만 함수를 사용 하는 경우에 유용 `InvokePrompt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-219">This option is needed less than in previous versions of **PSReadLine**, but is useful when the `InvokePrompt` function is used.</span></span>

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

### <span data-ttu-id="2562e-220">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="2562e-220">-HistoryNoDuplicates</span></span>

<span data-ttu-id="2562e-221">이 옵션은 회수 동작을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-221">This option controls the recall behavior.</span></span> <span data-ttu-id="2562e-222">중복 된 명령은 여전히 기록 파일에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-222">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="2562e-223">이 옵션을 설정 하면 명령을 회수할 때 가장 최근의 호출만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-223">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="2562e-224">회수 하는 동안 순서를 유지 하기 위해 기록에 반복 명령이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-224">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="2562e-225">그러나 기록을 회수 하거나 검색할 때 일반적으로 명령을 여러 번 표시 하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-225">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="2562e-226">기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistoryNoDuplicates** 속성은로 설정 됩니다 `True` .</span><span class="sxs-lookup"><span data-stu-id="2562e-226">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="2562e-227">이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-227">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="2562e-228">속성 값을 변경 하려면 다음과 같이 **Switchparameter** 값을 지정 해야 합니다 `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="2562e-228">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="2562e-229">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-229">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2562e-230">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="2562e-230">-HistorySavePath</span></span>

<span data-ttu-id="2562e-231">기록이 저장 되는 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-231">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="2562e-232">Windows 또는 Windows 이외의 플랫폼을 실행 하는 컴퓨터는 다른 위치에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-232">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="2562e-233">파일 이름은 변수에 저장 됩니다 `$($host.Name)_history.txt` (예:) `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="2562e-233">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="2562e-234">이 매개 변수를 사용 하지 않는 경우 기본 경로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-234">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="2562e-235">**Windows**</span><span class="sxs-lookup"><span data-stu-id="2562e-235">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="2562e-236">**비 Windows**</span><span class="sxs-lookup"><span data-stu-id="2562e-236">**non-Windows**</span></span>

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

### <span data-ttu-id="2562e-237">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="2562e-237">-HistorySaveStyle</span></span>

<span data-ttu-id="2562e-238">**Psreadline** 에서 기록을 저장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-238">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="2562e-239">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-239">Valid values are as follows:</span></span>

- <span data-ttu-id="2562e-240">**Saveincrementally**: 각 명령이 실행 된 후 기록을 저장 하 고 PowerShell의 여러 인스턴스 간에 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-240">**SaveIncrementally**: Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="2562e-241">**SaveAtExit**: PowerShell이 종료 될 때 기록 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-241">**SaveAtExit**: Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="2562e-242">**SaveNothing**: 기록 파일을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-242">**SaveNothing**: Don't use a history file.</span></span>

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

### <span data-ttu-id="2562e-243">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="2562e-243">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="2562e-244">**ReverseSearchHistory** 또는 **HistorySearchBackward** 와 같은 함수에서 기록 검색에서 대/소문자를 구분 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-244">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="2562e-245">기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistorySearchCaseSensitive** 속성은로 설정 됩니다 `False` .</span><span class="sxs-lookup"><span data-stu-id="2562e-245">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="2562e-246">이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-246">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="2562e-247">속성 값을 다시 변경 하려면 **Switchparameter** 의 값을 다음과 같이 지정 해야 합니다 `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="2562e-247">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="2562e-248">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-248">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2562e-249">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="2562e-249">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="2562e-250">검색을 사용 하 여 기록에서 로드 하는 명령의 끝으로 커서를 이동 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-250">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="2562e-251">이 매개 변수를로 설정 하면 `$False` 위로 또는 아래로 화살표를 누를 때 커서가 있던 위치에 커서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-251">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="2562e-252">기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistorySearchCursorMovesToEnd** 속성은로 설정 됩니다 `False` .</span><span class="sxs-lookup"><span data-stu-id="2562e-252">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="2562e-253">이 **Switchparameter** 를 사용 하 여 속성 값을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-253">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="2562e-254">속성 값을 다시 변경 하려면 **Switchparameter** 의 값을 다음과 같이 지정 해야 합니다 `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="2562e-254">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="2562e-255">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-255">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2562e-256">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="2562e-256">-MaximumHistoryCount</span></span>

<span data-ttu-id="2562e-257">**Psreadline** 기록에 저장할 최대 명령 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-257">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="2562e-258">**Psreadline** 기록은 PowerShell 기록과 별개입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-258">**PSReadLine** history is separate from PowerShell history.</span></span>

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

### <span data-ttu-id="2562e-259">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="2562e-259">-MaximumKillRingCount</span></span>

<span data-ttu-id="2562e-260">Kill 링에 저장 된 최대 항목 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-260">Specifies the maximum number of items stored in the kill ring.</span></span>

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

### <span data-ttu-id="2562e-261">-PromptText</span><span class="sxs-lookup"><span data-stu-id="2562e-261">-PromptText</span></span>

<span data-ttu-id="2562e-262">구문 분석 오류가 발생 하는 경우 **Psreadline** 은 프롬프트의 일부를 빨간색으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-262">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="2562e-263">**Psreadline** 은 프롬프트 함수를 분석 하 여 프롬프트 부분의 색만 변경 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-263">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="2562e-264">이 분석은 100% 안정적이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-264">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="2562e-265">**Psreadline** 에서 예기치 않은 방법으로 프롬프트를 변경 하는 경우이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-265">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="2562e-266">후행 공백을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-266">Include any trailing whitespace.</span></span>

<span data-ttu-id="2562e-267">예를 들어, 프롬프트 함수는 다음 예제와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-267">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="2562e-268">그런 다음 다음을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-268">Then set:</span></span>

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

### <span data-ttu-id="2562e-269">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="2562e-269">-ShowToolTips</span></span>

<span data-ttu-id="2562e-270">가능한 완료를 표시 하면 도구 설명이 완성 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-270">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="2562e-271">기본적으로 이 옵션은 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-271">This option is enabled by default.</span></span> <span data-ttu-id="2562e-272">이 옵션은 이전 버전의 **Psreadline** 에서 기본적으로 사용 하도록 설정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-272">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="2562e-273">사용 하지 않도록 설정 하려면이 옵션을로 설정 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-273">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="2562e-274">기본적으로 전역 **PSConsoleReadLineOptions** 개체의 **showtooltips** 속성은로 설정 됩니다 `True` .</span><span class="sxs-lookup"><span data-stu-id="2562e-274">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="2562e-275">이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-275">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="2562e-276">속성 값을 변경 하려면 다음과 같이 **Switchparameter** 값을 지정 해야 합니다 `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="2562e-276">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="2562e-277">다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-277">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2562e-278">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="2562e-278">-ViModeChangeHandler</span></span>

<span data-ttu-id="2562e-279">**Vimodeindicator** 로 설정 된 경우 `Script` 모드가 변경 될 때마다 제공 된 스크립트 블록이 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-279">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="2562e-280">스크립트 블록은 형식의 인수 하나를 제공 합니다 `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="2562e-280">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="2562e-281">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-281">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="2562e-282">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="2562e-282">-ViModeIndicator</span></span>

<span data-ttu-id="2562e-283">이 옵션은 현재 **Vi** 모드의 시각적 표시를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-283">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="2562e-284">삽입 모드 또는 명령 모드 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-284">Either insert mode or command mode.</span></span>

<span data-ttu-id="2562e-285">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-285">The valid values are as follows:</span></span>

- <span data-ttu-id="2562e-286">**없음**: 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-286">**None**: There's no indication.</span></span>
- <span data-ttu-id="2562e-287">**Prompt**: 프롬프트에서 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-287">**Prompt**: The prompt changes color.</span></span>
- <span data-ttu-id="2562e-288">**Cursor**: 커서 크기가 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-288">**Cursor**: The cursor changes size.</span></span>
- <span data-ttu-id="2562e-289">**스크립트**: 사용자 지정 텍스트가 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-289">**Script**: User-specified text is printed.</span></span>

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

### <span data-ttu-id="2562e-290">-WordDelimiters 기호</span><span class="sxs-lookup"><span data-stu-id="2562e-290">-WordDelimiters</span></span>

<span data-ttu-id="2562e-291">**Forwardword** 또는 **KillWord** 같은 함수의 단어를 구분 하는 문자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-291">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2562e-292">-PredictionSource</span><span class="sxs-lookup"><span data-stu-id="2562e-292">-PredictionSource</span></span>

<span data-ttu-id="2562e-293">는 예측 제안을 가져오도록 PSReadLine의 원본을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-293">Specifies the source for PSReadLine to get predictive suggestions.</span></span>

<span data-ttu-id="2562e-294">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-294">Valid values are:</span></span>

- <span data-ttu-id="2562e-295">**None** -예측 IntelliSense 기능을 사용 하지 않도록 설정 합니다 (기본값).</span><span class="sxs-lookup"><span data-stu-id="2562e-295">**None** - disable the predictive IntelliSense feature (default).</span></span>
<span data-ttu-id="2562e-296">-\`**기록** -예측 IntelliSense 기능을 사용 하도록 설정 하 고 psreadline 기록을 유일한 원본으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-296">-\`**History** - enable the predictive IntelliSense feature and use the PSReadLine history as the only source.</span></span>
- <span data-ttu-id="2562e-297">**플러그 인** -예측 IntelliSense 기능을 사용 하도록 설정 하 고 플러그 인 ( `CommandPrediction` )을 유일한 원본으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-297">**Plugin** - enable the predictive IntelliSense feature and use the plugins (`CommandPrediction`) as the only source.</span></span> <span data-ttu-id="2562e-298">이 값은 PSReadLine 2.2.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-298">This value was added in PSReadLine 2.2.0</span></span>
- <span data-ttu-id="2562e-299">**HistoryAndPlugin** -예측 IntelliSense 기능을 사용 하도록 설정 하 고 기록과 플러그 인을 모두 원본으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-299">**HistoryAndPlugin** - enable the predictive IntelliSense feature and use both history and plugin as the sources.</span></span> <span data-ttu-id="2562e-300">이 값은 PSReadLine 2.2.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-300">This value was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2562e-301">-PredictionViewStyle</span><span class="sxs-lookup"><span data-stu-id="2562e-301">-PredictionViewStyle</span></span>

<span data-ttu-id="2562e-302">예측 텍스트 표시의 스타일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-302">Sets the style for the display of the predictive text.</span></span> <span data-ttu-id="2562e-303">기본값은 **InlineView** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-303">The default is **InlineView**.</span></span>

- <span data-ttu-id="2562e-304">**InlineView** -물고기 shell 및 zsh와 마찬가지로 오늘 기존 스타일입니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-304">**InlineView** - the style as existing today, similar as in fish shell and zsh.</span></span> <span data-ttu-id="2562e-305">(기본값)</span><span class="sxs-lookup"><span data-stu-id="2562e-305">(default)</span></span>
- <span data-ttu-id="2562e-306">**ListView** -제안은 드롭다운 목록에서 렌더링 되며 사용자는 <kbd>Uparrow</kbd> 및 <kbd>아래쪽 화살표</kbd>를 사용 하 여 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-306">**ListView** - suggestions are rendered in a drop down list, and users can select using <kbd>UpArrow</kbd> and <kbd>DownArrow</kbd>.</span></span>

<span data-ttu-id="2562e-307">이 매개 변수는 PSReadLine 2.2.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-307">This parameter was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionViewStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineView
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2562e-308">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2562e-308">CommonParameters</span></span>

<span data-ttu-id="2562e-309">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2562e-309">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2562e-310">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2562e-310">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2562e-311">입력</span><span class="sxs-lookup"><span data-stu-id="2562e-311">Inputs</span></span>

### <span data-ttu-id="2562e-312">없음</span><span class="sxs-lookup"><span data-stu-id="2562e-312">None</span></span>

<span data-ttu-id="2562e-313">개체를 파이프로 사용할 수 없습니다. `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="2562e-313">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="2562e-314">출력</span><span class="sxs-lookup"><span data-stu-id="2562e-314">Outputs</span></span>

### <span data-ttu-id="2562e-315">없음</span><span class="sxs-lookup"><span data-stu-id="2562e-315">None</span></span>

<span data-ttu-id="2562e-316">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2562e-316">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2562e-317">참고</span><span class="sxs-lookup"><span data-stu-id="2562e-317">Notes</span></span>

## <span data-ttu-id="2562e-318">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2562e-318">Related links</span></span>

[<span data-ttu-id="2562e-319">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="2562e-319">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="2562e-320">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2562e-320">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="2562e-321">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2562e-321">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="2562e-322">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2562e-322">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="2562e-323">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2562e-323">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
