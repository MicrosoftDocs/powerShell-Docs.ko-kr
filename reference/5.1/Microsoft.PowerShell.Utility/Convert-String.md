---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214146"
---
# <span data-ttu-id="502e6-103">Convert-String</span><span class="sxs-lookup"><span data-stu-id="502e6-103">Convert-String</span></span>

## <span data-ttu-id="502e6-104">개요</span><span class="sxs-lookup"><span data-stu-id="502e6-104">SYNOPSIS</span></span>
<span data-ttu-id="502e6-105">예제와 일치 하도록 문자열의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-105">Formats a string to match examples.</span></span>

## <span data-ttu-id="502e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="502e6-106">SYNTAX</span></span>

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## <span data-ttu-id="502e6-107">설명</span><span class="sxs-lookup"><span data-stu-id="502e6-107">DESCRIPTION</span></span>

<span data-ttu-id="502e6-108">**Convert-문자열** cmdlet은 예제의 형식과 일치 하도록 문자열의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-108">The **Convert-String** cmdlet formats a string to match the format of examples.</span></span>

## <span data-ttu-id="502e6-109">예제</span><span class="sxs-lookup"><span data-stu-id="502e6-109">EXAMPLES</span></span>

### <span data-ttu-id="502e6-110">예제 1: 문자열 형식 변환</span><span class="sxs-lookup"><span data-stu-id="502e6-110">Example 1: Convert format of a string</span></span>

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

<span data-ttu-id="502e6-111">첫 번째 명령은 이름과 성이 포함 된 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-111">The first command creates an array that contains first and last names.</span></span>

<span data-ttu-id="502e6-112">두 번째 명령은 예제에 따라 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-112">The second command formats the names according to the example.</span></span>
<span data-ttu-id="502e6-113">이니셜을 먼저 출력에 배치 하 고 그 뒤에 이니셜을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-113">It puts the surname first in the output, followed by an initial.</span></span>

### <span data-ttu-id="502e6-114">예제 2: 문자열 형식 단순화</span><span class="sxs-lookup"><span data-stu-id="502e6-114">Example 2: Simplify format of a string</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

<span data-ttu-id="502e6-115">첫 번째 명령은 첫 번째, 중간 이름 및 성을 포함 하는 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-115">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="502e6-116">마지막 항목에는 중간 이름이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-116">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="502e6-117">두 번째 명령은 예제에 따라 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-117">The second command formats the names according to the example.</span></span>
<span data-ttu-id="502e6-118">출력에서 성을 먼저 입력 한 다음 첫 번째 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-118">It puts the last name first in the output, followed by the first name.</span></span>
<span data-ttu-id="502e6-119">모든 중간 이름이 제거 되었습니다. 중간 이름이 없는 항목이 올바르게 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-119">All middle names removed; entry without middle name is handled correctly.</span></span>

### <span data-ttu-id="502e6-120">예 3: 문자열이 일치 하지 않는 경우의 출력 관리 예</span><span class="sxs-lookup"><span data-stu-id="502e6-120">Example 3: Output management when strings don't match example</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

<span data-ttu-id="502e6-121">첫 번째 명령은 첫 번째, 중간 이름 및 성을 포함 하는 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-121">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="502e6-122">마지막 항목에는 중간 이름이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-122">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="502e6-123">두 번째 명령은 예제에 따라 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-123">The second command formats the names according to the example.</span></span>
<span data-ttu-id="502e6-124">**중간 이름을** 출력에 먼저 배치 하 고 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-124">It puts the **middle name** first in the output, followed by the first name.</span></span>
<span data-ttu-id="502e6-125">**$Composers** 의 마지막 항목은 샘플 패턴과 일치 하지 않기 때문에 건너뜁니다. 중간 이름이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-125">The last entry in **$Composers** is skipped, because it doesn't match the sample pattern: it has no middle name.</span></span>

### <span data-ttu-id="502e6-126">예제 4: 장점 공간 주의</span><span class="sxs-lookup"><span data-stu-id="502e6-126">Example 4: Caution with beauty spaces</span></span>

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

<span data-ttu-id="502e6-127">첫 번째 명령은 이름 및 성의 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-127">The first command creates an array of first and last names.</span></span>
<span data-ttu-id="502e6-128">두 번째와 네 번째 항목에는 마지막 이름 뒤에 후행 공백이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-128">Note that second and fourth items have an extra trailing space, after the last name.</span></span>

<span data-ttu-id="502e6-129">두 번째 명령은 _단어, 공백, 단어 및 마지막 후행 공백과_ 같은 샘플 패턴과 일치 하는 모든 문자열을 등호 앞의 모두로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-129">The second command converts all strings that match the sample pattern: _word, space, word, and final trailing space_ , all of this before the equal sign.</span></span>
<span data-ttu-id="502e6-130">또한 출력의 선행 공간도 적어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-130">Also, note the leading space in the output.</span></span>

### <span data-ttu-id="502e6-131">예 5: 여러 패턴으로 프로세스 정보 서식 지정</span><span class="sxs-lookup"><span data-stu-id="502e6-131">Example 5: Format process information with multiple patterns</span></span>

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

<span data-ttu-id="502e6-132">**$ExamplePatterns** 는 예제를 통해 데이터에 예상 되는 다양 한 패턴을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-132">**$ExamplePatterns** defines different expected patterns in the data, through examples.</span></span>

<span data-ttu-id="502e6-133">첫 번째 패턴는 `@{before='"Hello","World"'; after='World: Hello'}` 다음과 같습니다. 단어를 큰따옴표로 _묶은 문자열을 사용한 다음 쉼표_ 와 
 _두 번째 및 마지막 단어를 따옴표로 묶습니다._ 
 _문자열에 공백이 없는입니다. 출력에서는 두 번째 단어 (_ 따옴표 제외)를 먼저 입력 한 
 _다음 공백 하나, 첫 번째 단어 (따옴표 제외_ )를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-133">The first pattern, `@{before='"Hello","World"'; after='World: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then the second, and last, word enclosed in quotes;_
_with no spaces in the string. On the output: place second word first,_
_without quotes, then a single space, and then the first word, without quotes._</span></span>

<span data-ttu-id="502e6-134">두 번째 패턴 인은 `@{before='"Hello","1"'; after='1: Hello'}` 다음과 같이 표시 됩니다. 즉, 단어를 큰따옴표로 _묶은 문자열을 사용한 다음 쉼표_ 
 _와 따옴표로 묶인 숫자를 가져옵니다._ 
 _문자열에 공백이 없는입니다. 출력에서: 숫자_ 를 따옴표 없이 먼저 입력 한 다음 공백 하나, 
 _단어 (따옴표 제외_ )를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-134">The second pattern, `@{before='"Hello","1"'; after='1: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then a number enclosed in quotes;_
_with no spaces in the string. On the output: place the number first,_
_without quotes, then a single space, and then the word, without quotes._</span></span>

<span data-ttu-id="502e6-135">세 번째 패턴 인은 `@{before='"Hello-World","22"'; after='22: Hello-World'}` 다음과 같이 표시 됩니다 _expect strings where two words with a hyphen in between come enclosed in_ 
 _double quotes, then a comma, and then a number enclosed in quotes;_ 
 . 사이에 하이픈이 있는 두 단어가 큰따옴표로 묶여 오고 쉼표를 사용한 다음 따옴표로 묶인 숫자를 표시 합니다. _쉼표와 세 번째 큰따옴표 사이에 공백이 없어야 합니다._ 
 _출력에서: 숫자를 따옴표 없이 먼저 입력 한 다음 공백_ 
 하나를 입력 합니다. _그리고 따옴표를 사용 하지 않고 하이픈을 넣은 단어를 사용 합니다._</span><span class="sxs-lookup"><span data-stu-id="502e6-135">The third pattern, `@{before='"Hello-World","22"'; after='22: Hello-World'}`, reads as follows: _expect strings where two words with a hyphen in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the hyphenated words, without quotes._</span></span>

<span data-ttu-id="502e6-136">네 번째 및 마지막, 패턴,은 `@{before='"hello world","333"'; after='333: hello world'}` 다음과 같이 표시 됩니다. _사이에 공백이 있는 두 단어가 큰따옴표로 묶여_ 오고 
 _쉼표와 따옴표로 묶인 숫자가 표시 됩니다._ 
 _쉼표와 세 번째 큰따옴표 사이에 공백이 없어야 합니다._ 
 _출력에서: 숫자를 따옴표 없이 먼저 입력 한 다음 공백_ 
 하나를 입력 합니다. 그 _다음에 공백이 없는 단어 사이에 공백이 있습니다._</span><span class="sxs-lookup"><span data-stu-id="502e6-136">The fourth, and final, pattern, `@{before='"hello world","333"'; after='333: hello world'}`, reads as follows: _expect strings where two words with a space in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the words with the space in between, without quotes._</span></span>

<span data-ttu-id="502e6-137">첫 번째 명령은 Get-Process cmdlet을 사용 하 여 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-137">The first command gets all processes by using the Get-Process cmdlet.</span></span>
<span data-ttu-id="502e6-138">이 명령은 프로세스 이름 및 프로세스 ID를 선택 하는 Select-Object cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-138">The command passes them to the Select-Object cmdlet, which selects the process name and process ID.</span></span> <span data-ttu-id="502e6-139">파이프라인의 끝에서 명령은 ConvertTo-Csv cmdlet을 사용 하 여 출력을 형식 정보가 없는 쉼표로 구분 된 값으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-139">At the end of the pipeline, the command converts the output to comma separated values, without type information, by using the ConvertTo-Csv cmdlet.</span></span>
<span data-ttu-id="502e6-140">이 명령은 **$Processes** 변수에 결과를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-140">The command stores the results in the **$Processes** variable.</span></span>
<span data-ttu-id="502e6-141">이제 **$Processes** 에 프로세스 이름 및 PID가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-141">**$Processes** now contains process names and PID.</span></span>

<span data-ttu-id="502e6-142">두 번째 명령은 입력 항목의 순서를 변경 하는 예제 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-142">The second command specifies an example variable that changes the order of the input items.</span></span>
<span data-ttu-id="502e6-143">명령은 **$Processes** 의 각 문자열을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-143">The command coverts each string in **$Processes** .</span></span>

><span data-ttu-id="502e6-144">**참고** 네 번째 패턴은 공백으로 구분 된 두 개 이상의 단어가 일치 함을 암시적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-144">**Note** The fourth pattern implicitly says that two or more words separated by spaces are matched.</span></span>
>
><span data-ttu-id="502e6-145">네 번째 패턴이 없으면 큰따옴표로 묶인 문자열의 첫 번째 단어만 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-145">Without the fourth pattern, only the first word of the string enclosed in double quotes is matched.</span></span>

## <span data-ttu-id="502e6-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="502e6-146">PARAMETERS</span></span>

### <span data-ttu-id="502e6-147">-예제</span><span class="sxs-lookup"><span data-stu-id="502e6-147">-Example</span></span>

<span data-ttu-id="502e6-148">대상 형식의 예 목록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-148">Specifies a list of examples of the target format.</span></span>
<span data-ttu-id="502e6-149">등호 (=)로 구분 된 쌍을 지정 합니다. 다음 예제와 같이 왼쪽의 소스 패턴과 오른쪽의 대상 패턴이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-149">Specify pairs separated by the equal (=) sign, with the source pattern on the left and the target pattern on the right, as in the following examples:</span></span>

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

><span data-ttu-id="502e6-150">**참고** 두 번째 예제에서는 패턴 목록을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-150">**Note** The second example uses a list of patterns</span></span>

<span data-ttu-id="502e6-151">또는 **전후** **속성을** 포함 하는 해시 테이블 목록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-151">Alternatively, specify a list of hash tables that contain **Before** and **After** properties.</span></span>

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

><span data-ttu-id="502e6-152">**주의** 패턴의 일부로 처리 되므로 등호 앞뒤에 공백을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="502e6-152">**Caution** Avoid using spaces around the equal sign, as they are treated as part of the pattern.</span></span>

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="502e6-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="502e6-153">-InputObject</span></span>

<span data-ttu-id="502e6-154">서식을 지정할 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-154">Specifies a string to format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="502e6-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="502e6-155">CommonParameters</span></span>

<span data-ttu-id="502e6-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="502e6-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="502e6-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="502e6-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="502e6-158">입력</span><span class="sxs-lookup"><span data-stu-id="502e6-158">INPUTS</span></span>

### <span data-ttu-id="502e6-159">String</span><span class="sxs-lookup"><span data-stu-id="502e6-159">String</span></span>

<span data-ttu-id="502e6-160">이 cmdlet으로 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-160">You can pipe strings to this cmdlet.</span></span>

## <span data-ttu-id="502e6-161">출력</span><span class="sxs-lookup"><span data-stu-id="502e6-161">OUTPUTS</span></span>

### <span data-ttu-id="502e6-162">String</span><span class="sxs-lookup"><span data-stu-id="502e6-162">String</span></span>

<span data-ttu-id="502e6-163">이 cmdlet은 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="502e6-163">This cmdlet returns a string.</span></span>

## <span data-ttu-id="502e6-164">참고</span><span class="sxs-lookup"><span data-stu-id="502e6-164">NOTES</span></span>

## <span data-ttu-id="502e6-165">관련 링크</span><span class="sxs-lookup"><span data-stu-id="502e6-165">RELATED LINKS</span></span>

[<span data-ttu-id="502e6-166">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="502e6-166">ConvertFrom-String</span></span>](ConvertFrom-String.md)

[<span data-ttu-id="502e6-167">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="502e6-167">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="502e6-168">Get-Process</span><span class="sxs-lookup"><span data-stu-id="502e6-168">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="502e6-169">Out-String</span><span class="sxs-lookup"><span data-stu-id="502e6-169">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="502e6-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="502e6-170">Select-Object</span></span>](Select-Object.md)
