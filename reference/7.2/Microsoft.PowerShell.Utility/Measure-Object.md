---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 594837b2f85f4d5d5d4125d3f7c63ad2c8a16153
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605011"
---
# <span data-ttu-id="572b6-102">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-102">Measure-Object</span></span>

## <span data-ttu-id="572b6-103">개요</span><span class="sxs-lookup"><span data-stu-id="572b6-103">SYNOPSIS</span></span>
<span data-ttu-id="572b6-104">개체의 숫자 속성과 텍스트 파일 등 문자열 개체의 문자, 단어 및 줄을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-104">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="572b6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="572b6-105">SYNTAX</span></span>

### <span data-ttu-id="572b6-106">GenericMeasure (기본값)</span><span class="sxs-lookup"><span data-stu-id="572b6-106">GenericMeasure (Default)</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### <span data-ttu-id="572b6-107">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="572b6-107">TextMeasure</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="572b6-108">설명</span><span class="sxs-lookup"><span data-stu-id="572b6-108">DESCRIPTION</span></span>

<span data-ttu-id="572b6-109">`Measure-Object`Cmdlet은 특정 개체 유형의 속성 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-109">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="572b6-110">`Measure-Object` 는 명령의 매개 변수에 따라 세 가지 유형의 측정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-110">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="572b6-111">`Measure-Object`Cmdlet은 개체의 속성 값에 대 한 계산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-111">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="572b6-112">`Measure-Object`를 사용 하 여 개체 수를 계산 하거나 지정 된 **속성** 을 사용 하 여 개체를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-112">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="572b6-113">를 사용 하 여 `Measure-Object` 숫자 값의 **최소값**, **최대값**, **합계**, **standarddeviation** 및 **평균** 을 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-113">You can also use `Measure-Object` to calculate the **Minimum**, **Maximum**, **Sum**, **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="572b6-114">**문자열** 개체의 경우를 사용 하 여 `Measure-Object` 줄, 단어 및 문자 수를 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-114">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="572b6-115">예제</span><span class="sxs-lookup"><span data-stu-id="572b6-115">EXAMPLES</span></span>

### <span data-ttu-id="572b6-116">예 1: 디렉터리에서 파일 및 폴더 수 계산</span><span class="sxs-lookup"><span data-stu-id="572b6-116">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="572b6-117">이 명령은 현재 디렉터리의 파일 및 폴더 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-117">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="572b6-118">예 2: 디렉터리에서 파일 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-118">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="572b6-119">이 명령은 현재 디렉터리에 있는 모든 파일 크기의 **최소값**, **최대값** 및 **합계** 와 디렉터리에 있는 파일의 평균 크기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-119">This command displays the **Minimum**, **Maximum**, and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="572b6-120">예 3: 텍스트 파일의 측정 텍스트</span><span class="sxs-lookup"><span data-stu-id="572b6-120">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="572b6-121">이 명령은 Text.txt 파일의 문자, 단어 및 줄 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-121">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="572b6-122">**원시** 매개 변수가 없으면은 `Get-Content` 파일을 줄의 배열로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-122">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="572b6-123">첫 번째 명령은 `Set-Content` 를 사용 하 여 일부 기본 텍스트를 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-123">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="572b6-124">예 4: 지정 된 속성을 포함 하는 측정값 개체</span><span class="sxs-lookup"><span data-stu-id="572b6-124">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="572b6-125">이 예에서는 **DisplayName** 속성이 있는 개체의 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-125">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="572b6-126">처음 두 명령은 로컬 컴퓨터의 모든 서비스 및 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-126">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="572b6-127">세 번째 명령은 서비스와 프로세스의 조합 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-127">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="572b6-128">마지막 명령은 두 개의 컬렉션을 결합 하 고 결과를로 파이프 합니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="572b6-128">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="572b6-129">**System.object** 개체에 **DisplayName** 속성이 없으며 최종 카운트를 벗어난 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-129">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### <span data-ttu-id="572b6-130">예 5: CSV 파일의 내용 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-130">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="572b6-131">이 명령은 회사 직원의 평균 근무 기간(년)을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-131">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="572b6-132">`ServiceYrs.csv`이 파일은 직원 번호와 각 직원의 서비스 연도를 포함 하는 CSV 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-132">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="572b6-133">테이블의 첫 번째 행은 **EmpNo**, **Years** 의 머리글 행입니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-133">The first row in the table is a header row of **EmpNo**, **Years**.</span></span>

<span data-ttu-id="572b6-134">를 사용 하 여 `Import-Csv` 파일을 가져올 때 결과는 **EmpNo** 및 **Years** 의 note 속성이 있는 **PSCustomObject** 입니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-134">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="572b6-135">`Measure-Object`를 사용 하 여 개체의 다른 속성과 마찬가지로 이러한 속성의 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-135">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="572b6-136">예 6: 부울 값 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-136">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="572b6-137">이 예제에서는가 부울 값을 측정 하는 방법을 보여 줍니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="572b6-137">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="572b6-138">이 경우 **PSIsContainer** **Boolean** 속성을 사용 하 여 현재 디렉터리에서 폴더 (vs. 파일)의 발생을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-138">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### <span data-ttu-id="572b6-139">예 7: 측정값 문자열</span><span class="sxs-lookup"><span data-stu-id="572b6-139">Example 7: Measure strings</span></span>

<span data-ttu-id="572b6-140">다음 예에서는 줄의 수, 먼저 단일 문자열, 여러 문자열을 차례로 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-140">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="572b6-141">줄 바꿈 문자는 <code>\`n</code> 문자열을 여러 줄로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-141">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### <span data-ttu-id="572b6-142">예 8: 모든 값 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-142">Example 8: Measure all the values</span></span>

<span data-ttu-id="572b6-143">PowerShell 6부터의 **Allstats** 매개 변수를 사용 하 여 `Measure-Object` 모든 통계를 함께 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-143">Beginning in PowerShell 6, the **AllStats** parameter of `Measure-Object` allows you to measure all the statistics together.</span></span>

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### <span data-ttu-id="572b6-144">예 9: scriptblock 속성을 사용 하 여 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-144">Example 9: Measure using scriptblock properties</span></span>

<span data-ttu-id="572b6-145">PowerShell 6부터은 `Measure-Object` **ScriptBlock** 속성을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-145">Beginning in PowerShell 6, `Measure-Object` supports **ScriptBlock** properties.</span></span> <span data-ttu-id="572b6-146">다음 예제에서는 **ScriptBlock** 속성을 사용 하 여 디렉터리에 있는 모든 파일의 크기 (mb)를 결정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-146">The following example demonstrates how to use a **ScriptBlock** property to determine the size, in MegaBytes, of all the files in a directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### <span data-ttu-id="572b6-147">예 10: 측정값 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="572b6-147">Example 10: Measure hashtables</span></span>

<span data-ttu-id="572b6-148">PowerShell 6부터 `Measure-Object` 은 **해시 테이블** 입력 측정을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-148">Beginning in PowerShell 6, `Measure-Object` supports measurement of **hashtable** input.</span></span> <span data-ttu-id="572b6-149">다음 예에서는 `num` 3 개의 **해시 테이블** 개체의 키에 대 한 가장 큰 값을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-149">The following example determines the largest value for the `num` key of 3 **hashtable** objects.</span></span>

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### <span data-ttu-id="572b6-150">예 11: 표준 편차 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-150">Example 11: Measure the Standard Deviation</span></span>

<span data-ttu-id="572b6-151">PowerShell 6부터 `Measure-Object` 은 `-StandardDeviation` 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-151">Beginning in PowerShell 6, `Measure-Object` supports the `-StandardDeviation` parameter.</span></span> <span data-ttu-id="572b6-152">다음 예에서는 모든 프로세스에서 사용 하는 CPU에 대 한 *표준 편차* 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-152">The following example determines the *standard deviation* for the CPU used by all processes.</span></span> <span data-ttu-id="572b6-153">큰 편차는 대부분의 CPU를 사용 하는 적은 수의 프로세스를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-153">A large deviation would indicate a small number of processes consuming the most CPU.</span></span>

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### <span data-ttu-id="572b6-154">예 12: 와일드 카드를 사용 하 여 측정</span><span class="sxs-lookup"><span data-stu-id="572b6-154">Example 12: Measure using wildcards</span></span>

<span data-ttu-id="572b6-155">PowerShell 6부터에서는 `Measure-Object` 속성 이름에 와일드 카드를 사용 하 여 개체 측정을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-155">Beginning in PowerShell 6, `Measure-Object` supports measurement of objects by using wildcards in property names.</span></span> <span data-ttu-id="572b6-156">다음 예에서는 프로세스 집합에서 페이징 메모리 사용의 최대 크기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-156">The following example determines the maximum of any type of paged memory usage among a set of processes.</span></span>

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## <span data-ttu-id="572b6-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="572b6-157">PARAMETERS</span></span>

### <span data-ttu-id="572b6-158">-평균</span><span class="sxs-lookup"><span data-stu-id="572b6-158">-Average</span></span>

<span data-ttu-id="572b6-159">Cmdlet에서 지정 된 속성의 평균 값을 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-159">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-160">-문자</span><span class="sxs-lookup"><span data-stu-id="572b6-160">-Character</span></span>

<span data-ttu-id="572b6-161">Cmdlet이 입력 개체의 문자 수를 계산 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-161">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="572b6-162">**단어**, **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-162">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="572b6-163">예 7을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="572b6-163">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-164">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="572b6-164">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="572b6-165">Cmdlet이 문자 수의 공백을 무시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-165">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="572b6-166">기본적으로 공백은 무시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-166">By default, white space is not ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="572b6-167">-InputObject</span></span>

<span data-ttu-id="572b6-168">측정할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-168">Specifies the objects to be measured.</span></span>
<span data-ttu-id="572b6-169">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="572b6-169">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="572b6-170">에 **inputobject** 매개 변수를 사용 하는 경우 `Measure-Object` 명령 결과를로 파이프 하는 대신 `Measure-Object` **inputobject** 값은 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-170">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="572b6-171">`Measure-Object`개체의 정의 된 속성에 특정 값이 있는지 여부에 따라 개체의 컬렉션을 측정 하려면 파이프라인에서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-171">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-172">-줄</span><span class="sxs-lookup"><span data-stu-id="572b6-172">-Line</span></span>

<span data-ttu-id="572b6-173">Cmdlet이 입력 개체의 줄 수를 계산 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-173">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="572b6-174">**단어**, **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-174">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="572b6-175">예 7을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="572b6-175">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-176">-최대</span><span class="sxs-lookup"><span data-stu-id="572b6-176">-Maximum</span></span>

<span data-ttu-id="572b6-177">Cmdlet에서 지정 된 속성의 최대값을 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-177">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-178">-최소</span><span class="sxs-lookup"><span data-stu-id="572b6-178">-Minimum</span></span>

<span data-ttu-id="572b6-179">Cmdlet에서 지정 된 속성의 최소값이 표시 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-179">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-180">-속성</span><span class="sxs-lookup"><span data-stu-id="572b6-180">-Property</span></span>

<span data-ttu-id="572b6-181">측정할 속성을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-181">Specifies one or more properties to measure.</span></span> <span data-ttu-id="572b6-182">다른 측정값을 지정 하지 않으면에서 `Measure-Object` 지정한 속성을 가진 개체의 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-182">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

<span data-ttu-id="572b6-183">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-183">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="572b6-184">계산 된 속성은 스크립트 블록 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-184">The calculated property must be a script block.</span></span> <span data-ttu-id="572b6-185">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="572b6-185">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="572b6-186">-StandardDeviation</span><span class="sxs-lookup"><span data-stu-id="572b6-186">-StandardDeviation</span></span>

<span data-ttu-id="572b6-187">Cmdlet에서 지정 된 속성 값의 표준 편차를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-187">Indicates that the cmdlet displays the standard deviation of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-188">-합계</span><span class="sxs-lookup"><span data-stu-id="572b6-188">-Sum</span></span>

<span data-ttu-id="572b6-189">Cmdlet에서 지정 된 속성 값의 합계를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-189">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-190">-AllStats</span><span class="sxs-lookup"><span data-stu-id="572b6-190">-AllStats</span></span>

<span data-ttu-id="572b6-191">Cmdlet이 지정 된 속성의 모든 통계를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-191">Indicates that the cmdlet displays all the statistics of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-192">-Word</span><span class="sxs-lookup"><span data-stu-id="572b6-192">-Word</span></span>

<span data-ttu-id="572b6-193">Cmdlet이 입력 개체의 단어 수를 계산 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-193">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="572b6-194">**단어**, **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-194">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="572b6-195">예 7을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="572b6-195">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="572b6-196">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="572b6-196">CommonParameters</span></span>

<span data-ttu-id="572b6-197">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="572b6-197">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="572b6-198">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="572b6-198">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="572b6-199">입력</span><span class="sxs-lookup"><span data-stu-id="572b6-199">INPUTS</span></span>

### <span data-ttu-id="572b6-200">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="572b6-200">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="572b6-201">개체를로 파이프 할 수 있습니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="572b6-201">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="572b6-202">출력</span><span class="sxs-lookup"><span data-stu-id="572b6-202">OUTPUTS</span></span>

### <span data-ttu-id="572b6-203">그러지 않으면 genericmeasureinfo.</span><span class="sxs-lookup"><span data-stu-id="572b6-203">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="572b6-204">TextMeasureInfo.</span><span class="sxs-lookup"><span data-stu-id="572b6-204">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="572b6-205">**Word** 매개 변수를 사용 하는 경우 `Measure-Object` **TextMeasureInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-205">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="572b6-206">그렇지 않으면 **그러지 않으면 genericmeasureinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="572b6-206">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="572b6-207">참고</span><span class="sxs-lookup"><span data-stu-id="572b6-207">NOTES</span></span>

## <span data-ttu-id="572b6-208">관련 링크</span><span class="sxs-lookup"><span data-stu-id="572b6-208">RELATED LINKS</span></span>

[<span data-ttu-id="572b6-209">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="572b6-209">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="572b6-210">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-210">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="572b6-211">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-211">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="572b6-212">Group-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-212">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="572b6-213">New-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-213">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="572b6-214">Select-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-214">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="572b6-215">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-215">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="572b6-216">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-216">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="572b6-217">Where-Object</span><span class="sxs-lookup"><span data-stu-id="572b6-217">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
