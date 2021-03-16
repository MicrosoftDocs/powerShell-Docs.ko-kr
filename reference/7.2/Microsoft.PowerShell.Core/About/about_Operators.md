---
description: PowerShell에서 지 원하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: c3884c7fc6c45e52ac9bccbe6c016908c242b8ef
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99601242"
---
# <a name="about-operators"></a><span data-ttu-id="aa1f8-103">연산자 정보</span><span class="sxs-lookup"><span data-stu-id="aa1f8-103">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="aa1f8-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="aa1f8-104">Short description</span></span>
<span data-ttu-id="aa1f8-105">PowerShell에서 지 원하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-105">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="aa1f8-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-106">Long description</span></span>

<span data-ttu-id="aa1f8-107">연산자는 명령 또는 식에서 사용할 수 있는 언어 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-107">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="aa1f8-108">PowerShell은 값을 조작 하는 데 도움이 되는 여러 유형의 연산자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-108">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="aa1f8-109">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-109">Arithmetic Operators</span></span>

<span data-ttu-id="aa1f8-110">산술 연산자 ( `+` ,, `-` `*` , `/` , `%` )를 사용 하 여 명령 또는 식의 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-110">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="aa1f8-111">이러한 연산자를 사용 하 여 값을 추가, 빼기, 곱하기 또는 나눈 다음 나누기 연산의 나머지 (모듈러스)를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-111">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="aa1f8-112">더하기 연산자는 요소를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-112">The addition operator concatenates elements.</span></span> <span data-ttu-id="aa1f8-113">곱하기 연산자는 각 요소에 대해 지정 된 수의 복사본을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-113">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="aa1f8-114">,,,, 등을 구현 하는 .net 형식에 산술 연산자를 사용할 수 있습니다 `Int` `String` `DateTime` `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-114">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="aa1f8-115">비트 연산자 ( `-band` , `-bor` , `-bxor` , `-bnot` , `-shl` , `-shr` )는 값의 비트 패턴을 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-115">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="aa1f8-116">자세한 내용은 [about_Arithmetic_Operators](about_Arithmetic_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-116">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="aa1f8-117">할당 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-117">Assignment Operators</span></span>

<span data-ttu-id="aa1f8-118">할당 연산자 ( `=` ,, `+=` , `-=` , `*=` `/=` , `%=` )를 사용 하 여 변수에 값을 할당, 변경 또는 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-118">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="aa1f8-119">산술 연산자를 할당과 결합 하 여 산술 연산 결과를 변수에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-119">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="aa1f8-120">자세한 내용은 [about_Assignment_Operators](about_Assignment_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-120">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="aa1f8-121">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-121">Comparison Operators</span></span>

<span data-ttu-id="aa1f8-122">비교 연산자 ( `-eq` ,, `-ne` , `-gt` , `-lt` `-le` , `-ge` )를 사용 하 여 값 및 테스트 조건을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-122">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="aa1f8-123">예를 들어 두 문자열 값을 비교 하 여 같은지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-123">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="aa1f8-124">비교 연산자에는 텍스트의 패턴을 찾거나 바꾸는 연산자도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-124">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="aa1f8-125">(, `-match` `-notmatch` , `-replace` ) 연산자는 정규식을 사용 하 고 ( `-like` , `-notlike` )는 와일드 카드를 사용 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-125">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="aa1f8-126">포함 비교 연산자는 테스트 값이 참조 집합 ( `-in` ,,,)에 표시 되는지 여부를 결정 `-notin` `-contains` `-notcontains` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-126">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="aa1f8-127">형식 비교 연산자 ( `-is` , `-isnot` )는 개체가 지정 된 형식 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-127">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="aa1f8-128">자세한 내용은 [about_Comparison_Operators](about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-128">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="aa1f8-129">논리 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-129">Logical Operators</span></span>

<span data-ttu-id="aa1f8-130">논리 연산자 ( `-and` , `-or` , `-xor` , `-not` , `!` )를 사용 하 여 조건부 문을 단일 복합 조건에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-130">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="aa1f8-131">예를 들어 논리 연산자를 사용 `-and` 하 여 두 가지 조건이 있는 개체 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-131">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="aa1f8-132">자세한 내용은 [about_Logical_Operators](about_logical_operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-132">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="aa1f8-133">리디렉션 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-133">Redirection Operators</span></span>

<span data-ttu-id="aa1f8-134">리디렉션 연산자 ( `>` ,, `>>` `2>` , `2>>` 및 `2>&1` )를 사용 하 여 명령 또는 식의 출력을 텍스트 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-134">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="aa1f8-135">리디렉션 연산자는 `Out-File` 매개 변수 없이 cmdlet 처럼 작동 하지만, 오류 출력을 지정 된 파일로 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-135">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="aa1f8-136">Cmdlet을 사용 하 여 `Tee-Object` 출력을 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-136">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="aa1f8-137">자세한 내용은 [about_Redirection](about_Redirection.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-137">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="aa1f8-138">분할 및 조인 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-138">Split and Join Operators</span></span>

<span data-ttu-id="aa1f8-139">`-split`및 `-join` 연산자는 부분 문자열을 나누고 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-139">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="aa1f8-140">`-split`연산자는 문자열을 부분 문자열로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-140">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="aa1f8-141">`-join`연산자는 여러 문자열을 단일 문자열로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-141">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="aa1f8-142">자세한 내용은 [about_Split](about_Split.md) 및 [about_Join](about_Join.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-142">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="aa1f8-143">형식 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-143">Type Operators</span></span>

<span data-ttu-id="aa1f8-144">형식 연산자 ( `-is` , `-isnot` , `-as` )를 사용 하 여 개체의 .NET Framework 유형을 찾거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-144">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="aa1f8-145">자세한 내용은 [about_Type_Operators](about_Type_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-145">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="aa1f8-146">단항 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-146">Unary Operators</span></span>

<span data-ttu-id="aa1f8-147">단항 연산자를 사용 하 여 변수 또는 개체 속성을 증가 또는 감소 시키고 정수를 양수 또는 음수로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-147">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="aa1f8-148">예를 들어 변수를에서로 증가 시키려면를 `$a` `9` `10` 입력 `$a++` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-148">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="aa1f8-149">특수 연산자</span><span class="sxs-lookup"><span data-stu-id="aa1f8-149">Special Operators</span></span>

<span data-ttu-id="aa1f8-150">특수 연산자에는 다른 운영자 그룹에 맞지 않는 특정 사용 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-150">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="aa1f8-151">예를 들어 특수 연산자를 사용 하 여 명령을 실행 하거나, 값의 데이터 형식을 변경 하거나, 배열에서 요소를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-151">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="aa1f8-152">그룹화 연산자 `( )`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-152">Grouping operator `( )`</span></span>

<span data-ttu-id="aa1f8-153">다른 언어와 마찬가지로에서는 `(...)` 식의 연산자 우선 순위를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-153">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="aa1f8-154">예: `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-154">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="aa1f8-155">그러나 PowerShell에는 추가 동작이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-155">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="aa1f8-156">`(...)`_명령의_ 출력이 식에 참여할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-156">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="aa1f8-157">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="aa1f8-157">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="aa1f8-158">파이프라인의 첫 번째 세그먼트로 사용 되는 경우 괄호를 사용 하 여 명령 또는 식을 항상 식 결과를 _열거_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-158">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="aa1f8-159">괄호가 _명령을_ 래핑하는 경우 파이프라인을 통해 결과가 전송 되기 전에 _메모리에 수집_ 된 모든 출력을 사용 하 여 완료 될 때까지 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-159">If the parentheses wrap a _command_, it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="aa1f8-160">하위 식 연산자 `$( )`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-160">Subexpression operator `$( )`</span></span>

<span data-ttu-id="aa1f8-161">하나 이상의 문 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-161">Returns the result of one or more statements.</span></span> <span data-ttu-id="aa1f8-162">단일 결과의 경우 스칼라를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-162">For a single result, returns a scalar.</span></span> <span data-ttu-id="aa1f8-163">여러 결과에 대해는 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-163">For multiple results, returns an array.</span></span> <span data-ttu-id="aa1f8-164">다른 식 내에서 식을 사용 하려는 경우이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-164">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="aa1f8-165">예를 들어 명령 결과를 문자열 식에 포함 하려면</span><span class="sxs-lookup"><span data-stu-id="aa1f8-165">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="aa1f8-166">Array 하위 식 연산자 `@( )`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-166">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="aa1f8-167">하나 이상의 문 결과를 배열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-167">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="aa1f8-168">항목이 하나만 있는 경우 배열에는 하나의 멤버만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-168">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a><span data-ttu-id="aa1f8-169">해시 테이블 리터럴 구문 `@{}`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-169">Hash table literal syntax `@{}`</span></span>

<span data-ttu-id="aa1f8-170">배열 하위 식과 마찬가지로이 구문은 해시 테이블을 선언 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-170">Similar to the array subexpression, this syntax is used to declare a hash table.</span></span>
<span data-ttu-id="aa1f8-171">자세한 내용은 [about_Hash_Tables](about_Hash_Tables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-171">For more information, see [about_Hash_Tables](about_Hash_Tables.md).</span></span>

#### <a name="call-operator-"></a><span data-ttu-id="aa1f8-172">Call 연산자 `&`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-172">Call operator `&`</span></span>

<span data-ttu-id="aa1f8-173">명령, 스크립트 또는 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-173">Runs a command, script, or script block.</span></span> <span data-ttu-id="aa1f8-174">"호출 연산자" 라고도 하는 call 연산자를 사용 하면 변수에 저장 되 고 문자열 또는 스크립트 블록으로 표시 되는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-174">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="aa1f8-175">호출 연산자는 자식 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-175">The call operator executes in a child scope.</span></span> <span data-ttu-id="aa1f8-176">범위에 대 한 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-176">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="aa1f8-177">이 예제에서는 명령을 문자열에 저장 하 고 call 연산자를 사용 하 여 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-177">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="aa1f8-178">호출 연산자는 문자열을 구문 분석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-178">The call operator does not parse strings.</span></span> <span data-ttu-id="aa1f8-179">즉, call 연산자를 사용 하는 경우 문자열 내에서 명령 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-179">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
```

<span data-ttu-id="aa1f8-180">호출 연산자를 사용할 때 구문 분석 오류가 발생 하는 코드를 [호출](xref:Microsoft.PowerShell.Utility.Invoke-Expression) 하는 코드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-180">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

<span data-ttu-id="aa1f8-181">Call 연산자를 사용 하 여 파일 이름을 사용 하 여 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-181">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="aa1f8-182">아래 예제에서는 공백이 포함 된 스크립트 파일 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-182">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="aa1f8-183">스크립트를 실행 하려고 하면 PowerShell은 대신 파일 이름을 포함 하는 따옴표 붙은 문자열의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-183">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="aa1f8-184">Call 연산자를 사용 하 여 파일 이름을 포함 하는 문자열의 내용을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-184">The call operator allows you to execute the contents of the string containing the filename.</span></span>

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

<span data-ttu-id="aa1f8-185">스크립트 블록에 대 한 자세한 내용은 [about_Script_Blocks](about_Script_Blocks.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-185">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="aa1f8-186">Background 연산자 `&`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-186">Background operator `&`</span></span>

<span data-ttu-id="aa1f8-187">PowerShell 작업에서 백그라운드 이전에 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-187">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="aa1f8-188">이 연산자는 `&` subshell에서 작업으로 비동기적으로 명령을 실행 하는 UNIX 제어 연산자 앰퍼샌드 ()와 유사 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-188">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="aa1f8-189">이 연산자는와 기능적으로 동일 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-189">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="aa1f8-190">기본적으로 background 연산자는 병렬 작업을 시작 하는 호출자의 현재 작업 디렉터리에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-190">By default, the background operator starts the jobs in the current working directory of the caller that started the parallel tasks.</span></span> <span data-ttu-id="aa1f8-191">다음 예에서는 백그라운드 작업 연산자의 기본 사용법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-191">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="aa1f8-192">이 명령은 다음과 같은 기능을 사용 하는 것과 기능적으로 동일 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-192">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="aa1f8-193">마찬가지로 `Start-Job` `&` background 연산자는 개체를 반환 합니다 `Job` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-193">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="aa1f8-194">이 개체는 `Receive-Job` `Remove-Job` 작업을 시작 하는 데 사용한 것 처럼 및와 함께 사용할 수 있습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-194">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

<span data-ttu-id="aa1f8-195">`&`또한 background 연산자는 UNIX 제어 연산자 앰퍼샌드 ()와 마찬가지로 문 종결자입니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-195">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="aa1f8-196">이렇게 하면 백그라운드 연산자 다음에 추가 명령을 호출할 수 있습니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-196">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="aa1f8-197">다음 예에서는 백그라운드 연산자 다음에 추가 명령을 호출 하는 방법을 보여 줍니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-197">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

<span data-ttu-id="aa1f8-198">다음 스크립트와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-198">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="aa1f8-199">각각의 백그라운드 프로세스에서 각 명령을 한 줄에 실행 하려는 경우 각 명령의 앞뒤에 있는 명령을 입력 `&` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-199">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="aa1f8-200">PowerShell 작업에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-200">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="aa1f8-201">캐스트 연산자 `[ ]`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-201">Cast operator `[ ]`</span></span>

<span data-ttu-id="aa1f8-202">개체를 지정 된 형식으로 변환 하거나 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-202">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="aa1f8-203">개체를 변환할 수 없는 경우 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-203">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="aa1f8-204">캐스트 [표기법](about_Variables.md)을 사용 하 여 변수를 할당 하는 경우에도 캐스트를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-204">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="aa1f8-205">쉼표 연산자 `,`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-205">Comma operator `,`</span></span>

<span data-ttu-id="aa1f8-206">이항 연산자로 쉼표는 배열을 만들거나 생성 되는 배열에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-206">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="aa1f8-207">식 모드에서 단항 연산자는 쉼표를 사용 하 여 하나의 멤버만 사용 하는 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-207">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="aa1f8-208">멤버 앞에 쉼표를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-208">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="aa1f8-209">에 `Write-Object` 는 인수가 필요 하므로 식을 괄호 안에 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-209">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="aa1f8-210">점 소싱 연산자 `.`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-210">Dot sourcing operator `.`</span></span>

<span data-ttu-id="aa1f8-211">현재 범위에서 스크립트를 실행 하 여 스크립트에서 만드는 모든 함수, 별칭 및 변수가 현재 범위에 추가 되 고 기존 함수를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-211">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="aa1f8-212">스크립트에 의해 선언 된 매개 변수는 변수가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-212">Parameters declared by the script become variables.</span></span> <span data-ttu-id="aa1f8-213">값이 지정 되지 않은 매개 변수는 값이 없는 변수가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-213">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="aa1f8-214">그러나 자동 변수는 `$args` 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-214">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="aa1f8-215">점 소싱 연산자에는 공백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-215">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="aa1f8-216">공백을 사용 하 여 `.` 현재 디렉터리를 나타내는 점 () 기호와 점을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-216">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="aa1f8-217">다음 예제에서는 현재 디렉터리의 Sample.ps1 스크립트가 현재 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-217">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="aa1f8-218">Format 연산자 `-f`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-218">Format operator `-f`</span></span>

<span data-ttu-id="aa1f8-219">문자열 개체의 format 메서드를 사용 하 여 문자열의 서식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-219">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="aa1f8-220">연산자의 좌 변에 있는 형식 문자열을 입력 하 고 연산자의 오른쪽에 서식을 지정할 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-220">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="aa1f8-221">서식이 지정 된 문자열에서 중괄호 ()를 유지 해야 하는 경우 중괄호 `{}` 를 두 배로 하 여 이스케이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-221">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="aa1f8-222">자세한 내용은 [string.format](/dotnet/api/system.string.format) 메서드 및 [복합 서식 지정](/dotnet/standard/base-types/composite-formatting)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-222">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="aa1f8-223">Index 연산자 `[ ]`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-223">Index operator `[ ]`</span></span>

<span data-ttu-id="aa1f8-224">배열 및 해시 테이블과 같은 인덱싱된 컬렉션에서 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-224">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="aa1f8-225">배열 인덱스는 0부터 시작 하므로 첫 번째 개체는로 인덱싱됩니다 `[0]` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-225">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="aa1f8-226">배열의 경우에는 음수 인덱스만 사용 하 여 마지막 값을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-226">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="aa1f8-227">해시 테이블은 키 값으로 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-227">Hash tables are indexed by key value.</span></span>

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a><span data-ttu-id="aa1f8-228">파이프라인 연산자 `|`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-228">Pipeline operator `|`</span></span>

<span data-ttu-id="aa1f8-229">앞에 오는 명령의 출력 ("파이프")을 뒤에 오는 명령에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-229">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="aa1f8-230">출력에 둘 이상의 개체 ("컬렉션")가 포함 된 경우 파이프라인 연산자는 개체를 한 번에 하나씩 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-230">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a><span data-ttu-id="aa1f8-231">파이프라인 체인 연산자 `&&` 및 `||`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-231">Pipeline chain operators `&&` and `||`</span></span>

<span data-ttu-id="aa1f8-232">왼쪽 파이프라인의 성공 여부에 따라 오른쪽 파이프라인을 조건부로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-232">Conditionally execute the right-hand side pipeline based on the success of the left-hand side pipeline.</span></span>

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

<span data-ttu-id="aa1f8-233">자세한 내용은 [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-233">For more information, see [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).</span></span>

#### <a name="range-operator-"></a><span data-ttu-id="aa1f8-234">Range 연산자 `..`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-234">Range operator `..`</span></span>

<span data-ttu-id="aa1f8-235">지정 된 상한 및 하 한을 가진 정수 배열의 순차 정수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-235">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="aa1f8-236">또한 순서에 따라 범위를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-236">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="aa1f8-237">PowerShell 6부터 범위 연산자는 **정수** 뿐만 아니라 **문자와** 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-237">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="aa1f8-238">문자 범위를 만들려면 경계 문자를 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-238">To create a range of characters, enclose the boundary characters in quotes.</span></span>

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a><span data-ttu-id="aa1f8-239">멤버 액세스 연산자 `.`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-239">Member access operator `.`</span></span>

<span data-ttu-id="aa1f8-240">개체의 속성 및 메서드에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-240">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="aa1f8-241">멤버 이름은 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-241">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="aa1f8-242">정적 멤버 연산자 `::`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-242">Static member operator `::`</span></span>

<span data-ttu-id="aa1f8-243">.NET Framework 클래스의 정적 속성 및 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-243">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="aa1f8-244">개체의 정적 속성 및 메서드를 찾으려면 cmdlet의 정적 매개 변수를 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-244">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="aa1f8-245">멤버 이름은 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-245">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a><span data-ttu-id="aa1f8-246">삼항 연산자 `? <if-true> : <if-false>`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-246">Ternary operator `? <if-true> : <if-false>`</span></span>

<span data-ttu-id="aa1f8-247">단순 조건부 사례의 문에 대 한 대체 항목으로 삼항 연산자를 사용할 수 있습니다 `if-else` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-247">You can use the ternary operator as a replacement for the `if-else` statement in simple conditional cases.</span></span>

<span data-ttu-id="aa1f8-248">자세한 내용은 [about_If](about_If.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-248">For more information, see [about_If](about_If.md).</span></span>

#### <a name="null-coalescing-operator-"></a><span data-ttu-id="aa1f8-249">Null 병합 연산자 `??`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-249">Null-coalescing operator `??`</span></span>

<span data-ttu-id="aa1f8-250">Null 병합 연산자 `??`는 null이 아닌 경우 왼쪽 피연산자의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-250">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span> <span data-ttu-id="aa1f8-251">그렇지 않으면 오른쪽 피연산자를 계산하고 그 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-251">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="aa1f8-252">`??` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-252">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

<span data-ttu-id="aa1f8-253">다음 예에서는 오른쪽 피연산자를 계산 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-253">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a><span data-ttu-id="aa1f8-254">Null 병합 할당 연산자 `??=`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-254">Null-coalescing assignment operator `??=`</span></span>

<span data-ttu-id="aa1f8-255">Null 병합 할당 연산자는 왼쪽 피연산자가 `??=` null로 계산 되는 경우에만 오른쪽 피연산자의 값을 왼쪽 피연산자에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-255">The null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="aa1f8-256">`??=` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-256">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

<span data-ttu-id="aa1f8-257">다음 예에서는 오른쪽 피연산자를 계산 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-257">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a><span data-ttu-id="aa1f8-258">Null 조건부 연산자 `?.` 및 `?[]`</span><span class="sxs-lookup"><span data-stu-id="aa1f8-258">Null-conditional operators `?.` and `?[]`</span></span>

> [!NOTE]
> <span data-ttu-id="aa1f8-259">이 기능은 PowerShell 7.1의 실험적에서 일반으로 이동 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-259">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

<span data-ttu-id="aa1f8-260">Null 조건 연산자는 해당 `?.` `?[]` 피연산자가 null이 아닌 값으로 계산 되는 경우에만 해당 피연산자에 대 한 멤버 액세스, 또는 요소 액세스를 적용 합니다. 그렇지 않으면 null을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-260">A null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

<span data-ttu-id="aa1f8-261">PowerShell을 사용하면 `?`를 변수 이름에 포함할 수 있으므로 이러한 연산자를 사용하려면 변수 이름의 공식적인 사양이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-261">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="aa1f8-262">따라서 `{}`를 `${a}`와 같이 변수 이름 주위에 사용하거나 `?`이 변수 이름의 일부인 경우(`${a?}`)에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-262">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="aa1f8-263">다음 예에서는 **속성 속성** 의 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-263">In the following example, the value of **PropName** is returned.</span></span>

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

<span data-ttu-id="aa1f8-264">다음 예에서는 멤버 이름 **속성** 이름에 액세스 하려고 하지 않고 null을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-264">The following example will return null, without trying to access the member name **PropName**.</span></span>

```powershell
$a = $null
${a}?.PropName
```

<span data-ttu-id="aa1f8-265">마찬가지로 요소 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-265">Similarly, the value of the element will be returned.</span></span>

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

<span data-ttu-id="aa1f8-266">피연산자가 null 이면 요소에 액세스 되지 않고 null이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-266">And when the operand is null, the element isn't accessed and null is returned.</span></span>

```PowerShell
$a = $null
${a}?[0]
```

> [!NOTE]
> <span data-ttu-id="aa1f8-267">PowerShell을 사용하면 `?`를 변수 이름에 포함할 수 있으므로 이러한 연산자를 사용하려면 변수 이름의 공식적인 사양이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-267">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="aa1f8-268">따라서 `{}`를 `${a}`와 같이 변수 이름 주위에 사용하거나 `?`이 변수 이름의 일부인 경우(`${a?}`)에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-268">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>
>
> <span data-ttu-id="aa1f8-269">의 변수 이름 구문은 하위 `${<name>}` 식 연산자와 혼동 해서는 안 됩니다 `$()` .</span><span class="sxs-lookup"><span data-stu-id="aa1f8-269">The variable name syntax of `${<name>}` should not be confused with the `$()` subexpression operator.</span></span> <span data-ttu-id="aa1f8-270">자세한 내용은 [about_Variables](about_Variables.md#variable-names-that-include-special-characters)의 변수 이름 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1f8-270">For more information, see Variable name section of [about_Variables](about_Variables.md#variable-names-that-include-special-characters).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa1f8-271">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa1f8-271">See also</span></span>

[<span data-ttu-id="aa1f8-272">about_arithmetic_operators</span><span class="sxs-lookup"><span data-stu-id="aa1f8-272">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="aa1f8-273">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="aa1f8-273">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="aa1f8-274">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="aa1f8-274">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="aa1f8-275">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="aa1f8-275">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="aa1f8-276">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="aa1f8-276">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="aa1f8-277">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="aa1f8-277">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="aa1f8-278">about_Pipeline_Chain_Operators</span><span class="sxs-lookup"><span data-stu-id="aa1f8-278">about_Pipeline_Chain_Operators</span></span>](about_Pipeline_Chain_Operators.md)

[<span data-ttu-id="aa1f8-279">about_Split</span><span class="sxs-lookup"><span data-stu-id="aa1f8-279">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="aa1f8-280">about_join</span><span class="sxs-lookup"><span data-stu-id="aa1f8-280">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="aa1f8-281">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="aa1f8-281">about_Redirection</span></span>](about_Redirection.md)