---
description: PowerShell에서 지 원하는 연산자에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: a76aab20c8fc64f78f3208c42e212a3fbccc7c48
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483148"
---
# <a name="about-operators"></a><span data-ttu-id="33ec1-104">연산자 정보</span><span class="sxs-lookup"><span data-stu-id="33ec1-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="33ec1-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="33ec1-105">Short description</span></span>
<span data-ttu-id="33ec1-106">PowerShell에서 지 원하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="33ec1-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-107">Long description</span></span>

<span data-ttu-id="33ec1-108">연산자는 명령 또는 식에서 사용할 수 있는 언어 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="33ec1-109">PowerShell은 값을 조작 하는 데 도움이 되는 여러 유형의 연산자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="33ec1-110">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-110">Arithmetic Operators</span></span>

<span data-ttu-id="33ec1-111">산술 연산자 ( `+` ,, `-` `*` , `/` , `%` )를 사용 하 여 명령 또는 식의 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="33ec1-112">이러한 연산자를 사용 하 여 값을 추가, 빼기, 곱하기 또는 나눈 다음 나누기 연산의 나머지 (모듈러스)를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="33ec1-113">더하기 연산자는 요소를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="33ec1-114">곱하기 연산자는 각 요소에 대해 지정 된 수의 복사본을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="33ec1-115">,,,, 등을 구현 하는 .net 형식에 산술 연산자를 사용할 수 있습니다 `Int` `String` `DateTime` `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="33ec1-116">비트 연산자 ( `-band` , `-bor` , `-bxor` , `-bnot` , `-shl` , `-shr` )는 값의 비트 패턴을 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="33ec1-117">자세한 내용은 [about_Arithmetic_Operators](about_Arithmetic_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="33ec1-118">할당 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-118">Assignment Operators</span></span>

<span data-ttu-id="33ec1-119">할당 연산자 ( `=` ,, `+=` , `-=` , `*=` `/=` , `%=` )를 사용 하 여 변수에 값을 할당, 변경 또는 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="33ec1-120">산술 연산자를 할당과 결합 하 여 산술 연산 결과를 변수에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="33ec1-121">자세한 내용은 [about_Assignment_Operators](about_Assignment_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="33ec1-122">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-122">Comparison Operators</span></span>

<span data-ttu-id="33ec1-123">비교 연산자 ( `-eq` ,, `-ne` , `-gt` , `-lt` `-le` , `-ge` )를 사용 하 여 값 및 테스트 조건을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="33ec1-124">예를 들어 두 문자열 값을 비교 하 여 같은지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="33ec1-125">비교 연산자에는 텍스트의 패턴을 찾거나 바꾸는 연산자도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="33ec1-126">(, `-match` `-notmatch` , `-replace` ) 연산자는 정규식을 사용 하 고 ( `-like` , `-notlike` )는 와일드 카드를 사용 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="33ec1-127">포함 비교 연산자는 테스트 값이 참조 집합 ( `-in` ,,,)에 표시 되는지 여부를 결정 `-notin` `-contains` `-notcontains` 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="33ec1-128">형식 비교 연산자 ( `-is` , `-isnot` )는 개체가 지정 된 형식 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="33ec1-129">자세한 내용은 [about_Comparison_Operators](about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="33ec1-130">논리 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-130">Logical Operators</span></span>

<span data-ttu-id="33ec1-131">논리 연산자 ( `-and` , `-or` , `-xor` , `-not` , `!` )를 사용 하 여 조건부 문을 단일 복합 조건에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="33ec1-132">예를 들어 논리 연산자를 사용 `-and` 하 여 두 가지 조건이 있는 개체 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="33ec1-133">자세한 내용은 [about_Logical_Operators](about_logical_operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="33ec1-134">리디렉션 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-134">Redirection Operators</span></span>

<span data-ttu-id="33ec1-135">리디렉션 연산자 ( `>` ,, `>>` `2>` , `2>>` 및 `2>&1` )를 사용 하 여 명령 또는 식의 출력을 텍스트 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="33ec1-136">리디렉션 연산자는 `Out-File` 매개 변수 없이 cmdlet 처럼 작동 하지만, 오류 출력을 지정 된 파일로 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="33ec1-137">Cmdlet을 사용 하 여 `Tee-Object` 출력을 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="33ec1-138">자세한 내용은 [about_Redirection](about_Redirection.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="33ec1-139">분할 및 조인 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-139">Split and Join Operators</span></span>

<span data-ttu-id="33ec1-140">`-split`및 `-join` 연산자는 부분 문자열을 나누고 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="33ec1-141">`-split`연산자는 문자열을 부분 문자열로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="33ec1-142">`-join`연산자는 여러 문자열을 단일 문자열로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="33ec1-143">자세한 내용은 [about_Split](about_Split.md) 및 [about_Join](about_Join.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="33ec1-144">형식 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-144">Type Operators</span></span>

<span data-ttu-id="33ec1-145">형식 연산자 ( `-is` , `-isnot` , `-as` )를 사용 하 여 개체의 .NET Framework 유형을 찾거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="33ec1-146">자세한 내용은 [about_Type_Operators](about_Type_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="33ec1-147">단항 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-147">Unary Operators</span></span>

<span data-ttu-id="33ec1-148">단항 연산자를 사용 하 여 변수 또는 개체 속성을 증가 또는 감소 시키고 정수를 양수 또는 음수로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="33ec1-149">예를 들어 변수를에서로 증가 시키려면를 `$a` `9` `10` 입력 `$a++` 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="33ec1-150">특수 연산자</span><span class="sxs-lookup"><span data-stu-id="33ec1-150">Special Operators</span></span>

<span data-ttu-id="33ec1-151">특수 연산자에는 다른 운영자 그룹에 맞지 않는 특정 사용 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="33ec1-152">예를 들어 특수 연산자를 사용 하 여 명령을 실행 하거나, 값의 데이터 형식을 변경 하거나, 배열에서 요소를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="33ec1-153">그룹화 연산자 `( )`</span><span class="sxs-lookup"><span data-stu-id="33ec1-153">Grouping operator `( )`</span></span>

<span data-ttu-id="33ec1-154">다른 언어와 마찬가지로에서는 `(...)` 식의 연산자 우선 순위를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="33ec1-155">`(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="33ec1-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="33ec1-156">그러나 PowerShell에는 추가 동작이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="33ec1-157">`(...)`_명령의_ 출력이 식에 참여할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="33ec1-158">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="33ec1-159">파이프라인의 첫 번째 세그먼트로 사용 되는 경우 괄호를 사용 하 여 명령 또는 식을 항상 식 결과를 _열거_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="33ec1-160">괄호가 _명령을_ 래핑하는 경우 파이프라인을 통해 결과가 전송 되기 전에 _메모리에 수집_ 된 모든 출력을 사용 하 여 완료 될 때까지 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="33ec1-161">괄호 안에 명령을 래핑하여 `$?` `$true` 포함 된 명령 자체가로 설정 된 경우에도 자동 변수가로 설정 됩니다 `$?` `$false` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-161">Wrapping a command in parentheses causes the automatic variable `$?` to be set to `$true`, even when the enclosed command itself set `$?` to `$false`.</span></span>
> <span data-ttu-id="33ec1-162">예를 들어 `(Get-Item /Nosuch); $?` 예기치 않게 **True** 가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-162">For example, `(Get-Item /Nosuch); $?` unexpectedly yields **True**.</span></span> <span data-ttu-id="33ec1-163">에 대 한 자세한 내용은 `$?` [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-163">For more information about `$?`, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="33ec1-164">하위 식 연산자 `$( )`</span><span class="sxs-lookup"><span data-stu-id="33ec1-164">Subexpression operator `$( )`</span></span>

<span data-ttu-id="33ec1-165">하나 이상의 문 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-165">Returns the result of one or more statements.</span></span> <span data-ttu-id="33ec1-166">단일 결과의 경우 스칼라를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-166">For a single result, returns a scalar.</span></span> <span data-ttu-id="33ec1-167">여러 결과에 대해는 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-167">For multiple results, returns an array.</span></span> <span data-ttu-id="33ec1-168">다른 식 내에서 식을 사용 하려는 경우이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-168">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="33ec1-169">예를 들어 명령 결과를 문자열 식에 포함 하려면</span><span class="sxs-lookup"><span data-stu-id="33ec1-169">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="33ec1-170">Array 하위 식 연산자 `@( )`</span><span class="sxs-lookup"><span data-stu-id="33ec1-170">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="33ec1-171">하나 이상의 문 결과를 배열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-171">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="33ec1-172">항목이 하나만 있는 경우 배열에는 하나의 멤버만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-172">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a><span data-ttu-id="33ec1-173">해시 테이블 리터럴 구문 `@{}`</span><span class="sxs-lookup"><span data-stu-id="33ec1-173">Hash table literal syntax `@{}`</span></span>

<span data-ttu-id="33ec1-174">배열 하위 식과 마찬가지로이 구문은 해시 테이블을 선언 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-174">Similar to the array subexpression, this syntax is used to declare a hash table.</span></span>
<span data-ttu-id="33ec1-175">자세한 내용은 [about_Hash_Tables](about_Hash_Tables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-175">For more information, see [about_Hash_Tables](about_Hash_Tables.md).</span></span>

#### <a name="call-operator-"></a><span data-ttu-id="33ec1-176">Call 연산자 `&`</span><span class="sxs-lookup"><span data-stu-id="33ec1-176">Call operator `&`</span></span>

<span data-ttu-id="33ec1-177">명령, 스크립트 또는 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-177">Runs a command, script, or script block.</span></span> <span data-ttu-id="33ec1-178">"호출 연산자" 라고도 하는 call 연산자를 사용 하면 변수에 저장 되 고 문자열 또는 스크립트 블록으로 표시 되는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-178">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="33ec1-179">호출 연산자는 자식 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-179">The call operator executes in a child scope.</span></span> <span data-ttu-id="33ec1-180">범위에 대 한 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-180">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="33ec1-181">이 예제에서는 명령을 문자열에 저장 하 고 call 연산자를 사용 하 여 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-181">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="33ec1-182">호출 연산자는 문자열을 구문 분석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-182">The call operator does not parse strings.</span></span> <span data-ttu-id="33ec1-183">즉, call 연산자를 사용 하는 경우 문자열 내에서 명령 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-183">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="33ec1-184">호출 연산자를 사용할 때 구문 분석 오류가 발생 하는 코드를 [호출](xref:Microsoft.PowerShell.Utility.Invoke-Expression) 하는 코드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-184">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

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

<span data-ttu-id="33ec1-185">Call 연산자를 사용 하 여 파일 이름을 사용 하 여 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-185">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="33ec1-186">아래 예제에서는 공백이 포함 된 스크립트 파일 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-186">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="33ec1-187">스크립트를 실행 하려고 하면 PowerShell은 대신 파일 이름을 포함 하는 따옴표 붙은 문자열의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-187">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="33ec1-188">Call 연산자를 사용 하 여 파일 이름을 포함 하는 문자열의 내용을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-188">The call operator allows you to execute the contents of the string containing the filename.</span></span>

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

<span data-ttu-id="33ec1-189">스크립트 블록에 대 한 자세한 내용은 [about_Script_Blocks](about_Script_Blocks.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-189">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="33ec1-190">Background 연산자 `&`</span><span class="sxs-lookup"><span data-stu-id="33ec1-190">Background operator `&`</span></span>

<span data-ttu-id="33ec1-191">PowerShell 작업에서 백그라운드 이전에 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-191">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="33ec1-192">이 연산자는 `&` subshell에서 작업으로 비동기적으로 명령을 실행 하는 UNIX 제어 연산자 앰퍼샌드 ()와 유사 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-192">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="33ec1-193">이 연산자는와 기능적으로 동일 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-193">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="33ec1-194">다음 예에서는 백그라운드 작업 연산자의 기본 사용법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-194">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="33ec1-195">이 명령은 다음과 같은 기능을 사용 하는 것과 기능적으로 동일 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-195">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="33ec1-196">마찬가지로 `Start-Job` `&` background 연산자는 개체를 반환 합니다 `Job` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-196">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="33ec1-197">이 개체는 `Receive-Job` `Remove-Job` 작업을 시작 하는 데 사용한 것 처럼 및와 함께 사용할 수 있습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-197">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

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

<span data-ttu-id="33ec1-198">`&`또한 background 연산자는 UNIX 제어 연산자 앰퍼샌드 ()와 마찬가지로 문 종결자입니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-198">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="33ec1-199">이렇게 하면 백그라운드 연산자 다음에 추가 명령을 호출할 수 있습니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-199">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="33ec1-200">다음 예에서는 백그라운드 연산자 다음에 추가 명령을 호출 하는 방법을 보여 줍니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-200">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

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

<span data-ttu-id="33ec1-201">다음 스크립트와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-201">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="33ec1-202">각각의 백그라운드 프로세스에서 각 명령을 한 줄에 실행 하려는 경우 각 명령의 앞뒤에 있는 명령을 입력 `&` 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-202">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="33ec1-203">PowerShell 작업에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-203">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="33ec1-204">캐스트 연산자 `[ ]`</span><span class="sxs-lookup"><span data-stu-id="33ec1-204">Cast operator `[ ]`</span></span>

<span data-ttu-id="33ec1-205">개체를 지정 된 형식으로 변환 하거나 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-205">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="33ec1-206">개체를 변환할 수 없는 경우 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-206">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="33ec1-207">캐스트 [표기법](about_Variables.md)을 사용 하 여 변수를 할당 하는 경우에도 캐스트를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-207">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="33ec1-208">쉼표 연산자 `,`</span><span class="sxs-lookup"><span data-stu-id="33ec1-208">Comma operator `,`</span></span>

<span data-ttu-id="33ec1-209">이항 연산자로 쉼표는 배열을 만들거나 생성 되는 배열에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-209">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="33ec1-210">식 모드에서 단항 연산자는 쉼표를 사용 하 여 하나의 멤버만 사용 하는 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-210">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="33ec1-211">멤버 앞에 쉼표를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-211">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="33ec1-212">에 `Write-Object` 는 인수가 필요 하므로 식을 괄호 안에 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-212">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="33ec1-213">점 소싱 연산자 `.`</span><span class="sxs-lookup"><span data-stu-id="33ec1-213">Dot sourcing operator `.`</span></span>

<span data-ttu-id="33ec1-214">현재 범위에서 스크립트를 실행 하 여 스크립트에서 만드는 모든 함수, 별칭 및 변수가 현재 범위에 추가 되 고 기존 함수를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-214">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="33ec1-215">스크립트에 의해 선언 된 매개 변수는 변수가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-215">Parameters declared by the script become variables.</span></span> <span data-ttu-id="33ec1-216">값이 지정 되지 않은 매개 변수는 값이 없는 변수가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-216">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="33ec1-217">그러나 자동 변수는 `$args` 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-217">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="33ec1-218">점 소싱 연산자에는 공백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-218">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="33ec1-219">공백을 사용 하 여 `.` 현재 디렉터리를 나타내는 점 () 기호와 점을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-219">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="33ec1-220">다음 예제에서는 현재 디렉터리의 Sample.ps1 스크립트가 현재 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-220">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="33ec1-221">Format 연산자 `-f`</span><span class="sxs-lookup"><span data-stu-id="33ec1-221">Format operator `-f`</span></span>

<span data-ttu-id="33ec1-222">문자열 개체의 format 메서드를 사용 하 여 문자열의 서식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-222">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="33ec1-223">연산자의 좌 변에 있는 형식 문자열을 입력 하 고 연산자의 오른쪽에 서식을 지정할 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-223">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="33ec1-224">서식이 지정 된 문자열에서 중괄호 ()를 유지 해야 하는 경우 중괄호 `{}` 를 두 배로 하 여 이스케이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-224">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="33ec1-225">자세한 내용은 [string.format](/dotnet/api/system.string.format) 메서드 및 [복합 서식 지정](/dotnet/standard/base-types/composite-formatting)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ec1-225">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="33ec1-226">Index 연산자 `[ ]`</span><span class="sxs-lookup"><span data-stu-id="33ec1-226">Index operator `[ ]`</span></span>

<span data-ttu-id="33ec1-227">배열 및 해시 테이블과 같은 인덱싱된 컬렉션에서 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-227">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="33ec1-228">배열 인덱스는 0부터 시작 하므로 첫 번째 개체는로 인덱싱됩니다 `[0]` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-228">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="33ec1-229">배열의 경우에는 음수 인덱스만 사용 하 여 마지막 값을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-229">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="33ec1-230">해시 테이블은 키 값으로 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-230">Hash tables are indexed by key value.</span></span>

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

#### <a name="pipeline-operator-"></a><span data-ttu-id="33ec1-231">파이프라인 연산자 `|`</span><span class="sxs-lookup"><span data-stu-id="33ec1-231">Pipeline operator `|`</span></span>

<span data-ttu-id="33ec1-232">앞에 오는 명령의 출력 ("파이프")을 뒤에 오는 명령에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-232">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="33ec1-233">출력에 둘 이상의 개체 ("컬렉션")가 포함 된 경우 파이프라인 연산자는 개체를 한 번에 하나씩 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-233">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a><span data-ttu-id="33ec1-234">Range 연산자 `..`</span><span class="sxs-lookup"><span data-stu-id="33ec1-234">Range operator `..`</span></span>

<span data-ttu-id="33ec1-235">지정 된 상한 및 하 한을 가진 정수 배열의 순차 정수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-235">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="33ec1-236">또한 순서에 따라 범위를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-236">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="33ec1-237">PowerShell 6부터 범위 연산자는 **정수** 뿐만 아니라 **문자와** 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-237">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="33ec1-238">문자 범위를 만들려면 경계 문자를 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-238">To create a range of characters, enclose the boundary characters in quotes.</span></span>

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

#### <a name="member-access-operator-"></a><span data-ttu-id="33ec1-239">멤버 액세스 연산자 `.`</span><span class="sxs-lookup"><span data-stu-id="33ec1-239">Member access operator `.`</span></span>

<span data-ttu-id="33ec1-240">개체의 속성 및 메서드에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-240">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="33ec1-241">멤버 이름은 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-241">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="33ec1-242">정적 멤버 연산자 `::`</span><span class="sxs-lookup"><span data-stu-id="33ec1-242">Static member operator `::`</span></span>

<span data-ttu-id="33ec1-243">.NET Framework 클래스의 정적 속성 및 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-243">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="33ec1-244">개체의 정적 속성 및 메서드를 찾으려면 cmdlet의 정적 매개 변수를 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="33ec1-244">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="33ec1-245">멤버 이름은 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ec1-245">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a><span data-ttu-id="33ec1-246">참조</span><span class="sxs-lookup"><span data-stu-id="33ec1-246">See also</span></span>

[<span data-ttu-id="33ec1-247">about_arithmetic_operators</span><span class="sxs-lookup"><span data-stu-id="33ec1-247">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="33ec1-248">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="33ec1-248">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="33ec1-249">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="33ec1-249">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="33ec1-250">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="33ec1-250">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="33ec1-251">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="33ec1-251">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="33ec1-252">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="33ec1-252">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="33ec1-253">about_Split</span><span class="sxs-lookup"><span data-stu-id="33ec1-253">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="33ec1-254">about_join</span><span class="sxs-lookup"><span data-stu-id="33ec1-254">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="33ec1-255">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="33ec1-255">about_Redirection</span></span>](about_Redirection.md)
