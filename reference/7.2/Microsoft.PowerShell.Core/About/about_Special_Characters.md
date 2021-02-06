---
description: PowerShell에서 시퀀스의 다음 문자를 해석 하는 방법을 제어 하는 특수 문자 시퀀스에 대해 설명 합니다.
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: c642bc69d9e67bd945e5687d7f7c35e039062194
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605236"
---
# <a name="about-special-characters"></a><span data-ttu-id="1619d-103">특수 문자 정보</span><span class="sxs-lookup"><span data-stu-id="1619d-103">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="1619d-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="1619d-104">Short description</span></span>

<span data-ttu-id="1619d-105">PowerShell에서 시퀀스의 다음 문자를 해석 하는 방법을 제어 하는 특수 문자 시퀀스에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-105">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="1619d-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-106">Long description</span></span>

<span data-ttu-id="1619d-107">PowerShell은 표준 문자 집합에 속하지 않는 문자를 나타내는 데 사용 되는 일련의 특수 문자 시퀀스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-107">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="1619d-108">시퀀스를 일반적으로 _이스케이프 시퀀스_ 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-108">The sequences are commonly known as _escape sequences_.</span></span>

<span data-ttu-id="1619d-109">이스케이프 시퀀스는 억음 악센트 문자 (ASCII 96)로 시작 하 고 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-109">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="1619d-110">억음 문자를 _이스케이프 문자_ 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-110">The backtick character can also be referred to as the _escape character_.</span></span>

<span data-ttu-id="1619d-111">이스케이프 시퀀스는 이중 따옴표 붙은 () 문자열에 포함 된 경우에만 해석 됩니다 `"` .</span><span class="sxs-lookup"><span data-stu-id="1619d-111">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="1619d-112">PowerShell은 다음과 같은 이스케이프 시퀀스를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-112">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="1619d-113">시퀀스</span><span class="sxs-lookup"><span data-stu-id="1619d-113">Sequence</span></span>   |       <span data-ttu-id="1619d-114">Description</span><span class="sxs-lookup"><span data-stu-id="1619d-114">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="1619d-115">Null</span><span class="sxs-lookup"><span data-stu-id="1619d-115">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="1619d-116">경고</span><span class="sxs-lookup"><span data-stu-id="1619d-116">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="1619d-117">백스페이스</span><span class="sxs-lookup"><span data-stu-id="1619d-117">Backspace</span></span>               |
| `` `e ``    | <span data-ttu-id="1619d-118">이스케이프</span><span class="sxs-lookup"><span data-stu-id="1619d-118">Escape</span></span>                  |
| `` `f ``    | <span data-ttu-id="1619d-119">폼 피드</span><span class="sxs-lookup"><span data-stu-id="1619d-119">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="1619d-120">줄 바꿈</span><span class="sxs-lookup"><span data-stu-id="1619d-120">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="1619d-121">캐리지 리턴</span><span class="sxs-lookup"><span data-stu-id="1619d-121">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="1619d-122">가로 탭</span><span class="sxs-lookup"><span data-stu-id="1619d-122">Horizontal tab</span></span>          |
| `` `u{x} `` | <span data-ttu-id="1619d-123">유니코드 이스케이프 시퀀스</span><span class="sxs-lookup"><span data-stu-id="1619d-123">Unicode escape sequence</span></span> |
| `` `v ``    | <span data-ttu-id="1619d-124">세로 탭</span><span class="sxs-lookup"><span data-stu-id="1619d-124">Vertical tab</span></span>            |

<span data-ttu-id="1619d-125">또한 PowerShell에는 구문 분석을 중지할 위치를 표시 하는 특수 토큰이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-125">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="1619d-126">이 토큰을 따르는 모든 문자는 해석 되지 않는 리터럴 값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-126">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="1619d-127">특수 구문 분석 토큰:</span><span class="sxs-lookup"><span data-stu-id="1619d-127">Special parsing token:</span></span>

| <span data-ttu-id="1619d-128">시퀀스</span><span class="sxs-lookup"><span data-stu-id="1619d-128">Sequence</span></span> |            <span data-ttu-id="1619d-129">Description</span><span class="sxs-lookup"><span data-stu-id="1619d-129">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="1619d-130">다음에 나오는 모든 항목 구문 분석 중지</span><span class="sxs-lookup"><span data-stu-id="1619d-130">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="1619d-131">Null (' 0 ')</span><span class="sxs-lookup"><span data-stu-id="1619d-131">Null (\`0)</span></span>

<span data-ttu-id="1619d-132">Null ( `` `0 `` ) 문자가 PowerShell 출력에 빈 공간으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-132">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="1619d-133">이 기능을 통해 PowerShell을 사용 하 여 문자열 종료 또는 레코드 종료 표시기와 같은 null 문자를 사용 하는 텍스트 파일을 읽고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-133">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="1619d-134">Null 특수 문자는 `$null` **null** 값을 저장 하는 변수와 동일 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-134">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="1619d-135">경고 (' a)</span><span class="sxs-lookup"><span data-stu-id="1619d-135">Alert (\`a)</span></span>

<span data-ttu-id="1619d-136">경고 ( `` `a `` ) 문자는 컴퓨터의 스피커로 경고음 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-136">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="1619d-137">이 문자를 사용 하 여 사용자에 게 임박한 작업을 경고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-137">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="1619d-138">다음 예에서는 두 개의 경고음 신호를 로컬 컴퓨터의 스피커로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-138">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="1619d-139">백스페이스 (' b)</span><span class="sxs-lookup"><span data-stu-id="1619d-139">Backspace (\`b)</span></span>

<span data-ttu-id="1619d-140">백스페이스 ( `` `b `` ) 문자는 커서를 한 문자 뒤로 이동 하지만 문자를 삭제 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-140">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="1619d-141">이 예에서는 word **backup** 을 작성 한 다음 커서를 다시 두 번 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-141">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="1619d-142">그런 다음 새 위치에서 공백을 쓴 다음 단어를 **출력** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-142">Then, at the new position, writes a space followed by the word **out**.</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a><span data-ttu-id="1619d-143">이스케이프 (' e)</span><span class="sxs-lookup"><span data-stu-id="1619d-143">Escape (\`e)</span></span>

<span data-ttu-id="1619d-144">이스케이프 ( `` `e `` ) 문자는 텍스트 색 및 기타 텍스트 특성 (예: 굵게, 밑줄)을 수정 하는 가상 터미널 시퀀스 (ANSI 이스케이프 시퀀스)를 지정 하는 데 가장 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-144">The escape (`` `e ``) character is most commonly used to specify a virtual terminal sequence (ANSI escape sequence) that modifies the color of text and other text attributes such as bolding and underlining.</span></span> <span data-ttu-id="1619d-145">이러한 시퀀스는 커서 위치 지정 및 스크롤에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-145">These sequences can also be used for cursor positioning and scrolling.</span></span> <span data-ttu-id="1619d-146">PowerShell 호스트는 가상 터미널 시퀀스를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-146">The PowerShell host must support virtual terminal sequences.</span></span> <span data-ttu-id="1619d-147">의 부울 값을 확인 하 여 `$Host.UI.SupportsVirtualTerminal` 이러한 ANSI 시퀀스가 지원 되는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-147">You can check the boolean value of `$Host.UI.SupportsVirtualTerminal` to determine if these ANSI sequences are supported.</span></span>

<span data-ttu-id="1619d-148">ANSI 이스케이프 시퀀스에 대 한 자세한 내용은 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1619d-148">For more information about ANSI escape sequences, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

<span data-ttu-id="1619d-149">다음 예제에서는 녹색 전경색으로 텍스트를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-149">The following example outputs text with a green foreground color.</span></span>

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a><span data-ttu-id="1619d-150">양식 피드 (' f)</span><span class="sxs-lookup"><span data-stu-id="1619d-150">Form feed (\`f)</span></span>

<span data-ttu-id="1619d-151">양식 피드 ( `` `f `` ) 문자는 현재 페이지를 배출 하 고 다음 페이지에서 인쇄를 계속 하는 인쇄 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-151">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="1619d-152">양식 피드 문자는 인쇄 된 문서에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-152">The form feed character only affects printed documents.</span></span> <span data-ttu-id="1619d-153">화면 출력에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-153">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="1619d-154">줄 바꿈 (' n)</span><span class="sxs-lookup"><span data-stu-id="1619d-154">New line (\`n)</span></span>

<span data-ttu-id="1619d-155">새 줄 ( `` `n `` ) 문자는 문자 바로 뒤에 줄 바꿈을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-155">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="1619d-156">이 예제에서는 줄 바꿈 문자를 사용 하 여 명령에서 줄 바꿈을 만드는 방법을 보여 줍니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="1619d-156">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="1619d-157">캐리지 리턴 (' r ')</span><span class="sxs-lookup"><span data-stu-id="1619d-157">Carriage return (\`r)</span></span>

<span data-ttu-id="1619d-158">캐리지 리턴 ( `` `r `` ) 문자는 출력 커서를 현재 줄의 시작으로 이동 하 고 쓰기를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-158">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="1619d-159">현재 줄에 있는 모든 문자를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-159">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="1619d-160">이 예제에서는 캐리지 리턴 전의 텍스트를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-160">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="1619d-161">문자 앞의 텍스트는 `` `r `` 삭제 되지 않으며 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-161">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="1619d-162">가로 탭 (' t)</span><span class="sxs-lookup"><span data-stu-id="1619d-162">Horizontal tab (\`t)</span></span>

<span data-ttu-id="1619d-163">가로 탭 ( `` `t `` ) 문자는 다음 탭 정지로 이동 하 여 해당 지점에서 계속 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-163">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="1619d-164">기본적으로 PowerShell 콘솔은 여덟 번째 모든 공간에서 탭 정지를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-164">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="1619d-165">이 예에서는 각 열 사이에 두 개의 탭을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-165">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a><span data-ttu-id="1619d-166">유니코드 문자 (' u {x})</span><span class="sxs-lookup"><span data-stu-id="1619d-166">Unicode character (\`u{x})</span></span>

<span data-ttu-id="1619d-167">유니코드 이스케이프 시퀀스 ( `` `u{x} `` )를 사용 하면 해당 코드 포인트의 16 진수 표현으로 유니코드 문자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-167">The Unicode escape sequence (`` `u{x} ``) allows you to specify any Unicode character by the hexadecimal representation of its code point.</span></span> <span data-ttu-id="1619d-168">여기에는 `0xFFFF` **엄지 손가락 위로** () 문자 같은가 모 지 문자를 포함 하는 기본 다국어 평면 (>) 위의 유니코드 문자가 포함 됩니다 `` `u{1F44D} `` .</span><span class="sxs-lookup"><span data-stu-id="1619d-168">This includes Unicode characters above the Basic Multilingual Plane (> `0xFFFF`) which includes emoji characters such as the **thumbs up** (`` `u{1F44D} ``) character.</span></span> <span data-ttu-id="1619d-169">유니코드 이스케이프 시퀀스는 16 진수가 하나 이상 필요 하며 최대 6 개의 16 진수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-169">The Unicode escape sequence requires at least one hexadecimal digit and supports up to six hexadecimal digits.</span></span> <span data-ttu-id="1619d-170">시퀀스의 최대 16 진수 값은 `10FFFF` 입니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-170">The maximum hexadecimal value for the sequence is `10FFFF`.</span></span>

<span data-ttu-id="1619d-171">이 예제에서는 **위쪽 아래쪽 화살표** (&#x2195;) 기호를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-171">This example outputs the **up down arrow** (&#x2195;) symbol.</span></span>

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a><span data-ttu-id="1619d-172">세로 탭 (' v)</span><span class="sxs-lookup"><span data-stu-id="1619d-172">Vertical tab (\`v)</span></span>

<span data-ttu-id="1619d-173">가로 탭 ( `` `v `` ) 문자는 다음 세로 탭 정지로 이동 하 고 해당 지점에서 나머지 출력을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-173">The horizontal tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="1619d-174">이는 기본 Windows 콘솔에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-174">This has no effect in the default Windows console.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="1619d-175">다음 예제에서는 프린터 또는 다른 콘솔 호스트에서 얻을 수 있는 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-175">The following example shows the output you would get on a printer or in a different console host.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="1619d-176">토큰 구문 분석 (--%)</span><span class="sxs-lookup"><span data-stu-id="1619d-176">Stop-parsing token (--%)</span></span>

<span data-ttu-id="1619d-177">구문 분석 ( `--%` ) 토큰은 powershell에서 문자열을 powershell 명령 및 식으로 해석 하는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-177">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="1619d-178">이렇게 하면 해당 문자열을 다른 프로그램에 전달 하 여 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-178">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="1619d-179">프로그램 이름 및 오류를 발생 시킬 수 있는 프로그램 인수 앞에 중지 구문 분석 토큰을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-179">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="1619d-180">이 예제에서 `Icacls` 명령은 중지 구문 분석 토큰을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-180">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="1619d-181">PowerShell에서 다음 문자열을로 보냅니다 `Icacls` .</span><span class="sxs-lookup"><span data-stu-id="1619d-181">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="1619d-182">또는 다음과 같은 예도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-182">Here is another example.</span></span> <span data-ttu-id="1619d-183">**Sho워 gs** 함수는 전달 된 값을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-183">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="1619d-184">이 예제에서는 라는 변수를 `$HOME` 함수에 두 번 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-184">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

출력에서 첫 번째 매개 변수의 경우 변수 `$HOME` 값이 함수에 전달 되도록 PowerShell에서 변수를 해석 하는 것을 볼 수 있습니다. <span data-ttu-id="1619d-186">두 번째 사용은 `$HOME` 중지 구문 분석 토큰 후에 제공 되므로 "$HOME" 문자열이 해석 없이 함수에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1619d-186">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="1619d-187">중지 구문 분석 토큰에 대 한 자세한 내용은 [about_Parsing](about_Parsing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1619d-187">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1619d-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1619d-188">See also</span></span>

[<span data-ttu-id="1619d-189">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1619d-189">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

