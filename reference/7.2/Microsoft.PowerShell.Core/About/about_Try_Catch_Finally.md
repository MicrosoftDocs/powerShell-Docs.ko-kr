---
description: ', 및 블록을 사용 하 여 `Try` `Catch` 종료 오류를 처리 하는 방법을 설명 합니다 `Finally` .'
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599952"
---
# <a name="about-try-catch-finally"></a><span data-ttu-id="519c3-103">Try Catch Finally 정보</span><span class="sxs-lookup"><span data-stu-id="519c3-103">About Try Catch Finally</span></span>

## <a name="short-description"></a><span data-ttu-id="519c3-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="519c3-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="519c3-105">, 및 블록을 사용 하 여 `Try` `Catch` 종료 오류를 처리 하는 방법을 설명 합니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="519c3-105">Describes how to use the `Try`, `Catch`, and `Finally` blocks to handle terminating errors.</span></span>

## <a name="long-description"></a><span data-ttu-id="519c3-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="519c3-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="519c3-107">`Try`, `Catch` 및 블록을 사용 하 여 스크립트에 `Finally` 응답 하거나 스크립트의 종료 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-107">Use `Try`, `Catch`, and `Finally` blocks to respond to or handle terminating errors in scripts.</span></span> <span data-ttu-id="519c3-108">`Trap`문을 사용 하 여 스크립트의 종료 오류를 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-108">The `Trap` statement can also be used to handle terminating errors in scripts.</span></span> <span data-ttu-id="519c3-109">자세한 내용은 [about_Trap](about_Trap.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="519c3-109">For more information, see [about_Trap](about_Trap.md).</span></span>

<span data-ttu-id="519c3-110">종료 오류가 발생 하면 문이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-110">A terminating error stops a statement from running.</span></span> <span data-ttu-id="519c3-111">PowerShell에서 어떤 방식으로든 종료 오류를 처리 하지 않는 경우 PowerShell은 현재 파이프라인을 사용 하 여 함수 또는 스크립트의 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-111">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script using the current pipeline.</span></span> <span data-ttu-id="519c3-112">C와 같은 다른 언어에서는 \# 종료 오류를 예외 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-112">In other languages, such as C\#, terminating errors are referred to as exceptions.</span></span>

<span data-ttu-id="519c3-113">블록을 사용 하 여 `Try` PowerShell에서 오류를 모니터링 하도록 할 스크립트의 섹션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-113">Use the `Try` block to define a section of a script in which you want PowerShell to monitor for errors.</span></span> <span data-ttu-id="519c3-114">블록 내에서 오류가 발생 하면 `Try` 먼저 자동 변수에 오류가 저장 됩니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="519c3-114">When an error occurs within the `Try` block, the error is first saved to the `$Error` automatic variable.</span></span> <span data-ttu-id="519c3-115">그러면 PowerShell에서 오류를 `Catch` 처리 하기 위해 블록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-115">PowerShell then searches for a `Catch` block to handle the error.</span></span> <span data-ttu-id="519c3-116">`Try`문에 일치 하는 블록이 없으면 PowerShell은 `Catch` `Catch` 부모 범위에서 적절 한 블록이 나 문을 계속 검색 `Trap` 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-116">If the `Try` statement does not have a matching `Catch` block, PowerShell continues to search for an appropriate `Catch` block or `Trap` statement in the parent scopes.</span></span> <span data-ttu-id="519c3-117">`Catch`블록이 완료 된 후 또는 적절 한 `Catch` 블록이 나 문이 없는 경우 `Trap` `Finally` 블록이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-117">After a `Catch` block is completed or if no appropriate `Catch` block or `Trap` statement is found, the `Finally` block is run.</span></span> <span data-ttu-id="519c3-118">오류를 처리할 수 없는 경우 오류가 오류 스트림에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-118">If the error cannot be handled, the error is written to the error stream.</span></span>

<span data-ttu-id="519c3-119">`Catch`블록은 오류를 추적 하거나 스크립트의 예상 흐름을 복구 하기 위한 명령을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-119">A `Catch` block can include commands for tracking the error or for recovering the expected flow of the script.</span></span> <span data-ttu-id="519c3-120">`Catch`블록은 catch 하는 오류 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-120">A `Catch` block can specify which error types it catches.</span></span> <span data-ttu-id="519c3-121">문에는 여러 `Try` 종류의 `Catch` 오류에 대 한 여러 블록이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-121">A `Try` statement can include multiple `Catch` blocks for different kinds of errors.</span></span>

<span data-ttu-id="519c3-122">`Finally`블록을 사용 하 여 스크립트에 더 이상 필요 하지 않은 리소스를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-122">A `Finally` block can be used to free any resources that are no longer needed by your script.</span></span>

<span data-ttu-id="519c3-123">`Try`, `Catch` 및는 `Finally` `Try` `Catch` `Finally` C 프로그래밍 언어에서 사용 되는, 및 키워드와 유사 \# 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-123">`Try`, `Catch`, and `Finally` resemble the `Try`, `Catch`, and `Finally` keywords used in the C\# programming language.</span></span>

### <a name="syntax"></a><span data-ttu-id="519c3-124">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="519c3-124">SYNTAX</span></span>

<span data-ttu-id="519c3-125">`Try`문에는 `Try` 블록, 0 개 이상의 블록 `Catch` 및 0 개 또는 1 개 블록이 포함 되어 있습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="519c3-125">A `Try` statement contains a `Try` block, zero or more `Catch` blocks, and zero or one `Finally` block.</span></span> <span data-ttu-id="519c3-126">`Try`문에는 `Catch` 블록이 나 블록이 하나 이상 있어야 합니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="519c3-126">A `Try` statement must have at least one `Catch` block or one `Finally` block.</span></span>

<span data-ttu-id="519c3-127">다음은 `Try` 블록 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-127">The following shows the `Try` block syntax:</span></span>

```powershell
try {<statement list>}
```

<span data-ttu-id="519c3-128">`Try`키워드 뒤에 중괄호의 문 목록이 옵니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-128">The `Try` keyword is followed by a statement list in braces.</span></span> <span data-ttu-id="519c3-129">문 목록의 문이 실행 되는 동안 종료 오류가 발생 하면 스크립트는 블록의 오류 개체를 `Try` 적절 한 블록으로 전달 합니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-129">If a terminating error occurs while the statements in the statement list are being run, the script passes the error object from the `Try` block to an appropriate `Catch` block.</span></span>

<span data-ttu-id="519c3-130">다음은 `Catch` 블록 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-130">The following shows the `Catch` block syntax:</span></span>

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

<span data-ttu-id="519c3-131">오류 형식은 대괄호 안에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-131">Error types appear in brackets.</span></span> <span data-ttu-id="519c3-132">가장 바깥쪽 대괄호는 요소가 선택 사항임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-132">The outermost brackets indicate the element is optional.</span></span>

<span data-ttu-id="519c3-133">`Catch`키워드 뒤에는 오류 유형 사양 및 문 목록의 선택적인 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-133">The `Catch` keyword is followed by an optional list of error type specifications and a statement list.</span></span> <span data-ttu-id="519c3-134">블록에서 종료 오류가 발생 하면 `Try` PowerShell에서 적절 한 블록을 검색 `Catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-134">If a terminating error occurs in the `Try` block, PowerShell searches for an appropriate `Catch` block.</span></span> <span data-ttu-id="519c3-135">블록의 문이 있는 경우 블록의 문이 `Catch` 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-135">If one is found, the statements in the `Catch` block are executed.</span></span>

<span data-ttu-id="519c3-136">`Catch`블록은 하나 이상의 오류 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-136">The `Catch` block can specify one or more error types.</span></span> <span data-ttu-id="519c3-137">오류 형식은 Microsoft .NET Framework 예외 이거나 .NET Framework 예외에서 파생 된 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-137">An error type is a Microsoft .NET Framework exception or an exception that is derived from a .NET Framework exception.</span></span> <span data-ttu-id="519c3-138">블록은 지정 된 `Catch` .NET Framework 예외 클래스 또는 지정 된 클래스에서 파생 되는 클래스의 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-138">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span>

<span data-ttu-id="519c3-139">블록에서 `Catch` 오류 유형을 지정 하는 경우 해당 `Catch` 블록은 해당 유형의 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-139">If a `Catch` block specifies an error type, that `Catch` block handles that type of error.</span></span> <span data-ttu-id="519c3-140">블록에 `Catch` 오류 형식이 지정 되지 않은 경우 해당 블록 `Catch` 은 블록에서 발생 한 모든 오류를 처리 `Try` 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-140">If a `Catch` block does not specify an error type, that `Catch` block handles any error encountered in the `Try` block.</span></span> <span data-ttu-id="519c3-141">`Try`문에는 `Catch` 지정 된 다른 오류 유형에 대 한 여러 블록이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-141">A `Try` statement can include multiple `Catch` blocks for the different specified error types.</span></span>

<span data-ttu-id="519c3-142">다음은 `Finally` 블록 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-142">The following shows the `Finally` block syntax:</span></span>

```powershell
finally {<statement list>}
```

<span data-ttu-id="519c3-143">키워드 뒤에는 문이 `Finally` `Try` 오류 없이 실행 되었거나 문에서 오류가 catch 된 경우에도 스크립트가 실행 될 때마다 실행 되는 문 목록이 나옵니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-143">The `Finally` keyword is followed by a statement list that runs every time the script is run, even if the `Try` statement ran without error or an error was caught in a `Catch` statement.</span></span>

<span data-ttu-id="519c3-144"><kbd>Ctrl</kbd> + <kbd>C</kbd> 키를 누르면 파이프라인이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-144">Note that pressing <kbd>CTRL</kbd>+<kbd>C</kbd> stops the pipeline.</span></span> <span data-ttu-id="519c3-145">파이프라인으로 전송 되는 개체는 출력으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-145">Objects that are sent to the pipeline will not be displayed as output.</span></span> <span data-ttu-id="519c3-146">따라서 "Finally 블록이 실행 되었습니다."와 같이 표시할 문을 포함 하 <kbd></kbd> + 는 경우 블록이 실행 된 경우에도 ctrl<kbd>C</kbd>를 누르면 표시 되지 않습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="519c3-146">Therefore, if you include a statement to be displayed, such as "Finally block has run", it will not be displayed after you press <kbd>CTRL</kbd>+<kbd>C</kbd>, even if the `Finally` block ran.</span></span>

### <a name="catching-errors"></a><span data-ttu-id="519c3-147">오류 CATCH</span><span class="sxs-lookup"><span data-stu-id="519c3-147">CATCHING ERRORS</span></span>

<span data-ttu-id="519c3-148">다음 샘플 스크립트는 블록이 포함 된 블록을 보여 줍니다 `Try` `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-148">The following sample script shows a `Try` block with a `Catch` block:</span></span>

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

<span data-ttu-id="519c3-149">`Catch`키워드는 `Try` 블록 또는 다른 블록 바로 뒤에와 야 합니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-149">The `Catch` keyword must immediately follow the `Try` block or another `Catch` block.</span></span>

<span data-ttu-id="519c3-150">PowerShell에서 cmdlet 또는 다른 항목으로 "NonsenseString"을 인식 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-150">PowerShell does not recognize "NonsenseString" as a cmdlet or other item.</span></span>
<span data-ttu-id="519c3-151">이 스크립트를 실행 하면 다음과 같은 결과가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-151">Running this script returns the following result:</span></span>

```powershell
An error occurred.
```

<span data-ttu-id="519c3-152">스크립트에서 "NonsenseString"이 발견 되 면 종료 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-152">When the script encounters "NonsenseString", it causes a terminating error.</span></span> <span data-ttu-id="519c3-153">블록 `Catch` 내부에서 문 목록을 실행 하 여 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-153">The `Catch` block handles the error by running the statement list inside the block.</span></span>

### <a name="using-multiple-catch-statements"></a><span data-ttu-id="519c3-154">여러 CATCH 문 사용</span><span class="sxs-lookup"><span data-stu-id="519c3-154">USING MULTIPLE CATCH STATEMENTS</span></span>

<span data-ttu-id="519c3-155">`Try`문에는 여러 개의 블록이 있을 수 있습니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-155">A `Try` statement can have any number of `Catch` blocks.</span></span> <span data-ttu-id="519c3-156">예를 들어 다음 스크립트는 `Try` 를 다운로드 하는 블록을 `MyDoc.doc` 포함 하며 두 개의 블록을 포함 합니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-156">For example, the following script has a `Try` block that downloads `MyDoc.doc`, and it contains two `Catch` blocks:</span></span>

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

<span data-ttu-id="519c3-157">첫 번째 `Catch` 블록은 **system WebException** 및 system.string **예외** 형식의 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-157">The first `Catch` block handles errors of the **System.Net.WebException** and **System.IO.IOException** types.</span></span> <span data-ttu-id="519c3-158">두 번째 `Catch` 블록은 오류 유형을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-158">The second `Catch` block does not specify an error type.</span></span> <span data-ttu-id="519c3-159">두 번째 `Catch` 블록은 발생 하는 다른 종료 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-159">The second `Catch` block handles any other terminating errors that occur.</span></span>

<span data-ttu-id="519c3-160">PowerShell은 상속을 통해 오류 유형을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-160">PowerShell matches error types by inheritance.</span></span> <span data-ttu-id="519c3-161">블록은 지정 된 `Catch` .NET Framework 예외 클래스 또는 지정 된 클래스에서 파생 되는 클래스의 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-161">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span> <span data-ttu-id="519c3-162">다음 예제에는 `Catch` "명령 찾을 수 없음" 오류를 catch 하는 블록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-162">The following example contains a `Catch` block that catches a "Command Not Found" error:</span></span>

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

<span data-ttu-id="519c3-163">지정 된 오류 형식 **CommandNotFoundException** 는 **System.SystemException** 형식에서 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-163">The specified error type, **CommandNotFoundException**, inherits from the **System.SystemException** type.</span></span> <span data-ttu-id="519c3-164">다음 예에서는 명령을 찾을 수 없음 오류를 catch 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-164">The following example also catches a Command Not Found error:</span></span>

```powershell
catch [System.SystemException] {"Base Exception" }
```

<span data-ttu-id="519c3-165">이 `Catch` 블록은 "명령 찾을 수 없음" 오류 및 **systemexception** 형식에서 상속 되는 기타 오류를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-165">This `Catch` block handles the "Command Not Found" error and other errors that inherit from the **SystemException** type.</span></span>

<span data-ttu-id="519c3-166">오류 클래스와 해당 파생 클래스 중 하나를 지정 하는 경우에는 `Catch` 일반 클래스의 블록 앞에 파생 클래스의 블록을 추가 `Catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-166">If you specify an error class and one of its derived classes, place the `Catch` block for the derived class before the `Catch` block for the general class.</span></span>

### <a name="using-traps-in-a-try-catch"></a><span data-ttu-id="519c3-167">Try Catch에서 트랩 사용</span><span class="sxs-lookup"><span data-stu-id="519c3-167">Using Traps in a Try Catch</span></span>

<span data-ttu-id="519c3-168">블록 내에서 정의 된가 있는 블록에서 종료 오류가 발생할 경우 `Try` `Trap` `Try` 일치 하는 `Catch` 블록이 있더라도 `Trap` 문은 제어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-168">When a terminating error occurs in a `Try` block with a `Trap` defined within the `Try` block, even if there is a matching `Catch` block, the `Trap` statement takes control.</span></span>

<span data-ttu-id="519c3-169">가 `Trap` 보다 높은 블록에 있고 `Try` 현재 범위 내에 일치 하는 블록이 없으면 `Catch` `Trap` 부모 범위에 일치 하는 블록이 있는 경우에도이 제어를 사용 합니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-169">If a `Trap` exists at a higher block than the `Try`, and there is no matching `Catch` block within the current scope, the `Trap` will take control, even if any parent scope has a matching `Catch` block.</span></span>

### <a name="accessing-exception-information"></a><span data-ttu-id="519c3-170">예외 정보 액세스</span><span class="sxs-lookup"><span data-stu-id="519c3-170">ACCESSING EXCEPTION INFORMATION</span></span>

<span data-ttu-id="519c3-171">블록 내에서 `Catch` 현재 오류는 라고도 하는를 사용 하 여 액세스할 수 있습니다 `$_` `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="519c3-171">Within a `Catch` block, the current error can be accessed using `$_`, which is also known as `$PSItem`.</span></span> <span data-ttu-id="519c3-172">개체의 형식은 **ErrorRecord** 입니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-172">The object is of type **ErrorRecord**.</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

<span data-ttu-id="519c3-173">이 스크립트를 실행 하면 다음과 같은 결과가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-173">Running this script returns the following result:</span></span>

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

<span data-ttu-id="519c3-174">**ScriptStackTrace**, **Exception** 및 **errordetails** 와 같이 액세스할 수 있는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-174">There are additional properties that can be accessed, such as **ScriptStackTrace**, **Exception**, and **ErrorDetails**.</span></span>  <span data-ttu-id="519c3-175">예를 들어 스크립트를 다음과 같이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-175">For example, if we change the script to the following:</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

<span data-ttu-id="519c3-176">결과는 다음과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-176">The result will be similar to:</span></span>

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a><span data-ttu-id="519c3-177">FINALLY를 사용 하 여 리소스 해제</span><span class="sxs-lookup"><span data-stu-id="519c3-177">FREEING RESOURCES BY USING FINALLY</span></span>

<span data-ttu-id="519c3-178">스크립트에서 사용 하는 리소스를 해제 하려면 `Finally` 및 블록 뒤에 블록을 추가 `Try` `Catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-178">To free resources used by a script, add a `Finally` block after the `Try` and `Catch` blocks.</span></span> <span data-ttu-id="519c3-179">블록 `Finally` 문은 블록에 종료 오류가 발생 하는지 여부에 관계 없이 실행 `Try` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-179">The `Finally` block statements run regardless of whether the `Try` block encounters a terminating error.</span></span> <span data-ttu-id="519c3-180">PowerShell은 `Finally` 스크립트가 종료 되기 전이나 현재 블록이 범위를 벗어나기 전에 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-180">PowerShell runs the `Finally` block before the script terminates or before the current block goes out of scope.</span></span>

<span data-ttu-id="519c3-181">`Finally` <kbd>CTRL</kbd> + <kbd>C</kbd> 를 사용 하 여 스크립트를 중지 하는 경우에도 블록이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="519c3-181">A `Finally` block runs even if you use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop the script.</span></span> <span data-ttu-id="519c3-182">블록은 `Finally` Exit 키워드가 블록 내에서 스크립트를 중지 하는 경우에도 실행 됩니다 `Catch` .</span><span class="sxs-lookup"><span data-stu-id="519c3-182">A `Finally` block also runs if an Exit keyword stops the script from within a `Catch` block.</span></span>

### <a name="see-also"></a><span data-ttu-id="519c3-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="519c3-183">SEE ALSO</span></span>

[<span data-ttu-id="519c3-184">about_Break</span><span class="sxs-lookup"><span data-stu-id="519c3-184">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="519c3-185">about_Continue</span><span class="sxs-lookup"><span data-stu-id="519c3-185">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="519c3-186">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="519c3-186">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="519c3-187">about_Throw</span><span class="sxs-lookup"><span data-stu-id="519c3-187">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="519c3-188">about_Trap</span><span class="sxs-lookup"><span data-stu-id="519c3-188">about_Trap</span></span>](about_Trap.md)
