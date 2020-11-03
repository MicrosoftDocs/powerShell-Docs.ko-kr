---
description: PowerShell에서 명령을 구문 분석 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: 200a3aa7aac6477a2b2d3660167621132514c333
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221393"
---
# <a name="about-parsing"></a><span data-ttu-id="29f6c-104">구문 분석 정보</span><span class="sxs-lookup"><span data-stu-id="29f6c-104">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="29f6c-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="29f6c-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="29f6c-106">PowerShell에서 명령을 구문 분석 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-106">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="29f6c-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="29f6c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="29f6c-108">명령 프롬프트에서 명령을 입력 하면 PowerShell에서 명령 텍스트를 _토큰_ 이라는 일련의 세그먼트로 분리 한 다음 각 토큰을 해석 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-108">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="29f6c-109">예를 들어 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-109">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="29f6c-110">PowerShell은 명령을 두 개의 토큰으로 분리 `Write-Host` 하 `book` 고 두 가지 주요 구문 분석 모드 (식 모드 및 인수 모드) 중 하나를 사용 하 여 각 토큰을 독립적으로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-110">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="29f6c-111">PowerShell에서 명령 입력을 구문 분석 하면 cmdlet 또는 네이티브 실행 파일에 명령 이름을 확인 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-111">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="29f6c-112">명령 이름에 정확히 일치 하는 항목이 없으면 PowerShell이 명령 앞 `Get-` 에 기본 동사로 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-112">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="29f6c-113">예를 들어 PowerShell `Process` 은로 구문 분석 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-113">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="29f6c-114">다음과 같은 이유로이 기능을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-114">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="29f6c-115">비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-115">It's inefficient.</span></span> <span data-ttu-id="29f6c-116">이렇게 하면 PowerShell에서 여러 번 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-116">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="29f6c-117">같은 이름의 외부 프로그램을 먼저 확인 하므로 의도 한 cmdlet을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-117">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="29f6c-118">`Get-Help` 및는 `Get-Command` 동사 없는 이름을 인식 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-118">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="29f6c-119">식 모드</span><span class="sxs-lookup"><span data-stu-id="29f6c-119">Expression mode</span></span>

<span data-ttu-id="29f6c-120">식 모드는 스크립팅 언어의 값 조작에 필요한 식을 결합 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-120">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="29f6c-121">식은 PowerShell 구문에서 값에 대 한 표현으로, 단순 또는 복합 일 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-121">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="29f6c-122">리터럴 식은 해당 값을 직접 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-122">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="29f6c-123">변수 식은 참조 하는 변수의 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-123">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="29f6c-124">연산자는 평가를 위해 다른 식을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-124">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="29f6c-125">_문자열 리터럴은_ 따옴표 안에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-125">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="29f6c-126">_숫자_ 는 일련의 문자가 아닌 숫자 값으로 처리 됩니다 (이스케이프 되지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="29f6c-126">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="29f6c-127">_Operators_ And와 같은 단항 연산자 및 `-` `-not` 및와 같은 이항 연산자를 포함 하 `+` 는 연산자 `-gt` 는 연산자로 해석 되 고 해당 인수 (피연산자)에 대해 해당 작업을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-127">_Operators_ , including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="29f6c-128">_특성 및 변환 식은_ 식으로 구문 분석 되 고 하위 식 (예:)에 적용 `[int] '7'` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-128">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="29f6c-129">_변수 참조_ 는 값으로 계산 되지만 _스 플랫_ (즉, 미리 채워진 매개 변수 집합 붙여넣기)는 사용할 수 없으며 파서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-129">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="29f6c-130">다른 모든 항목은 호출할 명령으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-130">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="29f6c-131">인수 모드</span><span class="sxs-lookup"><span data-stu-id="29f6c-131">Argument mode</span></span>

<span data-ttu-id="29f6c-132">구문 분석할 때 PowerShell은 먼저 입력을 식으로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-132">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="29f6c-133">그러나 명령 호출이 발생 하면 구문 분석은 인수 모드에서 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-133">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="29f6c-134">인수 모드는 셸 환경의 명령에 대 한 인수 및 매개 변수를 구문 분석 하기 위해 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-134">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="29f6c-135">모든 입력은 다음 구문 중 하나를 사용 하지 않는 한 확장 가능한 문자열로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-135">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="29f6c-136">달러 기호 ( `$` )는 변수 참조를 시작 합니다 (뒤에 유효한 변수 이름이 오는 경우에만). 그렇지 않은 경우 확장 가능한 문자열의 일부로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-136">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="29f6c-137">따옴표 ( `'` 및 `"` )는 문자열 값을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-137">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="29f6c-138">괄호 ( `(` 및 `)` )는 새 식을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-138">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="29f6c-139">하위 식 연산자 ( `$(` ... `)` ) 정하는 포함 식.</span><span class="sxs-lookup"><span data-stu-id="29f6c-139">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="29f6c-140">중괄호 ( `{` 및 `}` )는 새 스크립트 블록을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-140">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="29f6c-141">초기 at 기호 ( `@` )는 스 플랫 ( `@args` ), 배열 ( `@(1,2,3)` ) 및 해시 테이블 ()과 같은 식 구문을 시작 `@{a=1;b=2}` 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-141">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="29f6c-142">쉼표 ()는로 전달 되는 `,` 명령이 네이티브 응용 프로그램 일 경우를 제외 하 고 배열로 전달 되는 목록을 소개 합니다 .이 경우 확장 가능한 문자열의 일부로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-142">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="29f6c-143">초기, 연속 또는 후행 쉼표는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-143">Initial, consecutive or trailing commas are not supported.</span></span>

<span data-ttu-id="29f6c-144">포함 식의 값은 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-144">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="29f6c-145">다음 표에서는 식 모드 및 인수 모드에서 처리 된 값의 몇 가지 예제와 이러한 값의 평가를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-145">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="29f6c-146">변수의 값이 인 것으로 가정 `a` `4` 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-146">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="29f6c-147">예제</span><span class="sxs-lookup"><span data-stu-id="29f6c-147">Example</span></span>        |    <span data-ttu-id="29f6c-148">모드</span><span class="sxs-lookup"><span data-stu-id="29f6c-148">Mode</span></span>    |      <span data-ttu-id="29f6c-149">결과</span><span class="sxs-lookup"><span data-stu-id="29f6c-149">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="29f6c-150">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-150">Expression</span></span> | <span data-ttu-id="29f6c-151">2 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-151">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="29f6c-152">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-152">Expression</span></span> | <span data-ttu-id="29f6c-153">"2" (명령)</span><span class="sxs-lookup"><span data-stu-id="29f6c-153">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="29f6c-154">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-154">Expression</span></span> | <span data-ttu-id="29f6c-155">2 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-155">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="29f6c-156">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-156">Expression</span></span> | <span data-ttu-id="29f6c-157">4 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-157">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="29f6c-158">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-158">Argument</span></span>   | <span data-ttu-id="29f6c-159">"2 + 2" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-159">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="29f6c-160">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-160">Expression</span></span> | <span data-ttu-id="29f6c-161">4 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-161">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="29f6c-162">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-162">Expression</span></span> | <span data-ttu-id="29f6c-163">4 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-163">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="29f6c-164">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-164">Expression</span></span> | <span data-ttu-id="29f6c-165">4 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-165">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="29f6c-166">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-166">Expression</span></span> | <span data-ttu-id="29f6c-167">6 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-167">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="29f6c-168">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-168">Argument</span></span>   | <span data-ttu-id="29f6c-169">4 + 2 (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-169">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="29f6c-170">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-170">Argument</span></span>   | <span data-ttu-id="29f6c-171">"$-" (명령)</span><span class="sxs-lookup"><span data-stu-id="29f6c-171">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="29f6c-172">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-172">Argument</span></span>   | <span data-ttu-id="29f6c-173">"$-" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-173">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="29f6c-174">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-174">Expression</span></span> | <span data-ttu-id="29f6c-175">"a $ a" (명령)</span><span class="sxs-lookup"><span data-stu-id="29f6c-175">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="29f6c-176">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-176">Argument</span></span>   | <span data-ttu-id="29f6c-177">"a4" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-177">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="29f6c-178">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-178">Expression</span></span> | <span data-ttu-id="29f6c-179">"a $ a" (명령)</span><span class="sxs-lookup"><span data-stu-id="29f6c-179">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="29f6c-180">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-180">Argument</span></span>   | <span data-ttu-id="29f6c-181">"a $ a" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-181">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="29f6c-182">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-182">Expression</span></span> | <span data-ttu-id="29f6c-183">"a $ a" (명령)</span><span class="sxs-lookup"><span data-stu-id="29f6c-183">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="29f6c-184">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-184">Argument</span></span>   | <span data-ttu-id="29f6c-185">"a4" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-185">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="29f6c-186">식</span><span class="sxs-lookup"><span data-stu-id="29f6c-186">Expression</span></span> | <span data-ttu-id="29f6c-187">"a $ (2)" (명령)</span><span class="sxs-lookup"><span data-stu-id="29f6c-187">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="29f6c-188">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-188">Argument</span></span>   | <span data-ttu-id="29f6c-189">"a2" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-189">"a2" (string)</span></span>     |

<span data-ttu-id="29f6c-190">모든 토큰은 부울 또는 문자열과 같은 일종의 개체 형식으로 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-190">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="29f6c-191">PowerShell에서 식의 개체 유형을 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-191">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="29f6c-192">개체 형식은 명령에 필요한 매개 변수의 형식과 PowerShell이 인수를 올바른 형식으로 변환 하는 방법을 인식 하는지 여부에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-192">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="29f6c-193">다음 표에서는 식에서 반환 하는 값에 할당 된 형식의 몇 가지 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-193">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="29f6c-194">예제</span><span class="sxs-lookup"><span data-stu-id="29f6c-194">Example</span></span>          |    <span data-ttu-id="29f6c-195">모드</span><span class="sxs-lookup"><span data-stu-id="29f6c-195">Mode</span></span>    |     <span data-ttu-id="29f6c-196">결과</span><span class="sxs-lookup"><span data-stu-id="29f6c-196">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="29f6c-197">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-197">argument</span></span>   | <span data-ttu-id="29f6c-198">"! 1" (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-198">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="29f6c-199">expression</span><span class="sxs-lookup"><span data-stu-id="29f6c-199">expression</span></span> | <span data-ttu-id="29f6c-200">False (부울)</span><span class="sxs-lookup"><span data-stu-id="29f6c-200">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="29f6c-201">expression</span><span class="sxs-lookup"><span data-stu-id="29f6c-201">expression</span></span> | <span data-ttu-id="29f6c-202">2 (정수)</span><span class="sxs-lookup"><span data-stu-id="29f6c-202">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="29f6c-203">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-203">argument</span></span>   | <span data-ttu-id="29f6c-204">' A ', ' B ' (배열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-204">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="29f6c-205">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-205">argument</span></span>   | <span data-ttu-id="29f6c-206">' A, B ' (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-206">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="29f6c-207">expression</span><span class="sxs-lookup"><span data-stu-id="29f6c-207">expression</span></span> | <span data-ttu-id="29f6c-208">' A ', ' B ' (배열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-208">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="29f6c-209">인수</span><span class="sxs-lookup"><span data-stu-id="29f6c-209">argument</span></span>   | <span data-ttu-id="29f6c-210">': A B ' (문자열)</span><span class="sxs-lookup"><span data-stu-id="29f6c-210">':A B' (string)</span></span> |

<span data-ttu-id="29f6c-211">PowerShell 3.0에 도입 된 중지 구문 분석 기호 ()는 powershell `--%` 명령 또는 식으로 입력을 해석 하지 않도록 powershell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-211">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="29f6c-212">PowerShell에서 실행 프로그램을 호출 하는 경우 프로그램 인수 앞에 구문 분석 기호를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-212">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="29f6c-213">이 기법은 잘못 해석을 방지 하기 위해 이스케이프 문자를 사용 하는 것 보다 훨씬 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-213">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="29f6c-214">중지 구문 분석 기호가 나타나면 PowerShell은 줄의 나머지 문자를 리터럴로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-214">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="29f6c-215">표준 Windows 표기법을 사용 하는 환경 변수 (예:)에 대 한 값을 대체 하는 해석을 수행 합니다 `%USERPROFILE%` .</span><span class="sxs-lookup"><span data-stu-id="29f6c-215">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="29f6c-216">중지 구문 분석 기호는 다음 줄 바꿈 문자 또는 파이프라인 문자 까지만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-216">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="29f6c-217">연속 문자 ()를 사용 `` ` `` 하 여 효과를 확장 하거나 명령 구분 기호 ()를 사용 하 여 효과를 종료할 수 없습니다 `;` .</span><span class="sxs-lookup"><span data-stu-id="29f6c-217">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="29f6c-218">예를 들어 다음 명령은 **Icacls** 프로그램을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-218">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="29f6c-219">PowerShell 2.0에서이 명령을 실행 하려면 이스케이프 문자를 사용 하 여 misinterpreting에서 괄호를 사용 하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-219">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="29f6c-220">PowerShell 3.0 부터는 중지 구문 분석 기호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-220">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="29f6c-221">PowerShell은 다음 명령 문자열을 **Icacls** 프로그램으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-221">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="29f6c-222">중지 구문 분석 기호는 Windows 플랫폼 에서만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29f6c-222">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="29f6c-223">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29f6c-223">SEE ALSO</span></span>

[<span data-ttu-id="29f6c-224">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="29f6c-224">about_Command_Syntax</span></span>](about_Command_Syntax.md)
