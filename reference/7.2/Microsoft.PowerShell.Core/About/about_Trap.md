---
description: 종료 오류를 처리 하는 키워드에 대해 설명 합니다.
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 30b03235cbc2338de3786e37416d1c1ce1d660e3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599342"
---
# <a name="about-trap"></a><span data-ttu-id="9bcfa-103">트랩 정보</span><span class="sxs-lookup"><span data-stu-id="9bcfa-103">About Trap</span></span>

## <a name="short-description"></a><span data-ttu-id="9bcfa-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9bcfa-104">Short description</span></span>

<span data-ttu-id="9bcfa-105">종료 오류를 처리 하는 키워드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-105">Describes a keyword that handles a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="9bcfa-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-106">Long description</span></span>

<span data-ttu-id="9bcfa-107">종료 오류가 발생 하면 문이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-107">A terminating error stops a statement from running.</span></span> <span data-ttu-id="9bcfa-108">PowerShell에서 어떤 방식으로든 종료 오류를 처리 하지 않는 경우에도 PowerShell은 현재 파이프라인에서 함수 또는 스크립트의 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-108">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script in the current pipeline.</span></span> <span data-ttu-id="9bcfa-109">C #과 같은 다른 언어에서 종료 오류는 예외 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-109">In other languages, such as C#, terminating errors are known as exceptions.</span></span>

<span data-ttu-id="9bcfa-110">`trap`키워드는 종료 오류가 발생할 때 실행할 문의 목록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-110">The `trap` keyword specifies a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="9bcfa-111">`trap` 문은 다음과 같은 방법으로 종료 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-111">`trap` statements handle the terminating errors in the following ways:</span></span>

- <span data-ttu-id="9bcfa-112">문 블록을 처리 한 후 오류를 표시 `trap` 하 고가 포함 된 스크립트나 함수를 계속 실행 합니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-112">Display the error after processing the `trap` statement block and continuing execution of the script or function containing the `trap`.</span></span> <span data-ttu-id="9bcfa-113">이것은 기본적인 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-113">This is the default behavior.</span></span>

- <span data-ttu-id="9bcfa-114">문에서 using을 포함 하는 스크립트 또는 함수의 실행을 중단 하 고 오류를 표시 `trap` `break` `trap` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-114">Display the error and abort execution of the script or function containing the `trap` using `break` in the `trap` statement.</span></span>

- <span data-ttu-id="9bcfa-115">오류가 발생 하지만 문에서를 사용 하 여를 포함 하는 스크립트 또는 함수를 계속 실행 합니다 `trap` `continue` `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-115">Silence the error, but continue execution of the script or function containing the `trap` by using `continue` in the `trap` statement.</span></span>

<span data-ttu-id="9bcfa-116">의 문 목록에는 `trap` 여러 조건 또는 함수 호출이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-116">The statement list of the `trap` can include multiple conditions or function calls.</span></span> <span data-ttu-id="9bcfa-117">는 `trap` 로그 나 테스트 조건을 쓰거나 다른 프로그램을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-117">A `trap` can write logs, test conditions, or even run another program.</span></span>

### <a name="syntax"></a><span data-ttu-id="9bcfa-118">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bcfa-118">Syntax</span></span>

<span data-ttu-id="9bcfa-119">`trap`문에는 다음 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-119">The `trap` statement has the following syntax:</span></span>

```powershell
trap [[<error type>]] {<statement list>}
```

<span data-ttu-id="9bcfa-120">`trap`문에는 종료 오류가 발생할 때 실행할 문의 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-120">The `trap` statement includes a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="9bcfa-121">`trap`문은 `trap` 키워드, 선택적으로 형식 식으로 구성 되 고, 오류가 트랩 될 때 실행할 문 목록을 포함 하는 문 블록으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-121">A `trap` statement consists of the `trap` keyword, optionally followed by a type expression, and the statement block containing the list of statements to run when an error is trapped.</span></span> <span data-ttu-id="9bcfa-122">형식 식은에서 catch 하는 오류 유형을 구체화 합니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-122">The type expression refines the types of errors the `trap` catches.</span></span>

<span data-ttu-id="9bcfa-123">스크립트나 명령에는 여러 개의 문이 있을 수 있습니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-123">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="9bcfa-124">`trap` 문은 스크립트나 명령의 어디에 나 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-124">`trap` statements can appear anywhere in the script or command.</span></span>

### <a name="trapping-all-terminating-errors"></a><span data-ttu-id="9bcfa-125">모든 종료 오류 트래핑</span><span class="sxs-lookup"><span data-stu-id="9bcfa-125">Trapping all terminating errors</span></span>

<span data-ttu-id="9bcfa-126">스크립트나 명령에서 다른 방식으로 처리 되지 않는 종료 오류가 발생 하면 PowerShell은 `trap` 오류를 처리 하는 문을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-126">When a terminating error occurs that is not handled in another way in a script or command, PowerShell checks for a `trap` statement that handles the error.</span></span> <span data-ttu-id="9bcfa-127">`trap`문이 있는 경우 PowerShell은 문에서 스크립트나 명령을 계속 실행 `trap` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-127">If a `trap` statement is present, PowerShell continues running the script or command in the `trap` statement.</span></span>

<span data-ttu-id="9bcfa-128">다음 예는 매우 간단한 문입니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-128">The following example is a very simple `trap` statement:</span></span>

```powershell
trap {"Error found."}
```

<span data-ttu-id="9bcfa-129">이 `trap` 문은 종료 오류를 트래핑 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-129">This `trap` statement traps any terminating error.</span></span>

<span data-ttu-id="9bcfa-130">다음 예제에서 함수는 런타임 오류를 발생 시키는 의미 없는 문자열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-130">In the following example, the function includes a nonsense string that causes a runtime error.</span></span>

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="9bcfa-131">이 함수를 실행 하면 다음이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-131">Running this function returns the following:</span></span>

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="9bcfa-132">다음 예에는 `trap` 자동 변수를 사용 하 여 오류를 표시 하는 문이 포함 되어 있습니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-132">The following example includes a `trap` statement that displays the error by using the `$_` automatic variable:</span></span>

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="9bcfa-133">이 버전의 함수를 실행 하면 다음이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-133">Running this version of the function returns the following:</span></span>

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> <span data-ttu-id="9bcfa-134">`trap` 문은 지정 된 범위 내의 모든 위치에서 정의 될 수 있지만 항상 해당 범위의 모든 문에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-134">`trap` statements may be defined anywhere within a given scope, but always apply to all statements in that scope.</span></span> <span data-ttu-id="9bcfa-135">런타임에 `trap` 블록의 문은 다른 문이 실행 되기 전에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-135">At runtime, `trap` statements in a block are defined before any other statements are executed.</span></span> <span data-ttu-id="9bcfa-136">JavaScript에서이를 [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-136">In JavaScript, this is known as [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting).</span></span> <span data-ttu-id="9bcfa-137">즉, `trap` 실행이 정의 된 지점을 지난 후에도 문은 해당 블록의 모든 문에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-137">This means that `trap` statements apply to all statements in that block even if execution has not advanced past the point at which they are defined.</span></span> <span data-ttu-id="9bcfa-138">예를 들어 `trap` 스크립트의 끝에을 정의 하 고 첫 번째 문에서 오류를 throw 하는 것은 여전히 트리거됩니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-138">For example, defining a `trap` at the end of a script and throwing an error in the first statement still triggers that `trap`.</span></span>

### <a name="trapping-specific-errors"></a><span data-ttu-id="9bcfa-139">특정 오류 트래핑</span><span class="sxs-lookup"><span data-stu-id="9bcfa-139">Trapping specific errors</span></span>

<span data-ttu-id="9bcfa-140">스크립트나 명령에는 여러 개의 문이 있을 수 있습니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-140">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="9bcfa-141">`trap`특정 오류를 처리 하도록를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-141">A `trap` can be defined to handle specific errors.</span></span>

<span data-ttu-id="9bcfa-142">다음 예는 `trap` 특정 오류 **CommandNotFoundException** 을 트래핑 하는 문입니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-142">The following example is a `trap` statement that traps the specific error **CommandNotFoundException**:</span></span>

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

<span data-ttu-id="9bcfa-143">함수 또는 스크립트에서 알려진 명령과 일치 하지 않는 문자열이 발견 되 면이 `trap` 문은 "명령 오류 트랩" 문자열을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-143">When a function or script encounters a string that does not match a known command, this `trap` statement displays the "Command error trapped" string.</span></span>
<span data-ttu-id="9bcfa-144">문 목록을 실행 한 후 PowerShell은 오류 `trap` 개체를 오류 스트림에 쓴 다음 스크립트를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-144">After running the `trap` statement list, PowerShell writes the error object to the error stream and then continues the script.</span></span>

<span data-ttu-id="9bcfa-145">PowerShell은 .NET 예외 유형을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-145">PowerShell uses .NET exception types.</span></span> <span data-ttu-id="9bcfa-146">다음 예에서는 **System.object 예외** 오류 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-146">The following example specifies the **System.Exception** error type:</span></span>

```powershell
trap [System.Exception] {"An error trapped"}
```

<span data-ttu-id="9bcfa-147">**CommandNotFoundException** 오류 형식은 **system.object** 형식에서 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-147">The **CommandNotFoundException** error type inherits from the **System.Exception** type.</span></span> <span data-ttu-id="9bcfa-148">이 문은 알 수 없는 명령에 의해 생성 된 오류를 트래핑 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-148">This statement traps an error that is created by an unknown command.</span></span> <span data-ttu-id="9bcfa-149">또한 다른 오류 유형도 트래핑 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-149">It also traps other error types.</span></span>

<span data-ttu-id="9bcfa-150">스크립트에 문이 둘 이상 있을 수 있습니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-150">You can have more than one `trap` statement in a script.</span></span> <span data-ttu-id="9bcfa-151">각 오류 유형은 하나의 문으로만 트래핑할 수 있습니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-151">Each error type can be trapped by only one `trap` statement.</span></span> <span data-ttu-id="9bcfa-152">종료 오류가 발생 하면 PowerShell은 `trap` 현재 실행 범위에서 시작 하 여 가장 구체적인 일치 항목을 가진를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-152">When a terminating error occurs, PowerShell searches for the `trap` with the most specific match, starting in the current scope of execution.</span></span>

<span data-ttu-id="9bcfa-153">다음 스크립트 예제에는 오류가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-153">The following script example contains an error.</span></span> <span data-ttu-id="9bcfa-154">스크립트에는 `trap` 종료 오류를 트래핑 하는 일반 문과 `trap` **CommandNotFoundException** 형식을 지정 하는 특정 문이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-154">The script includes a general `trap` statement that traps any terminating error and a specific `trap` statement that specifies the **CommandNotFoundException** type.</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

<span data-ttu-id="9bcfa-155">이 스크립트를 실행 하면 다음과 같은 결과가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-155">Running this script produces the following result:</span></span>

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="9bcfa-156">PowerShell에서 cmdlet 또는 다른 항목으로 "nonsenseString"을 인식 하지 못하기 때문에 **CommandNotFoundException** 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-156">Because PowerShell does not recognize "nonsenseString" as a cmdlet or other item, it returns a **CommandNotFoundException** error.</span></span> <span data-ttu-id="9bcfa-157">이 종료 오류는 특정 문으로 트래핑 됩니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-157">This terminating error is trapped by the specific `trap` statement.</span></span>

<span data-ttu-id="9bcfa-158">다음 스크립트 예제에는 `trap` 다른 오류가 있는 동일한 문이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-158">The following script example contains the same `trap` statements with a different error:</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

<span data-ttu-id="9bcfa-159">이 스크립트를 실행 하면 다음과 같은 결과가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-159">Running this script produces the following result:</span></span>

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="9bcfa-160">0으로 나누려고 하면 **CommandNotFoundException** 오류가 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-160">The attempt to divide by zero does not create a **CommandNotFoundException** error.</span></span> <span data-ttu-id="9bcfa-161">대신,이 오류는 종료 오류를 트래핑 하는 다른 문에 의해 트래핑 됩니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-161">Instead, that error is trapped by the other `trap` statement, which traps any terminating error.</span></span>

### <a name="trapping-errors-and-scope"></a><span data-ttu-id="9bcfa-162">오류 및 범위 트래핑</span><span class="sxs-lookup"><span data-stu-id="9bcfa-162">Trapping errors and scope</span></span>

<span data-ttu-id="9bcfa-163">문과 동일한 범위에서 종료 오류가 발생 하는 경우 `trap` PowerShell은에서 정의한 문 목록을 실행 합니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-163">If a terminating error occurs in the same scope as the `trap` statement, PowerShell runs the list of statements defined by the `trap`.</span></span> <span data-ttu-id="9bcfa-164">오류가 발생 한 후 문에서 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-164">Execution continues at the statement after the error.</span></span> <span data-ttu-id="9bcfa-165">`trap`문이 오류와 다른 범위에 있으면 문과 동일한 범위에 있는 다음 문에서 실행이 계속 됩니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-165">If the `trap` statement is in a different scope from the error, execution continues at the next statement that is in the same scope as the `trap` statement.</span></span>

<span data-ttu-id="9bcfa-166">예를 들어 함수에서 오류가 발생 하 고 `trap` 문이 함수에 있는 경우 스크립트는 다음 문에서 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-166">For example, if an error occurs in a function, and the `trap` statement is in the function, the script continues at the next statement.</span></span> <span data-ttu-id="9bcfa-167">다음 스크립트에는 오류와 문이 포함 되어 있습니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-167">The following script contains an error and a `trap` statement:</span></span>

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

<span data-ttu-id="9bcfa-168">이 스크립트를 실행 하면 다음과 같은 결과가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-168">Running this script produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

<span data-ttu-id="9bcfa-169">`trap`함수의 문은 오류를 트래핑 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-169">The `trap` statement in the function traps the error.</span></span> <span data-ttu-id="9bcfa-170">메시지를 표시 한 후 PowerShell은 함수 실행을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-170">After displaying the message, PowerShell resumes running the function.</span></span> <span data-ttu-id="9bcfa-171">`Function1`가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-171">Note that `Function1` was completed.</span></span>

<span data-ttu-id="9bcfa-172">같은 오류 및 문이 있는 다음 예제와 비교 `trap` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-172">Compare this with the following example, which has the same error and `trap` statement.</span></span> <span data-ttu-id="9bcfa-173">이 예제에서 `trap` 문은 함수 외부에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-173">In this example, the `trap` statement occurs outside the function:</span></span>

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

<span data-ttu-id="9bcfa-174">함수를 실행 하면 `Function2` 다음과 같은 결과가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-174">Running the `Function2` function produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="9bcfa-175">이 예에서는 "function2가 완료 되었습니다." 명령이 실행 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-175">In this example, the "function2 was completed" command was not run.</span></span> <span data-ttu-id="9bcfa-176">두 예제에서 종료 오류는 함수 내에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-176">In both examples, the terminating error occurs within the function.</span></span> <span data-ttu-id="9bcfa-177">그러나이 예제에서 `trap` 문은 함수 외부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-177">In this example, however, the `trap` statement is outside the function.</span></span> <span data-ttu-id="9bcfa-178">문이 실행 된 후에는 PowerShell이 함수로 다시 이동 하지 않습니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-178">PowerShell does not go back into the function after the `trap` statement runs.</span></span>

> [!CAUTION]
> <span data-ttu-id="9bcfa-179">동일한 오류 조건에 대해 여러 개의 트랩이 정의 되 면 첫 번째로 `trap` 정의 된 어휘를 사용 합니다 (범위에서 가장 높음).</span><span class="sxs-lookup"><span data-stu-id="9bcfa-179">When multiple traps are defined for the same error condition, the first `trap` defined lexically (highest in the scope) is used.</span></span>

<span data-ttu-id="9bcfa-180">다음 예제에서는 `trap` "같습니다. 1"이 있는만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-180">In the following example, only the `trap` with "whoops 1" is run.</span></span>

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> <span data-ttu-id="9bcfa-181">Trap 문은 컴파일되는 위치로 범위가 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-181">A Trap statement is scoped to where it compiles.</span></span> <span data-ttu-id="9bcfa-182">함수 또는 점 원본 스크립트 내에 문이 있는 경우 `trap` 함수 또는 점 원본 스크립트가 종료 되 면 `trap` 내부의 모든 문이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-182">If you have a `trap` statement inside a function or dot sourced script, when the function or dot sourced script exits, all `trap` statements inside are removed.</span></span>

### <a name="using-the-break-and-continue-keywords"></a><span data-ttu-id="9bcfa-183">Break 및 continue 키워드 사용</span><span class="sxs-lookup"><span data-stu-id="9bcfa-183">Using the break and continue keywords</span></span>

<span data-ttu-id="9bcfa-184">문에 및 키워드를 사용 하 여 `break` `continue` `trap` 종료 오류 후 스크립트나 명령을 계속 실행할지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-184">You can use the `break` and `continue` keywords in a `trap` statement to determine whether a script or command continues to run after a terminating error.</span></span>

<span data-ttu-id="9bcfa-185">문 목록에 문을 포함 하는 경우 `break` `trap` PowerShell은 함수 또는 스크립트를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-185">If you include a `break` statement in a `trap` statement list, PowerShell stops the function or script.</span></span> <span data-ttu-id="9bcfa-186">다음 샘플 함수는 `break` 문에서 키워드를 사용 합니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-186">The following sample function uses the `break` keyword in a `trap` statement:</span></span>

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="9bcfa-187">문은 키워드를 포함 하기 때문에 `trap` `break` 함수는 계속 실행 되지 않으며 "함수 완료 됨" 줄은 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-187">Because the `trap` statement included the `break` keyword, the function does not continue to run, and the "Function completed" line is not run.</span></span>

<span data-ttu-id="9bcfa-188">문에 키워드를 포함 하는 경우에는 `continue` `trap` 또는 없이 오류가 발생 한 문 뒤에 PowerShell이 다시 시작 됩니다 `break` `continue` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-188">If you include a `continue` keyword in a `trap` statement, PowerShell resumes after the statement that caused the error, just as it would without `break` or `continue`.</span></span> <span data-ttu-id="9bcfa-189">그러나 키워드를 사용 하면 `continue` PowerShell에서 오류 스트림에 오류를 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-189">With the `continue` keyword, however, PowerShell does not write an error to the error stream.</span></span>

<span data-ttu-id="9bcfa-190">다음 샘플 함수는 `continue` 문에서 키워드를 사용 합니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="9bcfa-190">The following sample function uses the `continue` keyword in a `trap` statement:</span></span>

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

<span data-ttu-id="9bcfa-191">이 함수는 오류가 트래핑 된 후 다시 시작 되 고 "Function completed" 문이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-191">The function resumes after the error is trapped, and the "Function completed" statement runs.</span></span> <span data-ttu-id="9bcfa-192">오류 스트림에 오류가 기록 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-192">No error is written to the error stream.</span></span>

## <a name="notes"></a><span data-ttu-id="9bcfa-193">참고</span><span class="sxs-lookup"><span data-stu-id="9bcfa-193">Notes</span></span>

<span data-ttu-id="9bcfa-194">`trap` 문은 범위 내의 모든 종료 오류를 처리 하는 간단한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-194">`trap` statements provide a simple way to broadly ensure all terminating errors within a scope are handled.</span></span> <span data-ttu-id="9bcfa-195">보다 세부적인 오류 처리에 대해서는 `try` / `catch` 문을 사용 하 여 트랩이 정의 된 블록을 사용 `catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-195">For more finer-grained error handling, use `try`/`catch` blocks where traps are defined using `catch` statements.</span></span> <span data-ttu-id="9bcfa-196">`catch`문은 연결 된 문 내부의 코드에만 적용 `try` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-196">The `catch` statements only apply to the code inside the associated `try` statement.</span></span> <span data-ttu-id="9bcfa-197">자세한 내용은 [about_Try_Catch_Finally](about_Try_Catch_Finally.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9bcfa-197">For more information, see [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bcfa-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bcfa-198">See also</span></span>

[<span data-ttu-id="9bcfa-199">about_Break</span><span class="sxs-lookup"><span data-stu-id="9bcfa-199">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="9bcfa-200">about_Continue</span><span class="sxs-lookup"><span data-stu-id="9bcfa-200">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="9bcfa-201">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="9bcfa-201">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="9bcfa-202">about_Throw</span><span class="sxs-lookup"><span data-stu-id="9bcfa-202">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="9bcfa-203">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="9bcfa-203">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
