---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 5d4a27f1a1949056ca63b9b6a2340bf1226592e0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219217"
---
# <span data-ttu-id="5e927-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-103">Measure-Object</span></span>

## <span data-ttu-id="5e927-104">개요</span><span class="sxs-lookup"><span data-stu-id="5e927-104">SYNOPSIS</span></span>
<span data-ttu-id="5e927-105">개체의 숫자 속성과 텍스트 파일 등 문자열 개체의 문자, 단어 및 줄을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="5e927-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e927-106">SYNTAX</span></span>

### <span data-ttu-id="5e927-107">GenericMeasure (기본값)</span><span class="sxs-lookup"><span data-stu-id="5e927-107">GenericMeasure (Default)</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Sum] [-Average] [-Maximum] [-Minimum]
 [<CommonParameters>]
```

### <span data-ttu-id="5e927-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="5e927-108">TextMeasure</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Line] [-Word] [-Character]
 [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="5e927-109">설명</span><span class="sxs-lookup"><span data-stu-id="5e927-109">DESCRIPTION</span></span>

<span data-ttu-id="5e927-110">`Measure-Object`Cmdlet은 특정 개체 유형의 속성 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="5e927-111">`Measure-Object` 는 명령의 매개 변수에 따라 세 가지 유형의 측정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="5e927-112">`Measure-Object`Cmdlet은 개체의 속성 값에 대 한 계산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="5e927-113">`Measure-Object`를 사용 하 여 개체 수를 계산 하거나 지정 된 **속성** 을 사용 하 여 개체를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-113">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="5e927-114">를 사용 하 여 `Measure-Object` 숫자 값의 **최소값** , **최대값** , **합계** , **standarddeviation** 및 **평균** 을 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="5e927-115">**문자열** 개체의 경우를 사용 하 여 `Measure-Object` 줄, 단어 및 문자 수를 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="5e927-116">예제</span><span class="sxs-lookup"><span data-stu-id="5e927-116">EXAMPLES</span></span>

### <span data-ttu-id="5e927-117">예 1: 디렉터리에서 파일 및 폴더 수 계산</span><span class="sxs-lookup"><span data-stu-id="5e927-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="5e927-118">이 명령은 현재 디렉터리의 파일 및 폴더 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="5e927-119">예 2: 디렉터리에서 파일 측정</span><span class="sxs-lookup"><span data-stu-id="5e927-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="5e927-120">이 명령은 현재 디렉터리에 있는 모든 파일 크기의 **최소값** , **최대값** 및 **합계** 와 디렉터리에 있는 파일의 평균 크기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="5e927-121">예 3: 텍스트 파일의 측정 텍스트</span><span class="sxs-lookup"><span data-stu-id="5e927-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="5e927-122">이 명령은 Text.txt 파일의 문자, 단어 및 줄 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="5e927-123">**원시** 매개 변수가 없으면은 `Get-Content` 파일을 줄의 배열로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="5e927-124">첫 번째 명령은 `Set-Content` 를 사용 하 여 일부 기본 텍스트를 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="5e927-125">예 4: 지정 된 속성을 포함 하는 측정값 개체</span><span class="sxs-lookup"><span data-stu-id="5e927-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="5e927-126">이 예에서는 **DisplayName** 속성이 있는 개체의 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="5e927-127">처음 두 명령은 로컬 컴퓨터의 모든 서비스 및 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="5e927-128">세 번째 명령은 서비스와 프로세스의 조합 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="5e927-129">마지막 명령은 두 개의 컬렉션을 결합 하 고 결과를로 파이프 합니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="5e927-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="5e927-130">**System.object** 개체에 **DisplayName** 속성이 없으며 최종 카운트를 벗어난 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

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

### <span data-ttu-id="5e927-131">예 5: CSV 파일의 내용 측정</span><span class="sxs-lookup"><span data-stu-id="5e927-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="5e927-132">이 명령은 회사 직원의 평균 근무 기간(년)을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="5e927-133">`ServiceYrs.csv`이 파일은 직원 번호와 각 직원의 서비스 연도를 포함 하는 CSV 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="5e927-134">테이블의 첫 번째 행은 **EmpNo** , **Years** 의 머리글 행입니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-134">The first row in the table is a header row of **EmpNo** , **Years**.</span></span>

<span data-ttu-id="5e927-135">를 사용 하 여 `Import-Csv` 파일을 가져올 때 결과는 **EmpNo** 및 **Years** 의 note 속성이 있는 **PSCustomObject** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="5e927-136">`Measure-Object`를 사용 하 여 개체의 다른 속성과 마찬가지로 이러한 속성의 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="5e927-137">예 6: 부울 값 측정</span><span class="sxs-lookup"><span data-stu-id="5e927-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="5e927-138">이 예제에서는가 부울 값을 측정 하는 방법을 보여 줍니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="5e927-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="5e927-139">이 경우 **PSIsContainer** **Boolean** 속성을 사용 하 여 현재 디렉터리에서 폴더 (vs. 파일)의 발생을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

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

### <span data-ttu-id="5e927-140">예 7: 측정값 문자열</span><span class="sxs-lookup"><span data-stu-id="5e927-140">Example 7: Measure strings</span></span>

<span data-ttu-id="5e927-141">다음 예에서는 줄의 수, 먼저 단일 문자열, 여러 문자열을 차례로 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="5e927-142">줄 바꿈 문자는 <code>\`n</code> 문자열을 여러 줄로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

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

## <span data-ttu-id="5e927-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5e927-143">PARAMETERS</span></span>

### <span data-ttu-id="5e927-144">-평균</span><span class="sxs-lookup"><span data-stu-id="5e927-144">-Average</span></span>

<span data-ttu-id="5e927-145">Cmdlet에서 지정 된 속성의 평균 값을 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-145">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

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

### <span data-ttu-id="5e927-146">-문자</span><span class="sxs-lookup"><span data-stu-id="5e927-146">-Character</span></span>

<span data-ttu-id="5e927-147">Cmdlet이 입력 개체의 문자 수를 계산 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-147">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="5e927-148">**단어** , **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-148">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="5e927-149">예 7을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e927-149">See Example 7.</span></span>

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

### <span data-ttu-id="5e927-150">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="5e927-150">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="5e927-151">Cmdlet이 문자 수의 공백을 무시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-151">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="5e927-152">기본적으로 공백은 무시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-152">By default, white space is not ignored.</span></span>

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

### <span data-ttu-id="5e927-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5e927-153">-InputObject</span></span>

<span data-ttu-id="5e927-154">측정할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-154">Specifies the objects to be measured.</span></span>
<span data-ttu-id="5e927-155">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="5e927-155">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="5e927-156">에 **inputobject** 매개 변수를 사용 하는 경우 `Measure-Object` 명령 결과를로 파이프 하는 대신 `Measure-Object` **inputobject** 값은 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-156">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="5e927-157">`Measure-Object`개체의 정의 된 속성에 특정 값이 있는지 여부에 따라 개체의 컬렉션을 측정 하려면 파이프라인에서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-157">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="5e927-158">-줄</span><span class="sxs-lookup"><span data-stu-id="5e927-158">-Line</span></span>

<span data-ttu-id="5e927-159">Cmdlet이 입력 개체의 줄 수를 계산 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-159">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="5e927-160">**단어** , **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-160">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="5e927-161">예 7을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e927-161">See Example 7.</span></span>

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

### <span data-ttu-id="5e927-162">-최대</span><span class="sxs-lookup"><span data-stu-id="5e927-162">-Maximum</span></span>

<span data-ttu-id="5e927-163">Cmdlet에서 지정 된 속성의 최대값을 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-163">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

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

### <span data-ttu-id="5e927-164">-최소</span><span class="sxs-lookup"><span data-stu-id="5e927-164">-Minimum</span></span>

<span data-ttu-id="5e927-165">Cmdlet에서 지정 된 속성의 최소값이 표시 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-165">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

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

### <span data-ttu-id="5e927-166">-속성</span><span class="sxs-lookup"><span data-stu-id="5e927-166">-Property</span></span>

<span data-ttu-id="5e927-167">측정할 속성을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-167">Specifies one or more properties to measure.</span></span> <span data-ttu-id="5e927-168">다른 측정값을 지정 하지 않으면에서 `Measure-Object` 지정한 속성을 가진 개체의 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-168">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5e927-169">-합계</span><span class="sxs-lookup"><span data-stu-id="5e927-169">-Sum</span></span>

<span data-ttu-id="5e927-170">Cmdlet에서 지정 된 속성 값의 합계를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-170">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

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

### <span data-ttu-id="5e927-171">-Word</span><span class="sxs-lookup"><span data-stu-id="5e927-171">-Word</span></span>

<span data-ttu-id="5e927-172">Cmdlet이 입력 개체의 단어 수를 계산 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-172">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="5e927-173">**단어** , **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-173">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="5e927-174">예 7을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e927-174">See Example 7.</span></span>

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

### <span data-ttu-id="5e927-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e927-175">CommonParameters</span></span>

<span data-ttu-id="5e927-176">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e927-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e927-177">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e927-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e927-178">입력</span><span class="sxs-lookup"><span data-stu-id="5e927-178">INPUTS</span></span>

### <span data-ttu-id="5e927-179">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="5e927-179">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5e927-180">개체를로 파이프 할 수 있습니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="5e927-180">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="5e927-181">출력</span><span class="sxs-lookup"><span data-stu-id="5e927-181">OUTPUTS</span></span>

### <span data-ttu-id="5e927-182">그러지 않으면 genericmeasureinfo.</span><span class="sxs-lookup"><span data-stu-id="5e927-182">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="5e927-183">TextMeasureInfo.</span><span class="sxs-lookup"><span data-stu-id="5e927-183">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="5e927-184">**Word** 매개 변수를 사용 하는 경우 `Measure-Object` **TextMeasureInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-184">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="5e927-185">그렇지 않으면 **그러지 않으면 genericmeasureinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e927-185">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="5e927-186">참고</span><span class="sxs-lookup"><span data-stu-id="5e927-186">NOTES</span></span>

## <span data-ttu-id="5e927-187">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5e927-187">RELATED LINKS</span></span>

[<span data-ttu-id="5e927-188">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-188">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="5e927-189">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-189">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="5e927-190">Group-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-190">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="5e927-191">New-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-191">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="5e927-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-192">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="5e927-193">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-193">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="5e927-194">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-194">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="5e927-195">Where-Object</span><span class="sxs-lookup"><span data-stu-id="5e927-195">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
