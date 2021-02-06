---
description: PowerShell의 정규식에 대해 설명 합니다.
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 4dc6ac670a31cbea4c35ee6540ce3368ad9b02ca
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602654"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="587b1-103">정규식 정보</span><span class="sxs-lookup"><span data-stu-id="587b1-103">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="587b1-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="587b1-104">Short description</span></span>
<span data-ttu-id="587b1-105">PowerShell의 정규식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-105">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="587b1-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-106">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="587b1-107">이 문서에서는 PowerShell에서 정규식을 사용 하기 위한 구문과 메서드를 보여 줍니다. 모든 구문에 대해서는 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-107">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="587b1-108">자세한 참조는 [정규식 언어-빠른 참조](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="587b1-108">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="587b1-109">정규식은 텍스트를 일치 시키는 데 사용 되는 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-109">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="587b1-110">리터럴 문자, 연산자 및 기타 구문으로 구성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-110">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="587b1-111">이 문서에서는 PowerShell의 정규식 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-111">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="587b1-112">PowerShell에는 정규식을 사용 하는 몇 가지 연산자와 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-112">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="587b1-113">구문 및 사용법에 대 한 자세한 내용은 아래 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="587b1-113">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="587b1-114">Select-String</span><span class="sxs-lookup"><span data-stu-id="587b1-114">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="587b1-115">-match 및-replace 연산자</span><span class="sxs-lookup"><span data-stu-id="587b1-115">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="587b1-116">-분할</span><span class="sxs-lookup"><span data-stu-id="587b1-116">-split</span></span>](about_Split.md)
- [<span data-ttu-id="587b1-117">-regex 옵션을 사용 하는 switch 문</span><span class="sxs-lookup"><span data-stu-id="587b1-117">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="587b1-118">PowerShell 정규식은 기본적으로 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-118">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="587b1-119">위에 표시 된 각 방법에는 대/소문자 구분을 적용 하는 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-119">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="587b1-120">메서드</span><span class="sxs-lookup"><span data-stu-id="587b1-120">Method</span></span>       |                      <span data-ttu-id="587b1-121">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="587b1-121">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="587b1-122">`-CaseSensitive`스위치 사용</span><span class="sxs-lookup"><span data-stu-id="587b1-122">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="587b1-123">`switch` 문</span><span class="sxs-lookup"><span data-stu-id="587b1-123">`switch` statement</span></span> | <span data-ttu-id="587b1-124">옵션 사용 `-casesensitive`</span><span class="sxs-lookup"><span data-stu-id="587b1-124">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="587b1-125">연산자</span><span class="sxs-lookup"><span data-stu-id="587b1-125">operators</span></span>          | <span data-ttu-id="587b1-126">**' c '** ( `-cmatch` , `-csplit` 또는 `-creplace` )를 사용 하는 접두사</span><span class="sxs-lookup"><span data-stu-id="587b1-126">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="587b1-127">문자 리터럴</span><span class="sxs-lookup"><span data-stu-id="587b1-127">Character literals</span></span>

<span data-ttu-id="587b1-128">정규식은 리터럴 문자 또는 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-128">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="587b1-129">식이 지정 된 텍스트와 정확히 일치 하도록 엔진을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-129">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="587b1-130">문자 클래스</span><span class="sxs-lookup"><span data-stu-id="587b1-130">Character classes</span></span>

<span data-ttu-id="587b1-131">문자 리터럴은 정확한 패턴을 알고 있는 경우에만 작동 하지만 문자 클래스를 사용 하면 더 구체적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-131">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="587b1-132">문자 그룹</span><span class="sxs-lookup"><span data-stu-id="587b1-132">Character groups</span></span>

<span data-ttu-id="587b1-133">`[character group]` 를 사용 하면 한 번의 문자를 한 번만 일치 시킬 수 있으며 `[^character group]` 그룹에 없는 문자만 일치 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-133">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="587b1-134">일치 시킬 문자 목록에 하이픈 문자 ()가 포함 되어 있으면 `-` 문자 범위 식과 구분 하기 위해 목록의 시작 부분 또는 끝 부분에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-134">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="587b1-135">문자 범위</span><span class="sxs-lookup"><span data-stu-id="587b1-135">Character ranges</span></span>

<span data-ttu-id="587b1-136">패턴은 문자 범위가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-136">A pattern can also be a range of characters.</span></span> <span data-ttu-id="587b1-137">문자는 영문자 `[A-Z]` , 숫자 `[0-9]` 또는 ASCII 기반 `[ -~]` (모든 인쇄 가능한 문자) 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-137">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="587b1-138">숫자</span><span class="sxs-lookup"><span data-stu-id="587b1-138">Numbers</span></span>

<span data-ttu-id="587b1-139">`\d`문자 클래스는 10 진수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-139">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="587b1-140">반대로 `\D` 는 10 진수가 아닌 모든 숫자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-140">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="587b1-141">단어 문자</span><span class="sxs-lookup"><span data-stu-id="587b1-141">Word characters</span></span>

<span data-ttu-id="587b1-142">`\w`문자 클래스는 단어 문자를 찾습니다 `[a-zA-Z_0-9]` .</span><span class="sxs-lookup"><span data-stu-id="587b1-142">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="587b1-143">비단어 문자를 찾으려면를 사용 `\W` 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-143">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="587b1-144">와일드카드</span><span class="sxs-lookup"><span data-stu-id="587b1-144">Wildcards</span></span>

<span data-ttu-id="587b1-145">마침표 ( `.` )는 정규식의 와일드 카드 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-145">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="587b1-146">줄 바꿈 ()을 제외한 모든 문자를 찾습니다 `\n` .</span><span class="sxs-lookup"><span data-stu-id="587b1-146">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="587b1-147">공백</span><span class="sxs-lookup"><span data-stu-id="587b1-147">Whitespace</span></span>

<span data-ttu-id="587b1-148">문자 클래스를 사용 하 여 공백을 일치 시킵니다 `\s` .</span><span class="sxs-lookup"><span data-stu-id="587b1-148">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="587b1-149">공백이 아닌 문자는를 사용 하 여 일치 시킵니다 `\S` .</span><span class="sxs-lookup"><span data-stu-id="587b1-149">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="587b1-150">리터럴 공백 문자 `' '` 를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-150">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="587b1-151">수량자</span><span class="sxs-lookup"><span data-stu-id="587b1-151">Quantifiers</span></span>

<span data-ttu-id="587b1-152">수량자는 입력 문자열에 있는 각 요소의 인스턴스 수를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-152">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="587b1-153">PowerShell에서 사용할 수 있는 수량자 중 몇 가지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-153">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="587b1-154">수량자</span><span class="sxs-lookup"><span data-stu-id="587b1-154">Quantifier</span></span> |                <span data-ttu-id="587b1-155">설명</span><span class="sxs-lookup"><span data-stu-id="587b1-155">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="587b1-156">0 회 이상</span><span class="sxs-lookup"><span data-stu-id="587b1-156">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="587b1-157">한 번 이상</span><span class="sxs-lookup"><span data-stu-id="587b1-157">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="587b1-158">0 번 또는 1 번.</span><span class="sxs-lookup"><span data-stu-id="587b1-158">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="587b1-159">적어도 `n` 한 `m` 번 이상.</span><span class="sxs-lookup"><span data-stu-id="587b1-159">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="587b1-160">별표 ( `*` )는 이전 요소를 0 번 이상 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-160">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="587b1-161">따라서 요소가 없는 입력 문자열도 일치 하는 항목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-161">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="587b1-162">더하기 기호 ( `+` )는 이전 요소를 1 번 이상 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-162">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="587b1-163">물음표는 `?` 이전 요소를 0 번 또는 한 번 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-163">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="587b1-164">별표와 마찬가지로 `*` 요소가 없는 문자열도 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-164">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="587b1-165">`{n, m}`수량자를 사용 하 여 수량자를 세부적으로 제어할 수 있는 여러 가지 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-165">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="587b1-166">두 번째 요소 `m` 와 쉼표는 `,` 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-166">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="587b1-167">수량자</span><span class="sxs-lookup"><span data-stu-id="587b1-167">Quantifier</span></span> |                <span data-ttu-id="587b1-168">설명</span><span class="sxs-lookup"><span data-stu-id="587b1-168">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="587b1-169">정확히 일치 하 `n` 는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-169">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="587b1-170">최소 횟수를 찾습니다 `n` .</span><span class="sxs-lookup"><span data-stu-id="587b1-170">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="587b1-171">`n`와 횟수를 일치 시킵니다 `m` .</span><span class="sxs-lookup"><span data-stu-id="587b1-171">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="587b1-172">앵커</span><span class="sxs-lookup"><span data-stu-id="587b1-172">Anchors</span></span>

<span data-ttu-id="587b1-173">앵커를 사용 하면 입력 문자열 내의 일치 위치에 따라 일치가 성공 하거나 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-173">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="587b1-174">일반적으로 사용 되는 두 앵커는 `^` 및 `$` 입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-174">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="587b1-175">캐럿은 문자열의 `^` 시작과 일치 하며 `$` 문자열의 끝과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-175">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="587b1-176">앵커를 사용 하면 원치 않는 문자를 삭제 하는 동시에 특정 위치에 있는 텍스트를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-176">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="587b1-177">앵커를 포함 하는 regex를 정의할 때 큰따옴표 `$` () 대신 작은따옴표 ()를 사용 하 여 regex를 묶어야 합니다 `'` `"` . 그렇지 않으면 PowerShell에서 식을 변수로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-177">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="587b1-178">PowerShell에서 앵커를 사용 하는 경우 **regexoptions.singleline** 및 **Multiline** 정규식 옵션의 차이점을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-178">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="587b1-179">**여러** 줄 모드: 여러 줄 모드는 `^` `$` 입력 문자열의 시작 및 끝이 아니라 모든 줄의 시작 부분을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-179">**Multiline**: Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="587b1-180">**Regexoptions.singleline**: regexoptions.singleline 모드는 입력 문자열을 **regexoptions.singleline** 로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-180">**Singleline**: Singleline mode treats the input string as a **SingleLine**.</span></span>
  <span data-ttu-id="587b1-181">`.`줄 바꿈 문자를 제외한 모든 문자와 일치 하는 대신 문자를 모든 문자 (줄바꿈 포함)와 일치 하도록 강제 합니다 `\n` .</span><span class="sxs-lookup"><span data-stu-id="587b1-181">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="587b1-182">이러한 옵션 및 사용 방법에 대 한 자세한 내용은 [정규식 언어-빠른 참조](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="587b1-182">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="587b1-183">문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="587b1-183">Escaping characters</span></span>

<span data-ttu-id="587b1-184">백슬래시 ( `\` )는 문자를 이스케이프 하는 데 사용 되므로 정규식 엔진에서 구문 분석 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-184">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="587b1-185">다음 문자는 예약 되어 `[]().\^$|?*+{}` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-185">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="587b1-186">입력 문자열에서 이러한 문자를 일치 시키려면 패턴에서 이러한 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-186">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="587b1-187">텍스트를 이스케이프할 수 있는 정규식 클래스의 정적 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-187">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="587b1-188">문자 클래스에서 사용 되는 기존 백슬래시를 포함 하 여 모든 예약 된 정규식 문자를 이스케이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-188">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="587b1-189">이스케이프 해야 하는 패턴 부분 에서만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-189">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="587b1-190">기타 문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="587b1-190">Other character escapes</span></span>

<span data-ttu-id="587b1-191">특수 문자 형식을 일치 시키는 데 사용할 수 있는 예약 된 문자 이스케이프도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-191">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="587b1-192">일반적으로 사용 되는 문자 이스케이프는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-192">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="587b1-193">문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="587b1-193">Character Escape</span></span>  |<span data-ttu-id="587b1-194">설명</span><span class="sxs-lookup"><span data-stu-id="587b1-194">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="587b1-195">탭과 일치</span><span class="sxs-lookup"><span data-stu-id="587b1-195">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="587b1-196">줄 바꿈 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-196">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="587b1-197">캐리지 리턴 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-197">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="587b1-198">그룹, 캡처 및 대체</span><span class="sxs-lookup"><span data-stu-id="587b1-198">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="587b1-199">그룹화 구문은 입력 문자열을 캡처하거나 무시할 수 있는 부분 문자열로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-199">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="587b1-200">그룹화 된 부분 문자열을 하위 식 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-200">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="587b1-201">기본적으로 부분식은 번호 매기기 그룹에 캡처되고 이름을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-201">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="587b1-202">그룹화 구문은 괄호로 묶은 정규식입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-202">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="587b1-203">포함 된 정규식과 일치 하는 모든 텍스트가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-203">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="587b1-204">다음 예제에서는 입력 텍스트를 두 개의 캡처링 그룹으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-204">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="587b1-205">`$Matches` **Hashtable** 자동 변수를 사용 하 여 캡처된 텍스트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-205">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="587b1-206">전체 일치 항목을 나타내는 텍스트는 키에 저장 됩니다 `0` .</span><span class="sxs-lookup"><span data-stu-id="587b1-206">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="587b1-207">캡처는 왼쪽에서 오른쪽으로 증가 하는 숫자 **정수** 키에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-207">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="587b1-208">캡처 `1` 는 사용자 이름, 캡처에 사용자 이름만 포함 될 때까지 모든 텍스트를 포함 합니다 `2` .</span><span class="sxs-lookup"><span data-stu-id="587b1-208">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

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
> <span data-ttu-id="587b1-209">`0`키가 **정수** 입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-209">The `0` key is an **Integer**.</span></span> <span data-ttu-id="587b1-210">모든 **Hashtable** 메서드를 사용 하 여 저장 된 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-210">You can use any **Hashtable** method to access the value stored.</span></span>
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

#### <a name="named-captures"></a><span data-ttu-id="587b1-211">명명 된 캡처</span><span class="sxs-lookup"><span data-stu-id="587b1-211">Named Captures</span></span>

<span data-ttu-id="587b1-212">기본적으로 캡처는 왼쪽에서 오른쪽으로 오름차순으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-212">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="587b1-213">캡처링 그룹에 **이름을** 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-213">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="587b1-214">이 **이름은** `$Matches` **Hashtable** 자동 변수의 키가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-214">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="587b1-215">캡처링 그룹 내에서를 사용 `?<keyname>` 하 여 캡처된 데이터를 명명 된 키 아래에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-215">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

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

<span data-ttu-id="587b1-216">다음 예에서는 Windows 보안 로그에 최신 로그 항목을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-216">The following example stores the newest log entry in the Windows Security Log.</span></span>
<span data-ttu-id="587b1-217">제공 된 정규식은 메시지에서 사용자 이름과 도메인을 추출 하 여 키 아래에 저장 합니다.**N** 은 이름, 도메인의 경우 **D** 입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-217">The provided regular expression extracts the username and domain from the message and stores them under the keys:**N** for name and **D** for domain.</span></span>

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

<span data-ttu-id="587b1-218">자세한 내용은 [정규식의 그룹화 구문](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="587b1-218">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="587b1-219">정규식의 대체</span><span class="sxs-lookup"><span data-stu-id="587b1-219">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="587b1-220">정규식을 연산자와 함께 사용 하면 `-replace` 캡처된 텍스트를 사용 하 여 동적으로 텍스트를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-220">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="587b1-221">`<input>`: 검색할 문자열</span><span class="sxs-lookup"><span data-stu-id="587b1-221">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="587b1-222">`<original>`: 입력 문자열을 검색 하는 데 사용 되는 정규식입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-222">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="587b1-223">`<substitute>`: 입력 문자열에서 찾은 일치 항목을 대체할 정규식 대체 식입니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-223">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="587b1-224">`<original>`및 `<substitute>` 피연산자는 문자 이스케이프와 같은 정규식 엔진의 규칙에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-224">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="587b1-225">캡처링 그룹은 문자열에서 참조할 수 있습니다 `<substitute>` .</span><span class="sxs-lookup"><span data-stu-id="587b1-225">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="587b1-226">대체는 그룹 식별자 앞에 있는 문자를 사용 하 여 수행 됩니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="587b1-226">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="587b1-227">캡처링 그룹을 참조 하는 두 가지 방법으로는 **번호** 및 **이름을** 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-227">Two ways to reference capturing groups are by **Number** and by **Name**.</span></span>

- <span data-ttu-id="587b1-228">**번호** 캡처링 그룹은 왼쪽에서 오른쪽으로 번호가 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-228">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="587b1-229">이름 **으로** 캡처링 그룹은 이름으로 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-229">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="587b1-230">`$&`식은 일치 하는 모든 텍스트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-230">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="587b1-231">문자는 `$` 문자열 확장에 사용 되므로 대체를 사용 하 여 리터럴 문자열을 사용 하거나 `$` 큰따옴표를 사용 하는 경우 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-231">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
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
> <span data-ttu-id="587b1-232">또한을 `$` 리터럴 문자로 사용 하려면 `$$` 일반 이스케이프 문자 대신을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-232">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="587b1-233">큰따옴표를 사용 하는 경우에도의 모든 인스턴스를 이스케이프 `$` 하 여 잘못 된 대체가 발생 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="587b1-233">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
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

<span data-ttu-id="587b1-234">자세한 내용은 [정규식의 대체](/dotnet/standard/base-types/substitutions-in-regular-expressions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="587b1-234">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="587b1-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="587b1-235">See also</span></span>

[<span data-ttu-id="587b1-236">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="587b1-236">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="587b1-237">about_Operators</span><span class="sxs-lookup"><span data-stu-id="587b1-237">about_Operators</span></span>](about_Operators.md)

