---
description: PowerShell 연산자를 우선 순위 대로 나열 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 6de44dd24d0b1b1826c94d838cca11f0cef6b7f2
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483216"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="cd9e4-104">연산자 우선 순위 정보</span><span class="sxs-lookup"><span data-stu-id="cd9e4-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="cd9e4-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="cd9e4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="cd9e4-106">PowerShell 연산자를 우선 순위 대로 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="cd9e4-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="cd9e4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="cd9e4-108">PowerShell 연산자를 사용 하 여 간단 하지만 강력한 식을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="cd9e4-109">이 항목에서는 연산자를 우선 순위 대로 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="cd9e4-110">우선 순위는 동일한 식에 여러 개의 연산자가 나타날 때 PowerShell에서 연산자를 평가 하는 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="cd9e4-111">연산자의 우선 순위가 같으면 PowerShell은 식에 표시 된 대로 왼쪽에서 오른쪽으로 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="cd9e4-112">예외는 오른쪽에서 왼쪽으로 계산 되는 할당 연산자, 캐스트 연산자 및 부정 연산자 ( `!` , `-not` , `-bnot` )입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="cd9e4-113">괄호와 같은 인클로저를 사용 하 여 표준 우선 순위를 재정의 하 고 PowerShell에서 식에 포함 되지 않은 부분을 계산 하도록 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="cd9e4-114">다음 목록에서는 연산자가 평가 되는 순서 대로 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="cd9e4-115">같은 줄 또는 같은 그룹에 있는 연산자는 우선 순위가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="cd9e4-116">연산자 열에 연산자가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-116">The Operator column lists the operators.</span></span> <span data-ttu-id="cd9e4-117">참조 열에는 연산자가 설명 된 PowerShell 도움말 항목이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="cd9e4-118">항목을 표시 하려면를 입력 `get-help <topic-name>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="cd9e4-119">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="cd9e4-119">OPERATOR</span></span>         |           <span data-ttu-id="cd9e4-120">참조</span><span class="sxs-lookup"><span data-stu-id="cd9e4-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | <span data-ttu-id="cd9e4-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-122">`. ?.` (멤버 액세스)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-122">`. ?.` (member access)</span></span>   | <span data-ttu-id="cd9e4-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-124">`::` 정적인</span><span class="sxs-lookup"><span data-stu-id="cd9e4-124">`::` (static)</span></span>            | <span data-ttu-id="cd9e4-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-126">`[0] ?[0]` (인덱스 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-126">`[0] ?[0]` (index operator)</span></span> | <span data-ttu-id="cd9e4-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-127">[about_Operators][]</span></span>         |
| <span data-ttu-id="cd9e4-128">`[int]` (캐스트 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="cd9e4-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-130">`-split` 플러스</span><span class="sxs-lookup"><span data-stu-id="cd9e4-130">`-split` (unary)</span></span>         | <span data-ttu-id="cd9e4-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-131">[about_Split][]</span></span>                |
| <span data-ttu-id="cd9e4-132">`-join` 플러스</span><span class="sxs-lookup"><span data-stu-id="cd9e4-132">`-join` (unary)</span></span>          | <span data-ttu-id="cd9e4-133">[about_join][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="cd9e4-134">`,` (쉼표 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-134">`,` (comma operator)</span></span>     | <span data-ttu-id="cd9e4-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="cd9e4-136">[about_assignment_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="cd9e4-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="cd9e4-138">`..` (범위 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-138">`..` (range operator)</span></span>    | <span data-ttu-id="cd9e4-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-140">`-f` (format 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-140">`-f` (format operator)</span></span>   | <span data-ttu-id="cd9e4-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-142">`-` (단항/부정)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="cd9e4-143">[about_arithmetic_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="cd9e4-144">[about_arithmetic_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="cd9e4-145">[about_arithmetic_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="cd9e4-146">다음 연산자 그룹의 우선 순위가 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="cd9e4-147">대/소문자를 구분 하 고 명시적으로 대/소문자를 구분 하지 않는 변형은 동일한 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="cd9e4-148">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="cd9e4-148">OPERATOR</span></span>          |           <span data-ttu-id="cd9e4-149">참조</span><span class="sxs-lookup"><span data-stu-id="cd9e4-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="cd9e4-150">`-split` 바이너리</span><span class="sxs-lookup"><span data-stu-id="cd9e4-150">`-split` (binary)</span></span>         | <span data-ttu-id="cd9e4-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-151">[about_Split][]</span></span>                |
| <span data-ttu-id="cd9e4-152">`-join` 바이너리</span><span class="sxs-lookup"><span data-stu-id="cd9e4-152">`-join` (binary)</span></span>          | <span data-ttu-id="cd9e4-153">[about_join][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="cd9e4-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="cd9e4-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="cd9e4-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="cd9e4-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="cd9e4-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="cd9e4-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="cd9e4-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="cd9e4-161">다음 연산자가 우선 순위 대로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="cd9e4-162">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="cd9e4-162">OPERATOR</span></span>                 |           <span data-ttu-id="cd9e4-163">참조</span><span class="sxs-lookup"><span data-stu-id="cd9e4-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="cd9e4-164">[about_arithmetic_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="cd9e4-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="cd9e4-166">다음 항목은 진정한 연산자가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-166">The following items are not true operators.</span></span> <span data-ttu-id="cd9e4-167">이러한 구문은 식 구문이 아니라 PowerShell의 명령 구문에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="cd9e4-168">할당은 항상 마지막으로 발생 하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="cd9e4-169">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd9e4-169">SYNTAX</span></span>                   |           <span data-ttu-id="cd9e4-170">참조</span><span class="sxs-lookup"><span data-stu-id="cd9e4-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="cd9e4-171">`.` (점 소스)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="cd9e4-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-173">`&` 전화할</span><span class="sxs-lookup"><span data-stu-id="cd9e4-173">`&` (call)</span></span>                              | <span data-ttu-id="cd9e4-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-175">`? <if-true> : <if-false>` (삼진 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-175">`? <if-true> : <if-false>` (Ternary operator)</span></span> | <span data-ttu-id="cd9e4-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-176">[about_Operators][]</span></span>      |
| <span data-ttu-id="cd9e4-177">`??` (null coalese 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-177">`??` (null-coalese operator)</span></span>            | <span data-ttu-id="cd9e4-178">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-178">[about_Operators][]</span></span>            |
| <span data-ttu-id="cd9e4-179"><code>&#124;</code> (파이프라인 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-179"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="cd9e4-180">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-180">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="cd9e4-181">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-181">[about_Redirection][]</span></span>          |
| <span data-ttu-id="cd9e4-182"><code>&& &#124;&#124;</code> (파이프라인 체인 연산자)</span><span class="sxs-lookup"><span data-stu-id="cd9e4-182"><code>&& &#124;&#124;</code> (pipeline chain operators)</span></span> | <span data-ttu-id="cd9e4-183">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-183">[about_Operators][]</span></span> |
| `= += -= *= /= %= ??=`                  | <span data-ttu-id="cd9e4-184">[about_assignment_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-184">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="cd9e4-185">예제</span><span class="sxs-lookup"><span data-stu-id="cd9e4-185">EXAMPLES</span></span>

<span data-ttu-id="cd9e4-186">다음 두 명령은 산술 연산자와 괄호를 사용 하 여 PowerShell이 식의 포함 된 부분을 먼저 평가 하도록 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-186">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="cd9e4-187">다음 예에서는 로컬 디렉터리에서 읽기 전용 텍스트 파일을 가져와서 변수에 저장 합니다 `$read_only` .</span><span class="sxs-lookup"><span data-stu-id="cd9e4-187">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="cd9e4-188">다음 예제와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-188">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="cd9e4-189">파이프라인 연산자 ()는 `|` 대입 연산자 () 보다 우선 순위가 높기 때문에 `=` cmdlet이 가져오는 파일을 `Get-ChildItem` `Where-Object` 변수에 할당 하기 전에 필터링 하기 위해 cmdlet으로 보냅니다 `$read_only` .</span><span class="sxs-lookup"><span data-stu-id="cd9e4-189">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="cd9e4-190">다음 예에서는 index 연산자가 cast 연산자 보다 우선적으로 적용 되는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-190">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="cd9e4-191">이 식은 세 문자열의 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-191">This expression creates an array of three strings.</span></span> <span data-ttu-id="cd9e4-192">그런 다음 값이 0 인 index 연산자를 사용 하 여 첫 번째 문자열인 배열의 첫 번째 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-192">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="cd9e4-193">마지막으로, 선택한 개체를 문자열로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-193">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="cd9e4-194">이 경우 캐스트는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-194">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="cd9e4-195">이 식은 괄호를 사용 하 여 인덱스를 선택 하기 전에 캐스트 연산을 강제로 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-195">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="cd9e4-196">결과적으로 전체 배열은 (단일) 문자열로 캐스팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-196">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="cd9e4-197">그런 다음 index 연산자는 첫 번째 문자인 문자열 배열의 첫 번째 항목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-197">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="cd9e4-198">다음 예에서는 ( `-gt` 보다 큼) 연산자가 (LOGICAL AND) 연산자 보다 높은 우선 순위를 가지 므로 `-and` 식의 결과는 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-198">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="cd9e4-199">다음 식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-199">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="cd9e4-200">-And 연산자의 우선 순위가 더 높은 경우 답은 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-200">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="cd9e4-201">그러나이 예에서는 연산자 우선 순위를 관리 하는 중요 한 원칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-201">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="cd9e4-202">사용자가 해석 하기 어려운 식의 경우 기본 연산자 우선 순위를 강제로 적용 하는 경우에도 괄호를 사용 하 여 계산 순서를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-202">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="cd9e4-203">괄호를 사용 하면 스크립트를 읽고 유지 관리 하는 사용자가 원하는 대로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e4-203">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd9e4-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd9e4-204">SEE ALSO</span></span>

<span data-ttu-id="cd9e4-205">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-205">[about_Operators][]</span></span>

<span data-ttu-id="cd9e4-206">[about_assignment_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-206">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="cd9e4-207">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-207">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="cd9e4-208">[about_arithmetic_operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-208">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="cd9e4-209">[about_join][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-209">[about_Join][]</span></span>

<span data-ttu-id="cd9e4-210">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-210">[about_Redirection][]</span></span>

<span data-ttu-id="cd9e4-211">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-211">[about_Scopes][]</span></span>

<span data-ttu-id="cd9e4-212">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-212">[about_Split][]</span></span>

<span data-ttu-id="cd9e4-213">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="cd9e4-213">[about_Type_Operators][]</span></span>

<!-- reference links -->
[about_arithmetic_operators]: about_Arithmetic_Operators.md
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_assignment_operators]: about_Assignment_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_join]: about_Join.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
