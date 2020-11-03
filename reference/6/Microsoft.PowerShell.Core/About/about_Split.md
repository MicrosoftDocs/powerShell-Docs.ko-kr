---
description: Split 연산자를 사용 하 여 하나 이상의 문자열을 부분 문자열로 분할 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/20/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: 520aac1fd1aae4f1f0f4a12a10bc4f5c7f258731
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221129"
---
# <a name="about-split"></a><span data-ttu-id="05843-104">분할 정보</span><span class="sxs-lookup"><span data-stu-id="05843-104">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="05843-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="05843-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="05843-106">Split 연산자를 사용 하 여 하나 이상의 문자열을 부분 문자열로 분할 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-106">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="05843-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="05843-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="05843-108">Split 연산자는 하나 이상의 문자열을 부분 문자열로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-108">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="05843-109">분할 작업의 다음 요소를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-109">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="05843-110">문자가.</span><span class="sxs-lookup"><span data-stu-id="05843-110">Delimiter.</span></span> <span data-ttu-id="05843-111">기본값은 공백 이지만 구분 기호를 지정 하는 문자, 문자열, 패턴 또는 스크립트 블록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-111">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="05843-112">PowerShell의 Split 연산자는 간단한 문자 대신 구분 기호에서 정규식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-112">The Split operator in PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="05843-113">최대 부분 문자열 수입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-113">Maximum number of substrings.</span></span> <span data-ttu-id="05843-114">기본값은 모든 부분 문자열을 반환 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-114">The default is to return all substrings.</span></span> <span data-ttu-id="05843-115">하위 문자열 수보다 작은 숫자를 지정 하면 나머지 부분 문자열이 마지막 부분 문자열에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-115">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="05843-116">SimpleMatch 및 Multiline와 같이 구분 기호가 일치 하는 조건을 지정 하는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-116">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="05843-117">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05843-117">SYNTAX</span></span>

<span data-ttu-id="05843-118">다음 다이어그램에서는-split 연산자의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05843-118">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="05843-119">명령에는 매개 변수 이름이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-119">The parameter names do not appear in the command.</span></span> <span data-ttu-id="05843-120">매개 변수 값만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-120">Include only the parameter values.</span></span> <span data-ttu-id="05843-121">값은 구문 다이어그램에 지정 된 순서 대로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-121">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="05843-122">`-iSplit` `-cSplit` `-split` 모든 이진 분할 문 (구분 기호 또는 스크립트 블록을 포함 하는 Split 문)에서 또는를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-122">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="05843-123">`-iSplit`및 `-split` 연산자는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-123">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="05843-124">`-cSplit`연산자는 대/소문자를 구분 합니다. 즉, 구분 기호 규칙이 적용 될 때 대/소문자가 고려 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-124">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="05843-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05843-125">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="05843-126">\<String\> 또는 \<String[]\></span><span class="sxs-lookup"><span data-stu-id="05843-126">\<String\> or \<String[]\></span></span>

<span data-ttu-id="05843-127">분할할 문자열을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-127">Specifies one or more strings to be split.</span></span> <span data-ttu-id="05843-128">여러 문자열을 전송 하는 경우 모든 문자열이 동일한 구분 기호 규칙을 사용 하 여 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-128">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="05843-129">예제:</span><span class="sxs-lookup"><span data-stu-id="05843-129">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="05843-130">부분 문자열의 끝을 식별 하는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-130">The characters that identify the end of a substring.</span></span> <span data-ttu-id="05843-131">기본 구분 기호는 공백 및 인쇄할 수 없는 문자 (예: 줄 바꿈 ( \` n) 및 tab (t))를 포함 하는 공백입니다 \` .</span><span class="sxs-lookup"><span data-stu-id="05843-131">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="05843-132">문자열이 분할 되 면 모든 부분 문자열에서 구분 기호가 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-132">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="05843-133">예제:</span><span class="sxs-lookup"><span data-stu-id="05843-133">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="05843-134">기본적으로 구분 기호는 결과에서 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-134">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="05843-135">구분 기호의 전체 또는 일부를 유지 하려면 유지 하려는 부분을 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-135">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="05843-136">\<Max-substrings\>매개 변수가 추가 되 면 명령이 컬렉션을 분할 하는 경우이 매개 변수가 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-136">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="05843-137">출력의 일부로 구분 기호를 포함 하도록 선택 하는 경우 명령은 출력의 일부로 구분 기호를 반환 합니다. 그러나 출력의 일부로 구분 기호를 반환 하도록 문자열을 분할 하는 것은 분할으로 계산 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-137">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="05843-138">예제:</span><span class="sxs-lookup"><span data-stu-id="05843-138">Examples:</span></span>

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

<span data-ttu-id="05843-139">다음 예제에서 \<Max-substrings\> 은 3으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-139">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="05843-140">이로 인해 문자열 값의 세 분할이 발생 하지만 결과 출력에 총 5 개의 문자열이 있습니다. 구분 기호는 분할 후에 포함 되며, 최대 세 부분 문자열에 도달할 때까지 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-140">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="05843-141">최종 부분 문자열의 추가 구분 기호는 부분 문자열의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-141">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="05843-142">문자열이 분할 되는 최대 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-142">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="05843-143">기본값은 구분 기호로 분할 된 모든 부분 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-143">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="05843-144">부분 문자열이 더 있으면 최종 부분 문자열에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-144">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="05843-145">부분 문자열이 더 적으면 모든 부분 문자열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-145">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="05843-146">값 0 및 음수 값은 모든 부분 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-146">A value of 0 and negative values return all the substrings.</span></span>

<span data-ttu-id="05843-147">Max-하위 문자열은 반환 되는 최대 개체 수를 지정 하지 않습니다. 해당 값은 문자열이 분할 되는 최대 횟수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-147">Max-substrings does not specify the maximum number of objects that are returned; its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="05843-148">분할 연산자에 둘 이상의 문자열 (문자열 배열)을 전송 하는 경우 최대 부분 문자열 제한은 각 문자열에 개별적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-148">If you submit more than one string (an array of strings) to the Split operator , the Max-substrings limit is applied to each string separately.</span></span>

<span data-ttu-id="05843-149">예제:</span><span class="sxs-lookup"><span data-stu-id="05843-149">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="05843-150">구분 기호를 적용 하는 규칙을 지정 하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-150">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="05843-151">식은 $true 또는 $false로 계산 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-151">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="05843-152">스크립트 블록을 중괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-152">Enclose the script block in braces.</span></span>

<span data-ttu-id="05843-153">예제:</span><span class="sxs-lookup"><span data-stu-id="05843-153">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="05843-154">옵션 이름을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-154">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="05843-155">옵션은 \<Max-substrings\> 매개 변수가 문에 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-155">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="05843-156">Options 매개 변수에 대 한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-156">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="05843-157">SimpleMatch 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-157">The SimpleMatch options are:</span></span>

- <span data-ttu-id="05843-158">**SimpleMatch** : 구분 기호를 계산할 때 간단한 문자열 비교를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-158">**SimpleMatch** : Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="05843-159">RegexMatch와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-159">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="05843-160">**IgnoreCase** :-csplit 연산자가 지정 된 경우에도 대/소문자를 구분 하지 않는 일치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-160">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="05843-161">RegexMatch 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-161">The RegexMatch options are:</span></span>

- <span data-ttu-id="05843-162">**RegexMatch** : 정규식 일치를 사용 하 여 구분 기호를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-162">**RegexMatch** : Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="05843-163">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="05843-163">This is the default behavior.</span></span> <span data-ttu-id="05843-164">SimpleMatch와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-164">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="05843-165">**IgnoreCase** :-csplit 연산자가 지정 된 경우에도 대/소문자를 구분 하지 않는 일치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-165">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="05843-166">**Regexoptions.cultureinvariant** : 구분 기호를 evaluting 때 언어의 문화권 차이를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-166">**CultureInvariant** : Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="05843-167">RegexMatch에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-167">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="05843-168">**Regexoptions.ignorepatternwhitespace** : 숫자 기호 (#)로 표시 된 이스케이프 되지 않은 공백과 주석을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-168">**IgnorePatternWhitespace** : Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="05843-169">RegexMatch에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="05843-170">**여러** 줄 모드: 여러 줄 모드는 `^` `$` 입력 문자열의 시작 및 끝이 아니라 모든 줄의 시작 부분을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="05843-170">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="05843-171">**Regexoptions.singleline** : regexoptions.singleline 모드는 입력 문자열을 *regexoptions.singleline* 로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-171">**Singleline** : Singleline mode treats the input string as a *SingleLine*.</span></span>
  <span data-ttu-id="05843-172">`.`줄 바꿈 문자를 제외한 모든 문자와 일치 하는 대신 문자를 모든 문자 (줄바꿈 포함)와 일치 하도록 강제 합니다 `\n` .</span><span class="sxs-lookup"><span data-stu-id="05843-172">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="05843-173">**Regexoptions.explicitcapture** : 명시적 캡처 그룹만 결과 목록에 반환 되도록 명명 되지 않은 일치 그룹을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-173">**ExplicitCapture** : Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="05843-174">RegexMatch에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-174">Valid only with RegexMatch.</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="05843-175">단항 및 이항 분할 연산자</span><span class="sxs-lookup"><span data-stu-id="05843-175">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="05843-176">단항 분할 연산자 ( `-split <string>` )의 우선 순위는 쉼표 보다 높습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-176">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="05843-177">결과적으로, 쉼표로 구분 된 문자열 목록을 단항 분할 연산자에 제출 하면 첫 번째 쉼표 앞의 첫 번째 문자열만 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-177">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="05843-178">다음 패턴 중 하나를 사용 하 여 둘 이상의 문자열을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-178">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="05843-179">이진 분할 연산자 ( \<string[]\> -split) 사용 \<delimiter\></span><span class="sxs-lookup"><span data-stu-id="05843-179">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="05843-180">모든 문자열을 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-180">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="05843-181">변수에 문자열을 저장 한 다음 split 연산자에 변수를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-181">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="05843-182">다음과 같은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05843-182">Consider the following example:</span></span>

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a><span data-ttu-id="05843-183">예제</span><span class="sxs-lookup"><span data-stu-id="05843-183">EXAMPLES</span></span>

<span data-ttu-id="05843-184">다음 문은 공백에서 문자열을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-184">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="05843-185">다음 문은 임의의 쉼표에서 문자열을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-185">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="05843-186">다음 문은 "er" 패턴에서 문자열을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-186">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="05843-187">다음 문은 "N" 문자에서 대/소문자를 구분 하는 분할을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-187">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="05843-188">다음 문은 "e" 및 "t"에서 문자열을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-188">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

<span data-ttu-id="05843-189">다음 문은 "e"와 "r"에서 문자열을 분할 하지만 결과 부분 문자열을 6 개의 부분 문자열로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-189">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="05843-190">다음 문은 문자열을 세 개의 부분 문자열로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-190">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="05843-191">다음 문은 두 문자열을 세 부분 문자열로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-191">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="05843-192">한도는 각 문자열에 독립적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-192">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="05843-193">다음 문은 여기에서 문자열의 각 줄을 첫 번째 자릿수로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-193">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="05843-194">여러 줄 옵션을 사용 하 여 각 줄과 문자열의 시작 부분을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-194">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="05843-195">0은 Max 부분 문자열 매개 변수의 "모두 반환" 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05843-195">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="05843-196">최대 부분 문자열 값이 지정 된 경우에만 여러 줄 등의 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-196">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="05843-197">다음 문에서는 백슬래시 문자를 사용 하 여 점 (.) 구분 기호를 이스케이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-197">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="05843-198">기본 RegexMatch를 사용 하면 따옴표 (".")로 묶인 점이 줄 바꿈 문자를 제외한 모든 문자와 일치 하는 것으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05843-198">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="05843-199">결과적으로 Split 문은 줄 바꿈 문자를 제외한 모든 문자에 대해 빈 줄을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-199">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```output
This
is
a
test
```

<span data-ttu-id="05843-200">다음 문은 SimpleMatch 옵션을 사용 하 여-split 연산자를 지시 하 여 점 (.) 구분 기호를 리터럴로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-200">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="05843-201">0은 Max 부분 문자열 매개 변수의 "모두 반환" 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05843-201">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="05843-202">SimpleMatch와 같은 옵션을 사용할 수 있습니다 .이 옵션은 Max-하위 문자열 값이 지정 된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05843-202">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```output
This
is
a
test
```

<span data-ttu-id="05843-203">다음 문은 변수 값에 따라 두 구분 기호 중 하나에서 문자열을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="05843-203">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="05843-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05843-204">SEE ALSO</span></span>

[<span data-ttu-id="05843-205">Split-Path</span><span class="sxs-lookup"><span data-stu-id="05843-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="05843-206">about_Operators</span><span class="sxs-lookup"><span data-stu-id="05843-206">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="05843-207">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="05843-207">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="05843-208">about_join</span><span class="sxs-lookup"><span data-stu-id="05843-208">about_Join</span></span>](about_Join.md)
