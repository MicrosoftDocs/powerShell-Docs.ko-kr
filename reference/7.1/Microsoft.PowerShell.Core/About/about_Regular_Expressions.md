---
description: PowerShell의 정규식에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: fe3f668265101f8c0aa07967f235a1092d76e299
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223962"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="6f6de-104">정규식 정보</span><span class="sxs-lookup"><span data-stu-id="6f6de-104">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="6f6de-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="6f6de-105">Short description</span></span>
<span data-ttu-id="6f6de-106">PowerShell의 정규식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-106">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="6f6de-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-107">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="6f6de-108">이 문서에서는 PowerShell에서 정규식을 사용 하기 위한 구문과 메서드를 보여 줍니다. 모든 구문에 대해서는 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-108">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="6f6de-109">자세한 참조는 [정규식 언어-빠른 참조](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6de-109">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="6f6de-110">정규식은 텍스트를 일치 시키는 데 사용 되는 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-110">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="6f6de-111">리터럴 문자, 연산자 및 기타 구문으로 구성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-111">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="6f6de-112">이 문서에서는 PowerShell의 정규식 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-112">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="6f6de-113">PowerShell에는 정규식을 사용 하는 몇 가지 연산자와 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-113">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="6f6de-114">구문 및 사용법에 대 한 자세한 내용은 아래 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6de-114">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="6f6de-115">Select-String</span><span class="sxs-lookup"><span data-stu-id="6f6de-115">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="6f6de-116">-match 및-replace 연산자</span><span class="sxs-lookup"><span data-stu-id="6f6de-116">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="6f6de-117">-분할</span><span class="sxs-lookup"><span data-stu-id="6f6de-117">-split</span></span>](about_Split.md)
- [<span data-ttu-id="6f6de-118">-regex 옵션을 사용 하는 switch 문</span><span class="sxs-lookup"><span data-stu-id="6f6de-118">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="6f6de-119">PowerShell 정규식은 기본적으로 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-119">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="6f6de-120">위에 표시 된 각 방법에는 대/소문자 구분을 적용 하는 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-120">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="6f6de-121">메서드</span><span class="sxs-lookup"><span data-stu-id="6f6de-121">Method</span></span>       |                      <span data-ttu-id="6f6de-122">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="6f6de-122">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="6f6de-123">`-CaseSensitive`스위치 사용</span><span class="sxs-lookup"><span data-stu-id="6f6de-123">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="6f6de-124">`switch` 문</span><span class="sxs-lookup"><span data-stu-id="6f6de-124">`switch` statement</span></span> | <span data-ttu-id="6f6de-125">옵션 사용 `-casesensitive`</span><span class="sxs-lookup"><span data-stu-id="6f6de-125">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="6f6de-126">연산자</span><span class="sxs-lookup"><span data-stu-id="6f6de-126">operators</span></span>          | <span data-ttu-id="6f6de-127">**' c '** ( `-cmatch` , `-csplit` 또는 `-creplace` )를 사용 하는 접두사</span><span class="sxs-lookup"><span data-stu-id="6f6de-127">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="6f6de-128">문자 리터럴</span><span class="sxs-lookup"><span data-stu-id="6f6de-128">Character literals</span></span>

<span data-ttu-id="6f6de-129">정규식은 리터럴 문자 또는 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-129">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="6f6de-130">식이 지정 된 텍스트와 정확히 일치 하도록 엔진을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-130">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="6f6de-131">문자 클래스</span><span class="sxs-lookup"><span data-stu-id="6f6de-131">Character classes</span></span>

<span data-ttu-id="6f6de-132">문자 리터럴은 정확한 패턴을 알고 있는 경우에만 작동 하지만 문자 클래스를 사용 하면 더 구체적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-132">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="6f6de-133">문자 그룹</span><span class="sxs-lookup"><span data-stu-id="6f6de-133">Character groups</span></span>

<span data-ttu-id="6f6de-134">`[character group]` 를 사용 하면 한 번의 문자를 한 번만 일치 시킬 수 있으며 `[^character group]` 그룹에 없는 문자만 일치 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-134">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="6f6de-135">일치 시킬 문자 목록에 하이픈 문자 ()가 포함 되어 있으면 `-` 문자 범위 식과 구분 하기 위해 목록의 시작 부분 또는 끝 부분에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-135">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="6f6de-136">문자 범위</span><span class="sxs-lookup"><span data-stu-id="6f6de-136">Character ranges</span></span>

<span data-ttu-id="6f6de-137">패턴은 문자 범위가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-137">A pattern can also be a range of characters.</span></span> <span data-ttu-id="6f6de-138">문자는 영문자 `[A-Z]` , 숫자 `[0-9]` 또는 ASCII 기반 `[ -~]` (모든 인쇄 가능한 문자) 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-138">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="6f6de-139">숫자</span><span class="sxs-lookup"><span data-stu-id="6f6de-139">Numbers</span></span>

<span data-ttu-id="6f6de-140">`\d`문자 클래스는 10 진수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-140">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="6f6de-141">반대로 `\D` 는 10 진수가 아닌 모든 숫자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-141">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="6f6de-142">단어 문자</span><span class="sxs-lookup"><span data-stu-id="6f6de-142">Word characters</span></span>

<span data-ttu-id="6f6de-143">`\w`문자 클래스는 단어 문자를 찾습니다 `[a-zA-Z_0-9]` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-143">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="6f6de-144">비단어 문자를 찾으려면를 사용 `\W` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-144">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="6f6de-145">와일드카드</span><span class="sxs-lookup"><span data-stu-id="6f6de-145">Wildcards</span></span>

<span data-ttu-id="6f6de-146">마침표 ( `.` )는 정규식의 와일드 카드 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-146">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="6f6de-147">줄 바꿈 ()을 제외한 모든 문자를 찾습니다 `\n` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-147">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="6f6de-148">공백</span><span class="sxs-lookup"><span data-stu-id="6f6de-148">Whitespace</span></span>

<span data-ttu-id="6f6de-149">문자 클래스를 사용 하 여 공백을 일치 시킵니다 `\s` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-149">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="6f6de-150">공백이 아닌 문자는를 사용 하 여 일치 시킵니다 `\S` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-150">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="6f6de-151">리터럴 공백 문자 `' '` 를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-151">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="6f6de-152">수량자</span><span class="sxs-lookup"><span data-stu-id="6f6de-152">Quantifiers</span></span>

<span data-ttu-id="6f6de-153">수량자는 입력 문자열에 있는 각 요소의 인스턴스 수를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-153">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="6f6de-154">PowerShell에서 사용할 수 있는 수량자 중 몇 가지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-154">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="6f6de-155">수량자</span><span class="sxs-lookup"><span data-stu-id="6f6de-155">Quantifier</span></span> |                <span data-ttu-id="6f6de-156">설명</span><span class="sxs-lookup"><span data-stu-id="6f6de-156">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="6f6de-157">0 회 이상</span><span class="sxs-lookup"><span data-stu-id="6f6de-157">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="6f6de-158">한 번 이상</span><span class="sxs-lookup"><span data-stu-id="6f6de-158">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="6f6de-159">0 번 또는 1 번.</span><span class="sxs-lookup"><span data-stu-id="6f6de-159">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="6f6de-160">적어도 `n` 한 `m` 번 이상.</span><span class="sxs-lookup"><span data-stu-id="6f6de-160">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="6f6de-161">별표 ( `*` )는 이전 요소를 0 번 이상 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-161">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="6f6de-162">따라서 요소가 없는 입력 문자열도 일치 하는 항목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-162">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="6f6de-163">더하기 기호 ( `+` )는 이전 요소를 1 번 이상 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-163">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="6f6de-164">물음표는 `?` 이전 요소를 0 번 또는 한 번 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-164">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="6f6de-165">별표와 마찬가지로 `*` 요소가 없는 문자열도 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-165">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="6f6de-166">`{n, m}`수량자를 사용 하 여 수량자를 세부적으로 제어할 수 있는 여러 가지 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-166">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="6f6de-167">두 번째 요소 `m` 와 쉼표는 `,` 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-167">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="6f6de-168">수량자</span><span class="sxs-lookup"><span data-stu-id="6f6de-168">Quantifier</span></span> |                <span data-ttu-id="6f6de-169">설명</span><span class="sxs-lookup"><span data-stu-id="6f6de-169">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="6f6de-170">정확히 일치 하 `n` 는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-170">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="6f6de-171">최소 횟수를 찾습니다 `n` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-171">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="6f6de-172">`n`와 횟수를 일치 시킵니다 `m` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-172">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="6f6de-173">앵커</span><span class="sxs-lookup"><span data-stu-id="6f6de-173">Anchors</span></span>

<span data-ttu-id="6f6de-174">앵커를 사용 하면 입력 문자열 내의 일치 위치에 따라 일치가 성공 하거나 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-174">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="6f6de-175">일반적으로 사용 되는 두 앵커는 `^` 및 `$` 입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-175">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="6f6de-176">캐럿은 문자열의 `^` 시작과 일치 하며 `$` 문자열의 끝과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-176">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="6f6de-177">앵커를 사용 하면 원치 않는 문자를 삭제 하는 동시에 특정 위치에 있는 텍스트를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-177">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="6f6de-178">앵커를 포함 하는 regex를 정의할 때 큰따옴표 `$` () 대신 작은따옴표 ()를 사용 하 여 regex를 묶어야 합니다 `'` `"` . 그렇지 않으면 PowerShell에서 식을 변수로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-178">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="6f6de-179">PowerShell에서 앵커를 사용 하는 경우 **regexoptions.singleline** 및 **Multiline** 정규식 옵션의 차이점을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-179">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="6f6de-180">**여러** 줄 모드: 여러 줄 모드는 `^` `$` 입력 문자열의 시작 및 끝이 아니라 모든 줄의 시작 부분을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-180">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="6f6de-181">**Regexoptions.singleline** : regexoptions.singleline 모드는 입력 문자열을 **regexoptions.singleline** 로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-181">**Singleline** : Singleline mode treats the input string as a **SingleLine**.</span></span>
  <span data-ttu-id="6f6de-182">`.`줄 바꿈 문자를 제외한 모든 문자와 일치 하는 대신 문자를 모든 문자 (줄바꿈 포함)와 일치 하도록 강제 합니다 `\n` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-182">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="6f6de-183">이러한 옵션 및 사용 방법에 대 한 자세한 내용은 [정규식 언어-빠른 참조](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6de-183">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="6f6de-184">문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="6f6de-184">Escaping characters</span></span>

<span data-ttu-id="6f6de-185">백슬래시 ( `\` )는 문자를 이스케이프 하는 데 사용 되므로 정규식 엔진에서 구문 분석 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-185">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="6f6de-186">다음 문자는 예약 되어 `[]().\^$|?*+{}` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-186">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="6f6de-187">입력 문자열에서 이러한 문자를 일치 시키려면 패턴에서 이러한 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-187">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="6f6de-188">텍스트를 이스케이프할 수 있는 정규식 클래스의 정적 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-188">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="6f6de-189">문자 클래스에서 사용 되는 기존 백슬래시를 포함 하 여 모든 예약 된 정규식 문자를 이스케이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-189">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="6f6de-190">이스케이프 해야 하는 패턴 부분 에서만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-190">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="6f6de-191">기타 문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="6f6de-191">Other character escapes</span></span>

<span data-ttu-id="6f6de-192">특수 문자 형식을 일치 시키는 데 사용할 수 있는 예약 된 문자 이스케이프도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-192">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="6f6de-193">일반적으로 사용 되는 문자 이스케이프는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-193">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="6f6de-194">문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="6f6de-194">Character Escape</span></span>  |<span data-ttu-id="6f6de-195">Description</span><span class="sxs-lookup"><span data-stu-id="6f6de-195">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="6f6de-196">탭과 일치</span><span class="sxs-lookup"><span data-stu-id="6f6de-196">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="6f6de-197">줄 바꿈 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-197">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="6f6de-198">캐리지 리턴 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-198">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="6f6de-199">그룹, 캡처 및 대체</span><span class="sxs-lookup"><span data-stu-id="6f6de-199">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="6f6de-200">그룹화 구문은 입력 문자열을 캡처하거나 무시할 수 있는 부분 문자열로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-200">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="6f6de-201">그룹화 된 부분 문자열을 하위 식 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-201">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="6f6de-202">기본적으로 부분식은 번호 매기기 그룹에 캡처되고 이름을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-202">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="6f6de-203">그룹화 구문은 괄호로 묶은 정규식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-203">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="6f6de-204">포함 된 정규식과 일치 하는 모든 텍스트가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-204">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="6f6de-205">다음 예제에서는 입력 텍스트를 두 개의 캡처링 그룹으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-205">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="6f6de-206">`$Matches` **Hashtable** 자동 변수를 사용 하 여 캡처된 텍스트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-206">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="6f6de-207">전체 일치 항목을 나타내는 텍스트는 키에 저장 됩니다 `0` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-207">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="6f6de-208">캡처는 왼쪽에서 오른쪽으로 증가 하는 숫자 **정수** 키에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-208">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="6f6de-209">캡처 `1` 는 사용자 이름, 캡처에 사용자 이름만 포함 될 때까지 모든 텍스트를 포함 합니다 `2` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-209">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> <span data-ttu-id="6f6de-210">`0`키가 **정수** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-210">The `0` key is an **Integer**.</span></span> <span data-ttu-id="6f6de-211">모든 **Hashtable** 메서드를 사용 하 여 저장 된 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-211">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a><span data-ttu-id="6f6de-212">명명 된 캡처</span><span class="sxs-lookup"><span data-stu-id="6f6de-212">Named Captures</span></span>

<span data-ttu-id="6f6de-213">기본적으로 캡처는 왼쪽에서 오른쪽으로 오름차순으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-213">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="6f6de-214">캡처링 그룹에 **이름을** 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-214">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="6f6de-215">이 **이름은** `$Matches` **Hashtable** 자동 변수의 키가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-215">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="6f6de-216">캡처링 그룹 내에서를 사용 `?<keyname>` 하 여 캡처된 데이터를 명명 된 키 아래에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-216">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

<span data-ttu-id="6f6de-217">다음 예에서는 Windows 보안 로그에 최신 로그 항목을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-217">The following example stores the newest log entry in the Windows Security Log.</span></span>
<span data-ttu-id="6f6de-218">제공 된 정규식은 메시지에서 사용자 이름과 도메인을 추출 하 여 키 아래에 저장 합니다. **N** 은 이름, 도메인의 경우 **D** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-218">The provided regular expression extracts the username and domain from the message and stores them under the keys: **N** for name and **D** for domain.</span></span>

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

<span data-ttu-id="6f6de-219">자세한 내용은 [정규식의 그룹화 구문](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6de-219">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="6f6de-220">정규식의 대체</span><span class="sxs-lookup"><span data-stu-id="6f6de-220">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="6f6de-221">정규식을 연산자와 함께 사용 하면 `-replace` 캡처된 텍스트를 사용 하 여 동적으로 텍스트를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-221">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="6f6de-222">`<input>`: 검색할 문자열</span><span class="sxs-lookup"><span data-stu-id="6f6de-222">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="6f6de-223">`<original>`: 입력 문자열을 검색 하는 데 사용 되는 정규식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-223">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="6f6de-224">`<substitute>`: 입력 문자열에서 찾은 일치 항목을 대체할 정규식 대체 식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-224">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="6f6de-225">`<original>`및 `<substitute>` 피연산자는 문자 이스케이프와 같은 정규식 엔진의 규칙에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-225">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="6f6de-226">캡처링 그룹은 문자열에서 참조할 수 있습니다 `<substitute>` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-226">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="6f6de-227">대체는 그룹 식별자 앞에 있는 문자를 사용 하 여 수행 됩니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="6f6de-227">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="6f6de-228">캡처링 그룹을 참조 하는 두 가지 방법으로는 **번호** 및 **이름을** 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-228">Two ways to reference capturing groups are by **Number** and by **Name**.</span></span>

- <span data-ttu-id="6f6de-229">**번호** 캡처링 그룹은 왼쪽에서 오른쪽으로 번호가 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-229">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="6f6de-230">이름 **으로** 캡처링 그룹은 이름으로 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-230">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="6f6de-231">`$&`식은 일치 하는 모든 텍스트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-231">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="6f6de-232">문자는 `$` 문자열 확장에 사용 되므로 대체를 사용 하 여 리터럴 문자열을 사용 하거나 `$` 큰따옴표를 사용 하는 경우 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-232">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> <span data-ttu-id="6f6de-233">또한을 `$` 리터럴 문자로 사용 하려면 `$$` 일반 이스케이프 문자 대신을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-233">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="6f6de-234">큰따옴표를 사용 하는 경우에도의 모든 인스턴스를 이스케이프 `$` 하 여 잘못 된 대체가 발생 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6de-234">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

<span data-ttu-id="6f6de-235">자세한 내용은 [정규식의 대체](/dotnet/standard/base-types/substitutions-in-regular-expressions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6de-235">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f6de-236">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f6de-236">See also</span></span>

[<span data-ttu-id="6f6de-237">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="6f6de-237">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="6f6de-238">about_Operators</span><span class="sxs-lookup"><span data-stu-id="6f6de-238">about_Operators</span></span>](about_Operators.md)

