---
description: 연산자를 사용 하 여 변수에 값을 할당 하는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_assignment_operators
ms.openlocfilehash: b9cb0f6a972ef627b7ce2621db489896992b406e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222817"
---
# <a name="about-assignment-operators"></a><span data-ttu-id="7d676-104">할당 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="7d676-104">About Assignment Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="7d676-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="7d676-105">Short description</span></span>
<span data-ttu-id="7d676-106">연산자를 사용 하 여 변수에 값을 할당 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-106">Describes how to use operators to assign values to variables.</span></span>

## <a name="long-description"></a><span data-ttu-id="7d676-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-107">Long description</span></span>

<span data-ttu-id="7d676-108">할당 연산자는 변수에 하나 이상의 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-108">Assignment operators assign one or more values to a variable.</span></span> <span data-ttu-id="7d676-109">할당 하기 전에 값에 대해 숫자 연산을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-109">They can perform numeric operations on the values before the assignment.</span></span>

<span data-ttu-id="7d676-110">PowerShell은 다음과 같은 할당 연산자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-110">PowerShell supports the following assignment operators.</span></span>

|<span data-ttu-id="7d676-111">연산자</span><span class="sxs-lookup"><span data-stu-id="7d676-111">Operator</span></span>|<span data-ttu-id="7d676-112">Description</span><span class="sxs-lookup"><span data-stu-id="7d676-112">Description</span></span>                                                  |
|--------|-------------------------------------------------------------|
|=       |<span data-ttu-id="7d676-113">변수의 값을 지정 된 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-113">Sets the value of a variable to the specified value.</span></span>         |
|+=      |<span data-ttu-id="7d676-114">변수의 값을 지정 된 값 만큼 늘립니다. 또는</span><span class="sxs-lookup"><span data-stu-id="7d676-114">Increases the value of a variable by the specified value, or</span></span> |
|        |<span data-ttu-id="7d676-115">지정 된 값을 기존 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-115">appends the specified value to the existing value.</span></span>           |
|-=      |<span data-ttu-id="7d676-116">지정 된 값에 따라 변수 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-116">Decreases the value of a variable by the specified value.</span></span>    |
|*=      |<span data-ttu-id="7d676-117">변수의 값을 지정 된 값과 곱합니다. 또는</span><span class="sxs-lookup"><span data-stu-id="7d676-117">Multiplies the value of a variable by the specified value, or</span></span>|
|        |<span data-ttu-id="7d676-118">지정 된 값을 기존 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-118">appends the specified value to the existing value.</span></span>           |
|/=      |<span data-ttu-id="7d676-119">변수의 값을 지정 된 값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-119">Divides the value of a variable by the specified value.</span></span>      |
|%=      |<span data-ttu-id="7d676-120">변수의 값을 지정 된 값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-120">Divides the value of a variable by the specified value and</span></span>   |
|        |<span data-ttu-id="7d676-121">그런 다음는 나머지 (모듈러스)를 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-121">then assigns the remainder (modulus) to the variable.</span></span>        |
|++      |<span data-ttu-id="7d676-122">변수 또는 할당 가능한 속성의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-122">Increases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="7d676-123">1의 배열 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-123">array element by 1.</span></span>                                          |
|--      |<span data-ttu-id="7d676-124">변수 또는 할당 가능한 속성의 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-124">Decreases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="7d676-125">1의 배열 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-125">array element by 1.</span></span>                                          |

## <a name="syntax"></a><span data-ttu-id="7d676-126">구문</span><span class="sxs-lookup"><span data-stu-id="7d676-126">Syntax</span></span>

<span data-ttu-id="7d676-127">할당 연산자의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-127">The syntax of the assignment operators is as follows:</span></span>

<span data-ttu-id="7d676-128">`<assignable-expression>` `<assignment-operator>` `<value>`</span><span class="sxs-lookup"><span data-stu-id="7d676-128">`<assignable-expression>` `<assignment-operator>` `<value>`</span></span>

<span data-ttu-id="7d676-129">할당 가능한 식에는 변수 및 속성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-129">Assignable expressions include variables and properties.</span></span> <span data-ttu-id="7d676-130">값은 단일 값, 값 배열 또는 명령, 식 또는 문이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-130">The value can be a single value, an array of values, or a command, expression, or statement.</span></span>

<span data-ttu-id="7d676-131">증가 및 감소 연산자는 단항 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-131">The increment and decrement operators are unary operators.</span></span> <span data-ttu-id="7d676-132">각에는 접두사 및 후 위 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-132">Each has prefix and postfix versions.</span></span>

`<assignable-expression><operator>`
`<operator><assignable-expression>`

<span data-ttu-id="7d676-133">할당 가능한 식은 숫자 여야 하며 숫자로 변환할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-133">The assignable expression must be a number or it must be convertible to a number.</span></span>

## <a name="assigning-values"></a><span data-ttu-id="7d676-134">값 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-134">Assigning values</span></span>

<span data-ttu-id="7d676-135">변수는 값을 저장 하는 메모리 공간 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-135">Variables are named memory spaces that store values.</span></span> <span data-ttu-id="7d676-136">할당 연산자를 사용 하 여 변수에 값을 저장 `=` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-136">You store the values in variables by using the assignment operator `=`.</span></span> <span data-ttu-id="7d676-137">새 값은 변수의 기존 값을 대체 하거나 기존 값에 새 값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-137">The new value can replace the existing value of the variable, or you can append a new value to the existing value.</span></span>

<span data-ttu-id="7d676-138">기본 할당 연산자는 등호 `=` `(ASCII 61)` 입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-138">The basic assignment operator is the equal sign `=` `(ASCII 61)`.</span></span> <span data-ttu-id="7d676-139">예를 들어 다음 문은 변수에 값 PowerShell을 할당 합니다 `$MyShell` .</span><span class="sxs-lookup"><span data-stu-id="7d676-139">For example, the following statement assigns the value PowerShell to the `$MyShell` variable:</span></span>

```powershell
$MyShell = "PowerShell"
```

<span data-ttu-id="7d676-140">PowerShell에서 변수에 값을 할당 하는 경우 변수가 아직 없는 경우 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-140">When you assign a value to a variable in PowerShell, the variable is created if it did not already exist.</span></span> <span data-ttu-id="7d676-141">예를 들어 다음 두 대입문 중 첫 번째 문은 변수를 만들고 `$a` 값으로 6을 할당 `$a` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-141">For example, the first of the following two assignment statements creates the `$a` variable and assigns a value of 6 to `$a`.</span></span> <span data-ttu-id="7d676-142">두 번째 대입문은 값 12를에 할당 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-142">The second assignment statement assigns a value of 12 to `$a`.</span></span> <span data-ttu-id="7d676-143">첫 번째 문은 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-143">The first statement creates a new variable.</span></span> <span data-ttu-id="7d676-144">두 번째 문은 해당 값만 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-144">The second statement changes only its value:</span></span>

```powershell
$a = 6
$a = 12
```

<span data-ttu-id="7d676-145">변환 하지 않는 한 PowerShell의 변수는 특정 데이터 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-145">Variables in PowerShell do not have a specific data type unless you cast them.</span></span>
<span data-ttu-id="7d676-146">변수에 하나의 개체만 포함 된 경우 변수는 해당 개체의 데이터 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-146">When a variable contains only one object, the variable takes the data type of that object.</span></span> <span data-ttu-id="7d676-147">변수에 개체 컬렉션이 포함 된 경우 변수는 System.object 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-147">When a variable contains a collection of objects, the variable has the System.Object data type.</span></span> <span data-ttu-id="7d676-148">따라서 모든 형식의 개체를 컬렉션에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-148">Therefore, you can assign any type of object to the collection.</span></span> <span data-ttu-id="7d676-149">다음 예제에서는 오류를 생성 하지 않고 프로세스 개체, 서비스 개체, 문자열 및 정수를 변수에 추가할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-149">The following example shows that you can add process objects, service objects, strings, and integers to a variable without generating an error:</span></span>

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

<span data-ttu-id="7d676-150">할당 연산자는 `=` 파이프라인 연산자 보다 우선 순위가 낮으므로 `|` 명령 파이프라인의 결과를 변수에 할당 하는 데는 괄호가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-150">Because the assignment operator `=` has a lower precedence than the pipeline operator `|`, parentheses are not required to assign the result of a command pipeline to a variable.</span></span> <span data-ttu-id="7d676-151">예를 들어 다음 명령은 컴퓨터의 서비스를 정렬 한 다음 정렬 된 서비스를 변수에 할당 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-151">For example, the following command sorts the services on the computer and then assigns the sorted services to the `$a` variable:</span></span>

```powershell
$a = Get-Service | Sort-Object -Property name
```

<span data-ttu-id="7d676-152">다음 예제와 같이 문에 의해 생성 된 값을 변수에 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-152">You can also assign the value created by a statement to a variable, as in the following example:</span></span>

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

<span data-ttu-id="7d676-153">이 예에서는 `$a` 의 값이 0 보다 작은 경우 변수에 0을 할당 `$b` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-153">This example assigns zero to the `$a` variable if the value of `$b` is less than zero.</span></span> <span data-ttu-id="7d676-154">`$b` `$a` 의 값 `$b` 이 0 보다 작지 않으면의 값을에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-154">It assigns the value of `$b` to `$a` if the value of `$b` is not less than zero.</span></span>

### <a name="the-assignment-operator"></a><span data-ttu-id="7d676-155">할당 연산자</span><span class="sxs-lookup"><span data-stu-id="7d676-155">The assignment operator</span></span>

<span data-ttu-id="7d676-156">대입 연산자는 `=` 변수에 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-156">The assignment operator `=` assigns values to variables.</span></span> <span data-ttu-id="7d676-157">변수에 이미 값이 있으면 대입 연산자는 `=` 경고 없이 값을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-157">If the variable already has a value, the assignment operator `=` replaces the value without warning.</span></span>

<span data-ttu-id="7d676-158">다음 문은 정수 값 6을 변수에 할당 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-158">The following statement assigns the integer value 6 to the `$a` variable:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="7d676-159">변수에 문자열 값을 할당 하려면 다음과 같이 문자열 값을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-159">To assign a string value to a variable, enclose the string value in quotation marks, as follows:</span></span>

```powershell
$a = "baseball"
```

<span data-ttu-id="7d676-160">변수에 배열 (다중 값)을 할당 하려면 다음과 같이 값을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-160">To assign an array (multiple values) to a variable, separate the values with commas, as follows:</span></span>

```powershell
$a = "apple", "orange", "lemon", "grape"
```

<span data-ttu-id="7d676-161">변수에 해시 테이블을 할당 하려면 PowerShell에서 표준 해시 테이블 표기법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-161">To assign a hash table to a variable, use the standard hash table notation in PowerShell.</span></span> <span data-ttu-id="7d676-162">`@`세미콜론으로 구분 되 고 중괄호로 묶인 키/값 쌍이 뒤에 오도록 기호를 입력 `;` `{ }` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-162">Type an at sign `@` followed by key/value pairs that are separated by semicolons `;` and enclosed in braces `{ }`.</span></span> <span data-ttu-id="7d676-163">예를 들어 변수에 해시 테이블을 할당 하려면 `$a` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-163">For example, to assign a hash table to the `$a` variable, type:</span></span>

```powershell
$a = @{one=1; two=2; three=3}
```

<span data-ttu-id="7d676-164">16 진수 값을 변수에 할당 하려면 값 앞에을 붙입니다 `0x` .</span><span class="sxs-lookup"><span data-stu-id="7d676-164">To assign hexadecimal values to a variable, precede the value with `0x`.</span></span>
<span data-ttu-id="7d676-165">PowerShell에서는 16 진수 값 (0x10)을 10 진수 값 (이 경우 16)으로 변환 하 고 해당 값을 `$a` 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-165">PowerShell converts the hexadecimal value (0x10) to a decimal value (in this case, 16) and assigns that value to the `$a` variable.</span></span> <span data-ttu-id="7d676-166">예를 들어 변수에 0x10 값을 할당 하려면 `$a` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-166">For example, to assign a value of 0x10 to the `$a` variable, type:</span></span>

```powershell
$a = 0x10
```

<span data-ttu-id="7d676-167">변수에 지 수 값을 할당 하려면 루트 번호, 문자 `e` 및 10의 배수를 나타내는 숫자를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-167">To assign an exponential value to a variable, type the root number, the letter `e`, and a number that represents a multiple of 10.</span></span> <span data-ttu-id="7d676-168">예를 들어 1000의 거듭제곱 3.1415 값을 변수에 할당 하려면 다음을 입력 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-168">For example, to assign a value of 3.1415 to the power of 1,000 to the `$a` variable, type:</span></span>

```powershell
$a = 3.1415e3
```

<span data-ttu-id="7d676-169">또한 PowerShell `KB` 에서는 킬로바이트, 메가바이트 `MB` 및 기가바이트를 `GB` 바이트로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-169">PowerShell can also convert kilobytes `KB`, megabytes `MB`, and gigabytes `GB` into bytes.</span></span> <span data-ttu-id="7d676-170">예를 들어 변수에 10kb 값을 할당 하려면 `$a` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-170">For example, to assign a value of 10 kilobytes to the `$a` variable, type:</span></span>

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a><span data-ttu-id="7d676-171">더하기 연산자 별 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-171">The assignment by addition operator</span></span>

<span data-ttu-id="7d676-172">더하기 연산자 대입 연산자는 `+=` 변수의 값을 증가 시키거나 지정 된 값을 기존 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-172">The assignment by addition operator `+=` either increments the value of a variable or appends the specified value to the existing value.</span></span> <span data-ttu-id="7d676-173">작업은 변수에 숫자 또는 문자열 형식이 있는지 여부와 변수에 단일 값 (스칼라) 또는 여러 값 (컬렉션)이 포함 되어 있는지 여부에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-173">The action depends on whether the variable has a numeric or string type and whether the variable contains a single value (a scalar) or multiple values (a collection).</span></span>

<span data-ttu-id="7d676-174">`+=`연산자는 두 개의 작업을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-174">The `+=` operator combines two operations.</span></span> <span data-ttu-id="7d676-175">먼저,을 추가 하 고 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-175">First, it adds, and then it assigns.</span></span>
<span data-ttu-id="7d676-176">따라서 다음 문은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-176">Therefore, the following statements are equivalent:</span></span>

```powershell
$a += 2
$a = ($a + 2)
```

<span data-ttu-id="7d676-177">변수에 단일 숫자 값이 포함 된 경우 연산자는 `+=` 연산자의 우변에 있는 양만큼 기존 값을 증가 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-177">When the variable contains a single numeric value, the `+=` operator increments the existing value by the amount on the right side of the operator.</span></span> <span data-ttu-id="7d676-178">그런 다음 연산자는 결과 값을 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-178">Then, the operator assigns the resulting value to the variable.</span></span> <span data-ttu-id="7d676-179">다음 예에서는 연산자를 사용 하 여 `+=` 변수 값을 늘리는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-179">The following example shows how to use the `+=` operator to increase the value of a variable:</span></span>

```powershell
$a = 4
$a += 2
$a
```

```
6
```

<span data-ttu-id="7d676-180">변수의 값이 문자열인 경우 연산자의 오른쪽에 있는 값은 다음과 같이 문자열에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-180">When the value of the variable is a string, the value on the right side of the operator is appended to the string, as follows:</span></span>

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

<span data-ttu-id="7d676-181">변수의 값이 배열인 경우 `+=` 연산자는 연산자의 오른쪽에 있는 값을 배열에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-181">When the value of the variable is an array, the `+=` operator appends the values on the right side of the operator to the array.</span></span> <span data-ttu-id="7d676-182">캐스팅을 통해 배열이 명시적으로 형식화 되지 않은 경우 다음과 같이 모든 형식의 값을 배열에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-182">Unless the array is explicitly typed by casting, you can append any type of value to the array, as follows:</span></span>

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

<span data-ttu-id="7d676-183">를 갖는</span><span class="sxs-lookup"><span data-stu-id="7d676-183">and</span></span>

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

<span data-ttu-id="7d676-184">변수 값이 해시 테이블인 경우 연산자는 `+=` 연산자의 오른쪽에 있는 값을 해시 테이블에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-184">When the value of a variable is a hash table, the `+=` operator appends the value on the right side of the operator to the hash table.</span></span> <span data-ttu-id="7d676-185">그러나 해시 테이블에 추가할 수 있는 유일한 형식은 다른 해시 테이블 이기 때문에 다른 모든 할당은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-185">However, because the only type that you can add to a hash table is another hash table, all other assignments fail.</span></span>

<span data-ttu-id="7d676-186">예를 들어 다음 명령은 변수에 해시 테이블을 할당 `$a` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-186">For example, the following command assigns a hash table to the `$a` variable.</span></span>
<span data-ttu-id="7d676-187">그런 다음 연산자를 사용 하 여 기존 해시 테이블 `+=` 에 다른 해시 테이블을 추가 하 여 기존 해시 테이블에 새 키/값 쌍을 효과적으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-187">Then, it uses the `+=` operator to append another hash table to the existing hash table, effectively adding a new key/value pair to the existing hash table.</span></span>
<span data-ttu-id="7d676-188">출력에 표시 된 것 처럼이 명령은 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-188">This command succeeds, as shown in the output:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

<span data-ttu-id="7d676-189">다음 명령은 변수의 해시 테이블에 "1" 정수를 추가 하려고 시도 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-189">The following command attempts to append an integer "1" to the hash table in the `$a` variable.</span></span> <span data-ttu-id="7d676-190">이 명령은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-190">This command fails:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a><span data-ttu-id="7d676-191">빼기 연산자로 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-191">The assignment by subtraction operator</span></span>

<span data-ttu-id="7d676-192">빼기로 할당 연산자는 `-=` 연산자의 우변에 지정 된 값으로 변수 값을 감소 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-192">The assignment by subtraction operator `-=` decrements the value of a variable by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="7d676-193">이 연산자는 문자열 변수와 함께 사용할 수 없으며 컬렉션에서 요소를 제거 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-193">This operator cannot be used with string variables, and it cannot be used to remove an element from a collection.</span></span>

<span data-ttu-id="7d676-194">`-=`연산자는 두 개의 작업을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-194">The `-=` operator combines two operations.</span></span> <span data-ttu-id="7d676-195">먼저를 빼고를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-195">First, it subtracts, and then it assigns.</span></span> <span data-ttu-id="7d676-196">따라서 다음 문은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-196">Therefore, the following statements are equivalent:</span></span>

```powershell
$a -= 2
$a = ($a - 2)
```

<span data-ttu-id="7d676-197">다음 예에서는 연산자를 사용 하 여 변수 값을 줄이는 방법을 보여 줍니다 `-=` .</span><span class="sxs-lookup"><span data-stu-id="7d676-197">The following example shows how to use of the `-=` operator to decrease the value of a variable:</span></span>

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

<span data-ttu-id="7d676-198">`-=`할당 연산자를 사용 하 여 숫자 배열의 멤버 값을 줄일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-198">You can also use the `-=` assignment operator to decrease the value of a member of a numeric array.</span></span> <span data-ttu-id="7d676-199">이렇게 하려면 변경 하려는 배열 요소의 인덱스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-199">To do this, specify the index of the array element that you want to change.</span></span> <span data-ttu-id="7d676-200">다음 예제에서는 배열의 세 번째 요소 (요소 2)의 값이 1 씩 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-200">In the following example, the value of the third element of an array (element 2) is decreased by 1:</span></span>

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

<span data-ttu-id="7d676-201">연산자를 사용 하 여 변수 값을 삭제할 수는 없습니다 `-=` .</span><span class="sxs-lookup"><span data-stu-id="7d676-201">You cannot use the `-=` operator to delete the values of a variable.</span></span> <span data-ttu-id="7d676-202">변수에 할당 된 모든 값을 삭제 하려면 [Clear 항목](xref:Microsoft.PowerShell.Management.Clear-Item) 또는 [clear-variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlet을 사용 하 여 또는 값을 `$null` 변수에 할당 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-202">To delete all the values that are assigned to a variable, use the [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) or [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlets to assign a value of `$null` or `""` to the variable.</span></span>

```powershell
$a = $null
```

<span data-ttu-id="7d676-203">배열에서 특정 값을 삭제 하려면 배열 표기법을 사용 하 여 값을 `$null` 특정 항목에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-203">To delete a particular value from an array, use array notation to assign a value of `$null` to the particular item.</span></span> <span data-ttu-id="7d676-204">예를 들어 다음 문은 배열에서 두 번째 값 (인덱스 위치 1)을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-204">For example, the following statement deletes the second value (index position 1) from an array:</span></span>

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

<span data-ttu-id="7d676-205">변수를 삭제 하려면 [제거-변수](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-205">To delete a variable, use the [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet.</span></span> <span data-ttu-id="7d676-206">이 메서드는 변수가 특정 데이터 형식으로 명시적으로 캐스팅 되 고 형식화 되지 않은 변수를 원하는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-206">This method is useful when the variable is explicitly cast to a particular data type, and you want an untyped variable.</span></span> <span data-ttu-id="7d676-207">다음 명령은 변수를 삭제 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-207">The following command deletes the `$a` variable:</span></span>

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a><span data-ttu-id="7d676-208">곱하기 연산자에의 한 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-208">The assignment by multiplication operator</span></span>

<span data-ttu-id="7d676-209">곱하기 연산자에의 한 할당은 `*=` 숫자 값을 곱하고 변수의 문자열 값에 대 한 지정 된 수의 복사본을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-209">The assignment by multiplication operator `*=` multiplies a numeric value or appends the specified number of copies of the string value of a variable.</span></span>

<span data-ttu-id="7d676-210">변수에 단일 숫자 값이 포함 된 경우 해당 값은 연산자의 우변에 있는 값을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-210">When a variable contains a single numeric value, that value is multiplied by the value on the right side of the operator.</span></span> <span data-ttu-id="7d676-211">예를 들어 다음 예제에서는 연산자를 사용 하 여 `*=` 변수 값을 곱하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-211">For example, the following example shows how to use the `*=` operator to multiply the value of a variable:</span></span>

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

<span data-ttu-id="7d676-212">이 경우 `*=` 연산자는 두 개의 작업을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-212">In this case, the `*=` operator combines two operations.</span></span> <span data-ttu-id="7d676-213">먼저를 곱한 다음 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-213">First, it multiplies, and then it assigns.</span></span> <span data-ttu-id="7d676-214">따라서 다음 문은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-214">Therefore, the following statements are equivalent:</span></span>

```powershell
$a *= 2
$a = ($a * 2)
```

<span data-ttu-id="7d676-215">변수에 문자열 값이 포함 된 경우 PowerShell은 다음과 같이 지정 된 수의 문자열을 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-215">When a variable contains a string value, PowerShell appends the specified number of strings to the value, as follows:</span></span>

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

<span data-ttu-id="7d676-216">배열의 요소를 곱하려면 인덱스를 사용 하 여 곱할 요소를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-216">To multiply an element of an array, use an index to identify the element that you want to multiply.</span></span> <span data-ttu-id="7d676-217">예를 들어 다음 명령은 배열 (인덱스 위치 0)의 첫 번째 요소를 2로 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-217">For example, the following command multiplies the first element in the array (index position 0) by 2:</span></span>

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a><span data-ttu-id="7d676-218">나누기 연산자에의 한 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-218">The assignment by division operator</span></span>

<span data-ttu-id="7d676-219">나누기 별 대입 연산자는 `/=` 숫자 값을 연산자의 우변에 지정 된 값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-219">The assignment by division operator `/=` divides a numeric value by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="7d676-220">연산자는 문자열 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-220">The operator cannot be used with string variables.</span></span>

<span data-ttu-id="7d676-221">`/=`연산자는 두 개의 작업을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-221">The `/=` operator combines two operations.</span></span> <span data-ttu-id="7d676-222">첫째,이를 나누고 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-222">First, it divides, and then it assigns.</span></span> <span data-ttu-id="7d676-223">따라서 다음 두 문은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-223">Therefore, the following two statements are equivalent:</span></span>

```powershell
$a /= 2
$a = ($a / 2)
```

<span data-ttu-id="7d676-224">예를 들어 다음 명령은 연산자를 사용 하 여 `/=` 변수 값을 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-224">For example, the following command uses the `/=` operator to divide the value of a variable:</span></span>

```powershell
$a = 8
$a /=2
$a
```

```
4
```

<span data-ttu-id="7d676-225">배열의 요소를 나누려면 인덱스를 사용 하 여 변경 하려는 요소를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-225">To divide an element of an array, use an index to identify the element that you want to change.</span></span> <span data-ttu-id="7d676-226">예를 들어 다음 명령은 배열의 두 번째 요소 (인덱스 위치 1)를 2로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-226">For example, the following command divides the second element in the array (index position 1) by 2:</span></span>

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a><span data-ttu-id="7d676-227">모듈러스 연산자에의 한 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-227">The assignment by modulus operator</span></span>

<span data-ttu-id="7d676-228">모듈러스 연산자의 대입 연산자는 `%=` 변수의 값을 연산자의 우변에 있는 값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-228">The assignment by modulus operator `%=` divides the value of a variable by the value on the right side of the operator.</span></span> <span data-ttu-id="7d676-229">그런 다음 `%=` 연산자는 나머지 (모듈러스 라고 함)를 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-229">Then, the `%=` operator assigns the remainder (known as the modulus) to the variable.</span></span> <span data-ttu-id="7d676-230">변수에 단일 숫자 값이 포함 된 경우에만이 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-230">You can use this operator only when a variable contains a single numeric value.</span></span> <span data-ttu-id="7d676-231">변수에 문자열 변수나 배열이 포함 된 경우에는이 연산자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-231">You cannot use this operator when a variable contains a string variable or an array.</span></span>

<span data-ttu-id="7d676-232">`%=`연산자는 두 개의 작업을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-232">The `%=` operator combines two operations.</span></span> <span data-ttu-id="7d676-233">먼저 나머지를 나누고 결정 한 다음 나머지를 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-233">First, it divides and determines the remainder, and then it assigns the remainder to the variable.</span></span> <span data-ttu-id="7d676-234">따라서 다음 문은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-234">Therefore, the following statements are equivalent:</span></span>

```powershell
$a %= 2
$a = ($a % 2)
```

<span data-ttu-id="7d676-235">다음 예제에서는 연산자를 사용 하 여 몫의 모듈러스를 저장 하는 방법을 보여 줍니다 `%=` .</span><span class="sxs-lookup"><span data-stu-id="7d676-235">The following example shows how to use the `%=` operator to save the modulus of a quotient:</span></span>

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a><span data-ttu-id="7d676-236">증가 및 감소 연산자</span><span class="sxs-lookup"><span data-stu-id="7d676-236">The increment and decrement operators</span></span>

<span data-ttu-id="7d676-237">증가 연산자는 `++` 변수의 값을 1 씩 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-237">The increment operator `++` increases the value of a variable by 1.</span></span> <span data-ttu-id="7d676-238">단순 문에서 increment 연산자를 사용 하면 값이 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-238">When you use the increment operator in a simple statement, no value is returned.</span></span> <span data-ttu-id="7d676-239">결과를 보려면 다음과 같이 변수 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-239">To view the result, display the value of the variable, as follows:</span></span>

```powershell
$a = 7
++$a
$a
```

```
8
```

<span data-ttu-id="7d676-240">값을 강제로 반환 하려면 다음과 같이 변수와 연산자를 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-240">To force a value to be returned, enclose the variable and the operator in parentheses, as follows:</span></span>

```powershell
$a = 7
(++$a)
```

```
8
```

<span data-ttu-id="7d676-241">증가 연산자는 변수 앞 (접두사) 이나 뒤 (후)에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-241">The increment operator can be placed before (prefix) or after (postfix) a variable.</span></span> <span data-ttu-id="7d676-242">연산자의 전위 버전은 다음과 같이 문에 값이 사용 되기 전에 변수를 증가 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-242">The prefix version of the operator increments a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

<span data-ttu-id="7d676-243">연산자의 후 위 버전은 해당 값이 문에서 사용 된 후 변수를 증가 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-243">The postfix version of the operator increments a variable after its value is used in the statement.</span></span> <span data-ttu-id="7d676-244">다음 예에서는 `$c` `$a` 값이 변경 전에에 할당 되기 때문에 및 변수의 값이 다릅니다 `$c` `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-244">In the following example, the `$c` and `$a` variables have different values because the value is assigned to `$c` before `$a` changes:</span></span>

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

<span data-ttu-id="7d676-245">감소 연산자는 `--` 변수의 값을 1만 큼 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-245">The decrement operator `--` decreases the value of a variable by 1.</span></span> <span data-ttu-id="7d676-246">증가 연산자와 마찬가지로 간단한 문에서 연산자를 사용 하는 경우 값이 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-246">As with the increment operator, no value is returned when you use the operator in a simple statement.</span></span> <span data-ttu-id="7d676-247">다음과 같이 괄호를 사용 하 여 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-247">Use parentheses to return a value, as follows:</span></span>

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

<span data-ttu-id="7d676-248">연산자의 전위 버전은 다음과 같이 문에 값이 사용 되기 전에 변수를 감소 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-248">The prefix version of the operator decrements a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

<span data-ttu-id="7d676-249">연산자의 후 위 버전은 해당 값이 문에 사용 된 후 변수를 감소 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-249">The postfix version of the operator decrements a variable after its value is used in the statement.</span></span> <span data-ttu-id="7d676-250">다음 예에서는 `$d` `$a` 값이 변경 전에에 할당 되기 때문에 및 변수의 값이 다릅니다 `$d` `$a` .</span><span class="sxs-lookup"><span data-stu-id="7d676-250">In the following example, the `$d` and `$a` variables have different values because the value is assigned to `$d` before `$a` changes:</span></span>

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a><span data-ttu-id="7d676-251">Microsoft .NET Framework 형식</span><span class="sxs-lookup"><span data-stu-id="7d676-251">Microsoft .NET Framework types</span></span>

<span data-ttu-id="7d676-252">기본적으로 변수에 값이 하나만 있는 경우 변수에 할당 된 값은 변수의 데이터 형식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-252">By default, when a variable has only one value, the value that is assigned to the variable determines the data type of the variable.</span></span> <span data-ttu-id="7d676-253">예를 들어 다음 명령은 "Integer" (system.string) 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-253">For example, the following command creates a variable that has the "Integer" (System.Int32) type:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="7d676-254">변수의 .NET Framework 형식을 찾으려면 다음과 같이 **GetType** 메서드와 해당 **FullName** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-254">To find the .NET Framework type of a variable, use the **GetType** method and its **FullName** property, as follows.</span></span> <span data-ttu-id="7d676-255">메서드 호출에 인수가 없더라도 **GetType** 메서드 이름 뒤에 괄호를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-255">Be sure to include the parentheses after the **GetType** method name, even though the method call has no arguments:</span></span>

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

<span data-ttu-id="7d676-256">문자열을 포함 하는 변수를 만들려면 변수에 문자열 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-256">To create a variable that contains a string, assign a string value to the variable.</span></span> <span data-ttu-id="7d676-257">값이 문자열 임을 나타내려면 다음과 같이 따옴표로 묶으십시오.</span><span class="sxs-lookup"><span data-stu-id="7d676-257">To indicate that the value is a string, enclose it in quotation marks, as follows:</span></span>

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

<span data-ttu-id="7d676-258">변수에 할당 된 첫 번째 값이 문자열인 경우 PowerShell은 모든 작업을 문자열 작업으로 처리 하 고 새 값을 문자열에 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-258">If the first value that is assigned to the variable is a string, PowerShell treats all operations as string operations and casts new values to strings.</span></span>
<span data-ttu-id="7d676-259">이는 다음 예제에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-259">This occurs in the following example:</span></span>

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

<span data-ttu-id="7d676-260">첫 번째 값이 정수인 경우 PowerShell은 모든 작업을 정수 연산으로 처리 하 고 새 값을 정수로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-260">If the first value is an integer, PowerShell treats all operations as integer operations and casts new values to integers.</span></span> <span data-ttu-id="7d676-261">이는 다음 예제에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-261">This occurs in the following example:</span></span>

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

<span data-ttu-id="7d676-262">변수 이름이 나 첫 번째 할당 값 앞에 있는 대괄호 안에 형식 이름을 배치 하 여 새 스칼라 변수를 .NET Framework 형식으로 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-262">You can cast a new scalar variable as any .NET Framework type by placing the type name in brackets that precede either the variable name or the first assignment value.</span></span> <span data-ttu-id="7d676-263">변수를 캐스팅할 때 변수에 저장할 수 있는 데이터 형식을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-263">When you cast a variable, you can determine the types of data that can be stored in the variable.</span></span> <span data-ttu-id="7d676-264">또한 변수를 조작할 때 변수의 동작 방식을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-264">And, you can determine how the variable behaves when you manipulate it.</span></span>

<span data-ttu-id="7d676-265">예를 들어 다음 명령은 변수를 문자열 형식으로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-265">For example, the following command casts the variable as a string type:</span></span>

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

<span data-ttu-id="7d676-266">다음 예에서는 변수를 캐스팅 하는 대신 첫 번째 값을 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-266">The following example casts the first value, instead of casting the variable:</span></span>

```powershell
$a = [string]27
```

<span data-ttu-id="7d676-267">변수를 특정 형식으로 캐스팅 하는 경우 일반적인 규칙은 값이 아니라 변수를 캐스팅 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-267">When you cast a variable to a specific type, the common convention is to cast the variable, not the value.</span></span> <span data-ttu-id="7d676-268">그러나 해당 값을 새 데이터 형식으로 변환할 수 없는 경우에는 기존 변수의 데이터 형식을 다시 캐스팅 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-268">However, you cannot recast the data type of an existing variable if its value cannot be converted to the new data type.</span></span> <span data-ttu-id="7d676-269">데이터 형식을 변경 하려면 다음과 같이 값을 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-269">To change the data type, you must replace its value, as follows:</span></span>

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

<span data-ttu-id="7d676-270">또한 변수 이름 앞에 데이터 형식을 사용 하는 경우 다른 데이터 형식을 지정 하 여 명시적으로 형식을 재정의 하지 않으면 해당 변수의 형식이 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-270">In addition, when you precede a variable name with a data type, the type of that variable is locked unless you explicitly override the type by specifying another data type.</span></span> <span data-ttu-id="7d676-271">기존 형식과 호환 되지 않는 값을 할당 하려고 하는데 형식을 명시적으로 재정의 하지 않는 경우 PowerShell에서 다음 예제와 같이 오류를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-271">If you try to assign a value that is incompatible with the existing type, and you do not explicitly override the type, PowerShell displays an error, as shown in the following example:</span></span>

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

<span data-ttu-id="7d676-272">PowerShell에서 배열의 여러 항목을 포함 하는 변수의 데이터 형식은 단일 항목을 포함 하는 변수의 데이터 형식과는 다르게 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-272">In PowerShell, the data types of variables that contain multiple items in an array are handled differently from the data types of variables that contain a single item.</span></span> <span data-ttu-id="7d676-273">데이터 형식이 배열 변수에 특별히 할당 되지 않은 경우 데이터 형식은 항상 `System.Object []` 입니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-273">Unless a data type is specifically assigned to an array variable, the data type is always `System.Object []`.</span></span> <span data-ttu-id="7d676-274">이 데이터 형식은 배열에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-274">This data type is specific to arrays.</span></span>

<span data-ttu-id="7d676-275">경우에 따라 다른 형식을 지정 하 여 기본 형식을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-275">Sometimes, you can override the default type by specifying another type.</span></span> <span data-ttu-id="7d676-276">예를 들어 다음 명령은 변수를 배열 형식으로 캐스팅 합니다 `string []` .</span><span class="sxs-lookup"><span data-stu-id="7d676-276">For example, the following command casts the variable as a `string []` array type:</span></span>

```powershell
[string []] $a = "one", "two", "three"
```

<span data-ttu-id="7d676-277">PowerShell 변수는 모든 .NET Framework 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-277">PowerShell variables can be any .NET Framework data type.</span></span> <span data-ttu-id="7d676-278">또한 현재 프로세스에서 사용할 수 있는 정규화 된 .NET Framework 데이터 형식을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-278">In addition, you can assign any fully qualified .NET Framework data type that is available in the current process.</span></span> <span data-ttu-id="7d676-279">예를 들어 다음 명령은 `System.DateTime` 데이터 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-279">For example, the following command specifies a `System.DateTime` data type:</span></span>

```powershell
[System.DateTime]$a = "5/31/2005"
```

<span data-ttu-id="7d676-280">변수에는 데이터 형식에 맞는 값이 할당 됩니다 `System.DateTime` .</span><span class="sxs-lookup"><span data-stu-id="7d676-280">The variable will be assigned a value that conforms to the `System.DateTime` data type.</span></span> <span data-ttu-id="7d676-281">변수의 값은 `$a` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-281">The value of the `$a` variable would be the following:</span></span>

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a><span data-ttu-id="7d676-282">여러 변수 할당</span><span class="sxs-lookup"><span data-stu-id="7d676-282">Assigning multiple variables</span></span>

<span data-ttu-id="7d676-283">PowerShell에서 단일 명령을 사용 하 여 여러 변수에 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-283">In PowerShell, you can assign values to multiple variables by using a single command.</span></span> <span data-ttu-id="7d676-284">할당 값의 첫 번째 요소는 첫 번째 변수에 할당 되 고 두 번째 요소는 두 번째 변수에 할당 되며 세 번째 요소는 세 번째 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-284">The first element of the assignment value is assigned to the first variable, the second element is assigned to the second variable, the third element to the third variable, and so on.</span></span> <span data-ttu-id="7d676-285">예를 들어 다음 명령은 변수에 값 1을 할당 하 고 값 2를 변수에 할당 `$a` 한 다음 `$b` 값 3을 변수에 할당 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="7d676-285">For example, the following command assigns the value 1 to the `$a` variable, the value 2 to the `$b` variable, and the value 3 to the `$c` variable:</span></span>

```powershell
$a, $b, $c = 1, 2, 3
```

<span data-ttu-id="7d676-286">할당 값에 변수 보다 많은 요소가 포함 된 경우 나머지 값은 모두 마지막 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-286">If the assignment value contains more elements than variables, all the remaining values are assigned to the last variable.</span></span> <span data-ttu-id="7d676-287">예를 들어 다음 명령은 3 개의 변수와 5 개의 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-287">For example, the following command contains three variables and five values:</span></span>

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

<span data-ttu-id="7d676-288">따라서 PowerShell은 변수에 값 1을 할당 하 `$a` 고 값 2를 `$b` 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-288">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="7d676-289">값 3, 4 및 5를 `$c` 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-289">It assigns the values 3, 4, and 5 to the `$c` variable.</span></span>
<span data-ttu-id="7d676-290">변수의 값을 `$c` 다른 세 변수에 할당 하려면 다음 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-290">To assign the values in the `$c` variable to three other variables, use the following format:</span></span>

```powershell
$d, $e, $f = $c
```

<span data-ttu-id="7d676-291">이 명령은 값 3을 변수에 할당 하 고, 값 4를 변수에 할당 하 `$d` `$e` 고, 값 5를 변수에 할당 `$f` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-291">This command assigns the value 3 to the `$d` variable, the value 4 to the `$e` variable, and the value 5 to the `$f` variable.</span></span>

<span data-ttu-id="7d676-292">할당 값에 변수 보다 더 작은 요소가 포함 된 경우 끝에 있는 나머지 모든 변수에는 값이 할당 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-292">If the assignment value contains less elements than variables, all the remaining variables at the end are not assigned any values.</span></span> <span data-ttu-id="7d676-293">예를 들어 다음 명령에는 세 개의 변수와 두 개의 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-293">For example, the following command contains three variables and two values:</span></span>

```powershell
$a, $b, $c = 1, 2
```

<span data-ttu-id="7d676-294">따라서 PowerShell은 변수에 값 1을 할당 하 `$a` 고 값 2를 `$b` 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-294">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="7d676-295">변수에 값을 할당 하지 않습니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="7d676-295">It will not assign any value to the `$c` variable.</span></span>

<span data-ttu-id="7d676-296">변수를 연결 하 여 여러 변수에 단일 값을 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-296">You can also assign a single value to multiple variables by chaining the variables.</span></span> <span data-ttu-id="7d676-297">예를 들어 다음 명령은 네 가지 변수에 모두 "3" 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-297">For example, the following command assigns a value of "three" to all four variables:</span></span>

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a><span data-ttu-id="7d676-298">변수 관련 cmdlet</span><span class="sxs-lookup"><span data-stu-id="7d676-298">Variable-related cmdlets</span></span>

<span data-ttu-id="7d676-299">할당 연산을 사용 하 여 변수 값을 설정 하는 것 외에도, [집합 변수](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-299">In addition to using an assignment operation to set a variable value, you can also use the [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet.</span></span> <span data-ttu-id="7d676-300">예를 들어 다음 명령은를 사용 하 여 `Set-Variable` 1, 2, 3의 배열을 `$a` 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d676-300">For example, the following command uses `Set-Variable` to assign an array of 1, 2, 3 to the `$a` variable.</span></span>

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a><span data-ttu-id="7d676-301">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d676-301">See also</span></span>

[<span data-ttu-id="7d676-302">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="7d676-302">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="7d676-303">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="7d676-303">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="7d676-304">about_Variables</span><span class="sxs-lookup"><span data-stu-id="7d676-304">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="7d676-305">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="7d676-305">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[<span data-ttu-id="7d676-306">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="7d676-306">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[<span data-ttu-id="7d676-307">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="7d676-307">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
