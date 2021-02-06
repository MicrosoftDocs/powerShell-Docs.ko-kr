---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: c95ebca6307d58668c31faf3e492617f49ddebf4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605498"
---
# <span data-ttu-id="db889-102">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="db889-102">ConvertFrom-StringData</span></span>

## <span data-ttu-id="db889-103">개요</span><span class="sxs-lookup"><span data-stu-id="db889-103">SYNOPSIS</span></span>
<span data-ttu-id="db889-104">키와 값 쌍이 하나 이상 포함된 문자열을 해시 테이블로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-104">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="db889-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db889-105">SYNTAX</span></span>

### <span data-ttu-id="db889-106">모두</span><span class="sxs-lookup"><span data-stu-id="db889-106">All</span></span>

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## <span data-ttu-id="db889-107">설명</span><span class="sxs-lookup"><span data-stu-id="db889-107">DESCRIPTION</span></span>

<span data-ttu-id="db889-108">`ConvertFrom-StringData`Cmdlet은 하나 이상의 키와 값 쌍을 포함 하는 문자열을 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-108">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="db889-109">각 키-값 쌍이 별도의 줄에 있어야 하기 때문에 문자열은 일반적으로 입력 형식으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-109">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="db889-110">기본적으로 **키** 는 등호 () 문자로 **값** 과 구분 되어야 합니다 `=` .</span><span class="sxs-lookup"><span data-stu-id="db889-110">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="db889-111">`ConvertFrom-StringData`Cmdlet은 `DATA` 스크립트 또는 함수의 섹션에서 사용할 수 있는 safe cmdlet으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-111">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="db889-112">섹션에서 사용 하는 경우 `DATA` 문자열의 내용이 데이터 섹션의 규칙을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-112">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="db889-113">자세한 내용은 [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db889-113">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="db889-114">`ConvertFrom-StringData` 에서는 기존 기계 번역 도구에서 허용 하는 이스케이프 문자 시퀀스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-114">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="db889-115">즉, cmdlet은 `\` 일반적으로 스크립트의 줄 끝에 신호를 보내는 PowerShell 억음 문자 () 대신 [Unescape 메서드](/dotnet/api/system.text.regularexpressions.regex.unescape)를 사용 하 여 문자열 데이터에서 백슬래시 ()를 이스케이프 문자로 해석할 수 있습니다 \` .</span><span class="sxs-lookup"><span data-stu-id="db889-115">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="db889-116">here-string 내에서 억음 문자는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-116">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="db889-117">다음과 같이 앞의 백슬래시로 이스케이프 하 여 결과에서 리터럴 백슬래시를 유지할 수도 있습니다 `\\` .</span><span class="sxs-lookup"><span data-stu-id="db889-117">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="db889-118">이스케이프되지 않은 백슬래시 문자(예: 일반적으로 파일 경로에 사용되는 문자)는 결과에서 잘못된 이스케이프 시퀀스로 렌더링될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-118">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

<span data-ttu-id="db889-119">PowerShell 7은 **구분 기호** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-119">PowerShell 7 adds the **Delimiter** parameter.</span></span>

## <span data-ttu-id="db889-120">예제</span><span class="sxs-lookup"><span data-stu-id="db889-120">EXAMPLES</span></span>

### <span data-ttu-id="db889-121">예제 1: 작은따옴표로 묶은 단일 문자열을 해시 테이블로 변환</span><span class="sxs-lookup"><span data-stu-id="db889-121">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="db889-122">이 예에서는 사용자 메시지의 작은따옴표로 묶은 문자열을 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-122">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="db889-123">작은따옴표로 묶인 문자열에서 값은 변수로 대체되지 않으며 식은 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-123">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="db889-124">`ConvertFrom-StringData`Cmdlet은 변수의 값을 `$Here` 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-124">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### <span data-ttu-id="db889-125">예 2: 다른 구분 기호를 사용 하 여 문자열 데이터 변환</span><span class="sxs-lookup"><span data-stu-id="db889-125">Example 2: Convert string data using a different delimiter</span></span>

<span data-ttu-id="db889-126">이 예에서는 다른 문자를 구분 기호로 사용 하는 문자열 데이터를 변환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db889-126">This example shows how to convert string data that uses a different character as a delimiter.</span></span> <span data-ttu-id="db889-127">이 예제에서 문자열 데이터는 구분 기호로 파이프 문자 ()를 사용 합니다 `|` .</span><span class="sxs-lookup"><span data-stu-id="db889-127">In this example the string data is using the pipe character (`|`) as the delimiter.</span></span>

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### <span data-ttu-id="db889-128">예제 3: 주석을 포함 하는 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="db889-128">Example 3: Convert a here-string containing a comment</span></span>

<span data-ttu-id="db889-129">이 예에서는 주석과 여러 키-값 쌍을 포함 하는 여기 문자열을 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-129">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

<span data-ttu-id="db889-130">**Stringdata** 매개 변수 값은 여기에 문자열이 포함 된 변수가 아니라 여기에 포함 된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="db889-130">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="db889-131">두 형식은 모두 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-131">Either format is valid.</span></span> <span data-ttu-id="db889-132">이 here-string에는 문자열 중 하나에 대한 주석이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-132">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="db889-133">`ConvertFrom-StringData` 한 줄로 된 주석을 무시 하지만 `#` 문자는 줄에서 공백이 아닌 첫 번째 문자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-133">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="db889-134">뒤의 줄에 있는 모든 문자는 `#` 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-134">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="db889-135">예제 4: 문자열을 해시 테이블로 변환</span><span class="sxs-lookup"><span data-stu-id="db889-135">Example 4: Convert a string to a hash table</span></span>

<span data-ttu-id="db889-136">이 예에서는 일반 이중 따옴표 붙은 문자열 (여기 문자열 아님)을 해시 테이블로 변환 하 고 `$A` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-136">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

<span data-ttu-id="db889-137">각 키-값 쌍이 별도의 줄에 있어야 하는 조건을 충족 하기 위해 문자열은 PowerShell 줄 바꿈 문자 ( \` n)를 사용 하 여 쌍을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-137">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="db889-138">예 5: 스크립트의 데이터 섹션에서 ConvertFrom-StringData 사용</span><span class="sxs-lookup"><span data-stu-id="db889-138">Example 5: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="db889-139">이 예에서는 `ConvertFrom-StringData` 스크립트의 데이터 섹션에 사용 되는 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db889-139">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="db889-140">DATA 섹션 아래에 있는 문은 사용자에게 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-140">The statements below the DATA section display the text to the user.</span></span>

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

<span data-ttu-id="db889-141">텍스트에 변수 이름이 포함되어 있으므로 변수를 확장하지 않고 문자 그대로 해석하기 위해 텍스트를 작은따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-141">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="db889-142">**데이터** 섹션에는 변수가 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-142">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="db889-143">예제 6: 파이프라인 연산자를 사용 하 여 문자열 전달</span><span class="sxs-lookup"><span data-stu-id="db889-143">Example 6: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="db889-144">이 예제에서는 파이프라인 연산자 ()를 사용 하 여 `|` 에 문자열을 보낼 수 있음을 보여 줍니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="db889-144">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="db889-145">변수의 값은 `$Here` 로 파이프 되 `ConvertFrom-StringData` 고 결과는 변수로 전달 됩니다 `$Hash` .</span><span class="sxs-lookup"><span data-stu-id="db889-145">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### <span data-ttu-id="db889-146">예 7: 이스케이프 문자를 사용 하 여 새 줄 및 반환 문자 추가</span><span class="sxs-lookup"><span data-stu-id="db889-146">Example 7: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="db889-147">이 예제에서는 이스케이프 문자를 사용 하 여 소스 데이터에 새 줄을 만들고 문자를 반환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db889-147">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="db889-148">이스케이프 시퀀스는 `\n` 결과 해시 테이블의 이름이 나 항목과 연결 된 텍스트 블록 내에 새 줄을 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-148">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### <span data-ttu-id="db889-149">예 8: 백슬래시 이스케이프 문자를 사용 하 여 파일 경로 올바르게 렌더링</span><span class="sxs-lookup"><span data-stu-id="db889-149">Example 8: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="db889-150">이 예제에서는 문자열 데이터에서 백슬래시 이스케이프 문자를 사용 하 여 결과 해시 테이블에서 파일 경로가 올바르게 렌더링 되도록 하는 방법을 보여 줍니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="db889-150">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="db889-151">이중 백슬래시는 리터럴 백슬래시가 해시 테이블 출력에 제대로 렌더링되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-151">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="db889-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db889-152">PARAMETERS</span></span>

### <span data-ttu-id="db889-153">-StringData</span><span class="sxs-lookup"><span data-stu-id="db889-153">-StringData</span></span>

<span data-ttu-id="db889-154">변환할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-154">Specifies the string to be converted.</span></span> <span data-ttu-id="db889-155">이 매개 변수를 사용 하거나 문자열을로 파이프 할 수 있습니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="db889-155">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="db889-156">매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="db889-156">The parameter name is optional.</span></span>

<span data-ttu-id="db889-157">이 매개 변수 값은 하나 이상의 키-값 쌍을 포함 하는 문자열 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-157">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="db889-158">각 키-값 쌍은 별도의 줄에 있어야 하며, 각 쌍은 줄 바꿈 문자 (n)로 구분 해야 합니다 \` .</span><span class="sxs-lookup"><span data-stu-id="db889-158">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="db889-159">문자열에 주석을 포함할 수 있지만 주석은 키-값 쌍과 같은 줄에 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-159">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="db889-160">`ConvertFrom-StringData` 한 줄로 이루어진 주석을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-160">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="db889-161">`#`문자는 줄에서 공백이 아닌 첫 번째 문자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-161">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="db889-162">뒤의 줄에 있는 모든 문자는 `#` 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-162">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="db889-163">주석은 해시 테이블에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-163">The comments are not included in the hash table.</span></span>

<span data-ttu-id="db889-164">여기에 있는 문자열은 하나 이상의 줄로 구성 된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="db889-164">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="db889-165">여기에 표시 되는 문자열 내의 따옴표는 문자열 데이터의 일부로 문자 그대로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-165">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="db889-166">자세한 내용은 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db889-166">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="db889-167">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="db889-167">-Delimiter</span></span>

<span data-ttu-id="db889-168">변환 되는 문자열의 **값** 데이터에서 **키** 를 구분 하는 데 사용 되는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="db889-168">The character used to separate the **key** from the **value** data in the string being converted.</span></span>
<span data-ttu-id="db889-169">기본 구분 기호는 등호 ( `=` ) 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="db889-169">The default delimiter is the equals sign (`=`) character.</span></span> <span data-ttu-id="db889-170">이 매개 변수는 PowerShell 7에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-170">This parameter was added in PowerShell 7.</span></span>

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db889-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db889-171">CommonParameters</span></span>

<span data-ttu-id="db889-172">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db889-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db889-173">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db889-173">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="db889-174">입력</span><span class="sxs-lookup"><span data-stu-id="db889-174">INPUTS</span></span>

### <span data-ttu-id="db889-175">System.String</span><span class="sxs-lookup"><span data-stu-id="db889-175">System.String</span></span>

<span data-ttu-id="db889-176">키-값 쌍을 포함 하는 문자열을로 파이프 할 수 있습니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="db889-176">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="db889-177">출력</span><span class="sxs-lookup"><span data-stu-id="db889-177">OUTPUTS</span></span>

### <span data-ttu-id="db889-178">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="db889-178">System.Collections.Hashtable</span></span>

<span data-ttu-id="db889-179">이 cmdlet은 키-값 쌍에서 만든 해시 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="db889-179">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="db889-180">참고</span><span class="sxs-lookup"><span data-stu-id="db889-180">NOTES</span></span>

<span data-ttu-id="db889-181">here-string은 하나 이상의 줄로 이루어진 문자열로, 이 문자열 내에서 따옴표는 문자 그대로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="db889-181">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="db889-182">이 cmdlet은 여러 음성 언어로 사용자 메시지를 표시 하는 스크립트에서 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-182">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="db889-183">사전 스타일의 해시 테이블을 사용하여 리소스 파일에서처럼 코드에서 텍스트 문자열을 분리하고 번역 도구에서 사용하도록 텍스트 문자열의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db889-183">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="db889-184">관련 링크</span><span class="sxs-lookup"><span data-stu-id="db889-184">RELATED LINKS</span></span>

