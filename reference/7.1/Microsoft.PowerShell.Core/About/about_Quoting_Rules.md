---
description: PowerShell에서 작은따옴표와 큰따옴표를 사용 하는 규칙을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 8d09171a1459a8ad03b54f2a4ef7a81c5983f6b8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222913"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="a89bf-104">따옴표 규칙 정보</span><span class="sxs-lookup"><span data-stu-id="a89bf-104">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="a89bf-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a89bf-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a89bf-106">PowerShell에서 작은따옴표와 큰따옴표를 사용 하는 규칙을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-106">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a89bf-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="a89bf-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a89bf-108">리터럴 문자열을 지정 하는 데 따옴표가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-108">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="a89bf-109">문자열을 작은따옴표 ( `'` ) 또는 큰따옴표 ()로 묶을 수 있습니다 `"` .</span><span class="sxs-lookup"><span data-stu-id="a89bf-109">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="a89bf-110">또한 따옴표를 사용 하 여 문자열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-110">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="a89bf-111">여기에 표시 되는 문자열은 따옴표를 문자 그대로 해석 하는 작은따옴표 또는 큰따옴표로 묶인 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-111">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="a89bf-112">여기에 있는 문자열은 여러 줄에 걸쳐 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-112">A here-string can span multiple lines.</span></span> <span data-ttu-id="a89bf-113">여기에 표시 된 문자열의 모든 줄은 따옴표로 묶여 있지 않더라도 문자열로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-113">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="a89bf-114">원격 컴퓨터에 대 한 명령에서 인용 부호는 원격 컴퓨터에서 실행 되는 명령의 일부를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-114">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="a89bf-115">원격 세션에서 따옴표는 명령의 변수가 로컬 컴퓨터 또는 원격 컴퓨터에서 먼저 해석 되는지 여부도 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-115">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="a89bf-116">작은따옴표 및 이중 따옴표 문자열</span><span class="sxs-lookup"><span data-stu-id="a89bf-116">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="a89bf-117">큰따옴표 (큰따옴표 문자열)로 문자열을 묶을 때 달러 기호 () 뒤에 오는 변수 이름은 `$` 문자열을 처리 하기 위해 명령에 전달 되기 전에 변수의 값으로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-117">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="a89bf-118">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="a89bf-119">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="a89bf-120">또한 이중 따옴표 붙은 문자열에서 식이 계산 되 고 결과가 문자열에 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="a89bf-121">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="a89bf-122">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="a89bf-123">작은따옴표 (작은따옴표로 묶은 문자열)로 문자열을 묶을 때 문자열은 입력 한 대로 정확 하 게 명령에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-123">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="a89bf-124">대체가 수행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-124">No substitution is performed.</span></span> <span data-ttu-id="a89bf-125">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-125">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="a89bf-126">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-126">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="a89bf-127">마찬가지로, 작은따옴표로 묶은 문자열의 식은 계산 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-127">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="a89bf-128">리터럴으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-128">They are interpreted as literals.</span></span> <span data-ttu-id="a89bf-129">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-129">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="a89bf-130">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-130">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="a89bf-131">큰따옴표로 묶은 문자열에서 변수 값을 대체 하지 않도록 하려면 PowerShell 이스케이프 문자인 억음 문자 ( `` ` `` ) (ASCII 96)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-131">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="a89bf-132">다음 예제에서 첫 번째 $i 변수 앞에 오는 억음 문자는 PowerShell에서 변수 이름을 해당 값으로 바꾸지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-132">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="a89bf-133">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-133">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="a89bf-134">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-134">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="a89bf-135">문자열에 큰따옴표가 표시 되도록 하려면 전체 문자열을 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-135">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="a89bf-136">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-136">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="a89bf-137">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-137">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="a89bf-138">작은따옴표로 묶은 문자열을 큰따옴표로 묶을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-138">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="a89bf-139">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-139">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="a89bf-140">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-140">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="a89bf-141">또는 큰따옴표를 큰따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-141">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="a89bf-142">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-142">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="a89bf-143">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-143">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="a89bf-144">작은따옴표로 묶은 단일 문자열에 작은따옴표를 포함 하려면 두 번째 연속 작은따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-144">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="a89bf-145">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-145">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="a89bf-146">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-146">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="a89bf-147">PowerShell에서 큰따옴표를 문자 그대로 해석 하도록 하려면 억음 문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-147">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="a89bf-148">이렇게 하면 PowerShell에서 따옴표를 문자열 구분 기호로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-148">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="a89bf-149">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-149">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="a89bf-150">작은따옴표로 묶인 단일 문자열의 내용이 리터럴로 해석 되기 때문에 억음 문자는 리터럴 문자로 취급 되 고 출력에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-150">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="a89bf-151">다음 문자열</span><span class="sxs-lookup"><span data-stu-id="a89bf-151">HERE-STRINGS</span></span>

<span data-ttu-id="a89bf-152">여기서는 문자열에 대 한 따옴표 규칙이 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-152">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="a89bf-153">여기에 표시 되는 문자열은 따옴표를 문자 그대로 해석 하는 작은따옴표 또는 큰따옴표로 묶인 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-153">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="a89bf-154">여기에 있는 문자열은 여러 줄에 걸쳐 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-154">A here-string can span multiple lines.</span></span> <span data-ttu-id="a89bf-155">여기에 표시 된 문자열의 모든 줄은 따옴표로 묶여 있지 않더라도 문자열로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-155">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="a89bf-156">일반 문자열과 마찬가지로 변수는 큰따옴표로 묶은 문자열의 값으로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-156">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="a89bf-157">여기에 있는 작은따옴표로 묶은 문자열에서는 변수가 해당 값으로 대체 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-157">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="a89bf-158">텍스트에는 여기에 문자열을 사용할 수 있지만 특히 다음과 같은 종류의 텍스트에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-158">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="a89bf-159">리터럴 따옴표를 포함 하는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-159">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="a89bf-160">HTML 또는 XML의 텍스트와 같은 여러 줄의 텍스트</span><span class="sxs-lookup"><span data-stu-id="a89bf-160">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="a89bf-161">스크립트 또는 함수 문서에 대 한 도움말 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-161">The Help text for a script or function document</span></span>

<span data-ttu-id="a89bf-162">여기서 문자열은 다음 형식 중 하나를 사용할 수 있습니다. 여기서는 `<Enter>` <kbd>enter</kbd> 키를 누를 때 추가 되는 줄 바꿈 또는 줄 바꿈 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-162">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="a89bf-163">큰따옴표:</span><span class="sxs-lookup"><span data-stu-id="a89bf-163">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="a89bf-164">작은따옴표:</span><span class="sxs-lookup"><span data-stu-id="a89bf-164">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="a89bf-165">두 형식에서 닫는 따옴표는 줄의 첫 번째 문자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-165">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="a89bf-166">여기에 표시 되는 문자열은 두 숨겨진 문자 사이의 모든 텍스트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-166">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="a89bf-167">여기 문자열에서 모든 따옴표는 문자 그대로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-167">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="a89bf-168">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-168">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="a89bf-169">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-169">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="a89bf-170">다음 문자열을 사용 하면 명령에서 문자열을 사용 하 여 단순화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-170">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="a89bf-171">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-171">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="a89bf-172">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-172">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="a89bf-173">여기에 있는 작은따옴표로 묶은 문자열에서 변수는 문자 그대로 해석 되어 정확히 재현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-173">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="a89bf-174">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-174">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="a89bf-175">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-175">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="a89bf-176">여기에 큰따옴표로 묶은 문자열에서는 변수가 해당 값으로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-176">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="a89bf-177">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a89bf-177">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="a89bf-178">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-178">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="a89bf-179">여기에서 문자열은 일반적으로 변수에 여러 줄을 할당 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-179">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="a89bf-180">예를 들어 다음은 $page 변수에 XML 페이지를 할당 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-180">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

<span data-ttu-id="a89bf-181">여기에서 문자열은 cmdlet에 대 한 입력에 사용할 수 있는 편리한 형식이 며 `ConvertFrom-StringData` , 여기서 문자열을 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a89bf-181">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="a89bf-182">자세한 내용은 `ConvertFrom-StringData`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a89bf-182">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a89bf-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a89bf-183">SEE ALSO</span></span>

[<span data-ttu-id="a89bf-184">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="a89bf-184">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="a89bf-185">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="a89bf-185">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
