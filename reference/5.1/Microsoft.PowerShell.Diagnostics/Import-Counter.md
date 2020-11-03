---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/import-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Counter
ms.openlocfilehash: 837f6b4b3b2869c6f74b3b02904dd43b73f6bcd5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212673"
---
# <span data-ttu-id="5f166-103">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="5f166-103">Import-Counter</span></span>

## <span data-ttu-id="5f166-104">개요</span><span class="sxs-lookup"><span data-stu-id="5f166-104">SYNOPSIS</span></span>
<span data-ttu-id="5f166-105">성능 카운터 로그 파일을 가져오고 로그의 각 카운터 샘플을 나타내는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-105">Imports performance counter log files and creates the objects that represent each counter sample in the log.</span></span>

## <span data-ttu-id="5f166-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f166-106">SYNTAX</span></span>

### <span data-ttu-id="5f166-107">GetCounterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="5f166-107">GetCounterSet (Default)</span></span>

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="5f166-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="5f166-108">ListSetSet</span></span>

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### <span data-ttu-id="5f166-109">요약 집합</span><span class="sxs-lookup"><span data-stu-id="5f166-109">SummarySet</span></span>

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## <span data-ttu-id="5f166-110">설명</span><span class="sxs-lookup"><span data-stu-id="5f166-110">DESCRIPTION</span></span>

<span data-ttu-id="5f166-111">**Import-module** cmdlet은 성능 카운터 로그 파일에서 성능 카운터 데이터를 가져오고 파일의 각 카운터 샘플에 대 한 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-111">The **Import-Counter** cmdlet imports performance counter data from performance counter log files and creates objects for each counter sample in the file.</span></span>
<span data-ttu-id="5f166-112">생성 되는 **PerformanceCounterSampleSet** 개체는 성능 카운터 데이터를 수집할 때 **Get Counter** 에서 반환 하는 개체와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-112">The **PerformanceCounterSampleSet** objects that it creates are identical to the objects that **Get-Counter** returns when it collects performance counter data.</span></span>

<span data-ttu-id="5f166-113">쉼표로 구분된 값(.csv), 탭으로 구분된 값( .tsv) 및 이진 성능 로그(.blg) 성능 로그 파일에서 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-113">You can import data from comma-separated value (.csv), tab-separated value ( .tsv), and binary performance log (.blg) performance log files.</span></span>
<span data-ttu-id="5f166-114">.Blg 파일을 사용 하는 경우 각 명령에서 최대 32 개의 파일을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-114">If you are using .blg files, you can import up to 32 files in each command.</span></span>
<span data-ttu-id="5f166-115">Import **-Counter** 의 매개 변수를 사용 하 여 가져온 데이터를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-115">You can use the parameters of **Import-Counter** to filter the data that you import.</span></span>

<span data-ttu-id="5f166-116">Get-Counter 및 Export-Counter cmdlet과 함께이 기능을 사용 하면 Windows PowerShell 내에서 성능 카운터 데이터를 수집 하 고, 내보내고, 가져오고, 결합 하 고, 필터링 하 고, 조작 하 고, 다시 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-116">Along with the Get-Counter and Export-Counter cmdlets, this feature lets you collect, export, import, combine, filter, manipulate, and re-export performance counter data within Windows PowerShell.</span></span>

## <span data-ttu-id="5f166-117">예제</span><span class="sxs-lookup"><span data-stu-id="5f166-117">EXAMPLES</span></span>

### <span data-ttu-id="5f166-118">예제 1: 파일에서 모든 카운터 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="5f166-118">Example 1: Import all counter data from a file</span></span>

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

<span data-ttu-id="5f166-119">이 명령은 ProcessorData.csv 파일에서 $Data 변수로 모든 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-119">This command imports all counter data from the ProcessorData.csv file into the $Data variable.</span></span>

### <span data-ttu-id="5f166-120">예제 2: 파일에서 특정 카운터 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="5f166-120">Example 2: Import specific counter data from a file</span></span>

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

<span data-ttu-id="5f166-121">이 명령은 Processordata.csv 파일의 **"Processor (_total) \ 인터럽트/sec"** 카운터 데이터만 $I 변수로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-121">This command imports only the **"Processor(_total)\Interrupts/sec"** counter data from the ProcessorData.blg file into the $I variable.</span></span>

### <span data-ttu-id="5f166-122">예제 3: 성능 카운터에서 데이터를 선택 하 고 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="5f166-122">Example 3: Select data from a performance counter then export it to a file</span></span>

```
The first command uses **Import-Counter** to import all of the performance counter data from the ProcessorData.blg files. The command saves the data in the $Data variable.
PS C:\> $Data = Import-Counter .\ProcessorData.blg

The second command displays the counter paths in the $Data variable. To get the display shown in the command output, the example uses the Format-Table cmdlet to format as a table the counter paths of the first counter in the $Data variable.
PS C:\> $Data[0].CounterSamples | Format-Table -Property Path

Path
----
\\SERVER01\Processor(_Total)\DPC Rate
\\SERVER01\Processor(1)\DPC Rate
\\SERVER01\Processor(0)\DPC Rate
\\SERVER01\Processor(_Total)\% Idle Time
\\SERVER01\Processor(1)\% Idle Time
\\SERVER01\Processor(0)\% Idle Time
\\SERVER01\Processor(_Total)\% C3 Time
\\SERVER01\Processor(1)\% C3 Time

The third command gets the counter paths that end in "Interrupts/sec" and saves the paths in the $IntCtrs variable. It uses the Where-Object cmdlet to filter the counter paths and the ForEach-Object cmdlet to get only the value of the **Path** property of each selected path object.
PS C:\> $IntCtrs = $Data[0].Countersamples | Where-Object {$_.Path -like "*Interrupts/sec"} | ForEach-Object {$_.Path}

The fourth command displays the selected counter paths in the $IntCtrs variable.
PS C:\> $IntCtrs

\\SERVER01\Processor(_Total)\Interrupts/sec
\\SERVER01\Processor(1)\Interrupts/sec
\\SERVER01\Processor(0)\Interrupts/sec

The fifth command uses the **Import-Counter** cmdlet to import the data. It uses the $IntCtrs variable as the value of the *Counter* parameter to import only data for the counter paths in $IntCtrs.
PS C:\> $I = Import-Counter -Path .\ProcessorData.blg -Counter $intCtrs

The sixth command uses the Export-Counter cmdlet to export the data to the Interrupts.csv file.
PS C:\> $I | Export-Counter -Path .\Interrupts.csv -Format CSV
```

<span data-ttu-id="5f166-123">이 예제에서는 성능 카운터 로그 파일(.blg)에서 데이터를 선택한 다음 선택한 데이터를 .csv 파일로 내보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-123">This example shows how to select data from a performance counter log file (.blg) and then export the selected data to a .csv file.</span></span>
<span data-ttu-id="5f166-124">처음 4 개 명령은 파일에서 카운터 경로를 가져와 $Data 라는 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-124">The first four commands get the counter paths from the file and save them in the variable named $Data.</span></span>
<span data-ttu-id="5f166-125">마지막 두 명령은 선택한 데이터를 가져온 다음 선택한 데이터만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-125">The last two commands import selected data and then export only the selected data.</span></span>

### <span data-ttu-id="5f166-126">예제 4: 가져온 카운터 집합 그룹의 모든 카운터 경로 표시</span><span class="sxs-lookup"><span data-stu-id="5f166-126">Example 4: Display all counter paths in a group of imported counter sets</span></span>

```
The first command uses the *ListSet* parameter of the **Import-Counter** cmdlet to get all of the counter sets that are represented in a counter data file.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet *

CounterSetName     : Processor
MachineName        : \\SERVER01
CounterSetType     : MultiInstance
Description        :
Paths              : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}
PathsWithInstances : {\\SERVER01\Processor(_Total)\DPC Rate, \\SERVER01\Processor(1)\DPC Rate, \\SERVER01
\Processor(0)\DPC Rate, \\SERVER01\Processor(_Total)\% Idle Time...}
Counter            : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}

The second command gets all of the counter paths from the list set.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet * | ForEach-Object {$_.Paths}

\\SERVER01\Processor(*)\DPC Rate
\\SERVER01\Processor(*)\% Idle Time
\\SERVER01\Processor(*)\% C3 Time
\\SERVER01\Processor(*)\% Interrupt Time
\\SERVER01\Processor(*)\% C2 Time
\\SERVER01\Processor(*)\% User Time
\\SERVER01\Processor(*)\% C1 Time
\\SERVER01\Processor(*)\% Processor Time
\\SERVER01\Processor(*)\C1 Transitions/sec
\\SERVER01\Processor(*)\% DPC Time
\\SERVER01\Processor(*)\C2 Transitions/sec
\\SERVER01\Processor(*)\% Privileged Time
\\SERVER01\Processor(*)\C3 Transitions/sec
\\SERVER01\Processor(*)\DPCs Queued/sec
\\SERVER01\Processor(*)\Interrupts/sec
```

<span data-ttu-id="5f166-127">이 예제에서는 가져온 카운터 집합 그룹에 있는 모든 카운터 경로를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-127">This example shows how to display all the counter paths in a group of imported counter sets.</span></span>

### <span data-ttu-id="5f166-128">예 5: 타임 스탬프 범위에서 카운터 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="5f166-128">Example 5: Import counter data from a range of time stamps</span></span>

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

<span data-ttu-id="5f166-129">이 예제에서는 타임스탬프가 명령에 지정된 시작 범위와 끝 범위 사이에 있는 카운터 데이터만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-129">This example imports only the counter data that has a time stamp between the starting an ending ranges specified in the command.</span></span>

### <span data-ttu-id="5f166-130">예 6: 성능 카운터 로그 파일에서 지정 된 수의 가장 오래 된 샘플 가져오기</span><span class="sxs-lookup"><span data-stu-id="5f166-130">Example 6: Import a specified number of the oldest samples from a performance counter log file</span></span>

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

<span data-ttu-id="5f166-131">이 예제에서는 성능 카운터 로그 파일에서 가장 오래된 샘플 5개와 최신 샘플 5개를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-131">This example shows how to import the five oldest and five newest samples from a performance counter log file.</span></span>

### <span data-ttu-id="5f166-132">예 7: 파일에서 카운터 데이터 요약 가져오기</span><span class="sxs-lookup"><span data-stu-id="5f166-132">Example 7: Get a summary of counter data from a file</span></span>

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

<span data-ttu-id="5f166-133">이 명령은 *Import-Counter* cmdlet의 **Summary** 매개 변수를 사용하여 Memory.blg 파일에 있는 카운터 데이터의 요약을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-133">This command uses the *Summary* parameter of the **Import-Counter** cmdlet to get a summary of the counter data in the Memory.blg file.</span></span>

### <span data-ttu-id="5f166-134">예 8: 성능 카운터 로그 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="5f166-134">Example 8: Update a performance counter log file</span></span>

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

<span data-ttu-id="5f166-135">이 예제에서는 성능 카운터 로그 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-135">This example updates a performance counter log file.</span></span>

### <span data-ttu-id="5f166-136">예 9: 여러 파일에서 성능 로그 데이터 가져오기 및 저장</span><span class="sxs-lookup"><span data-stu-id="5f166-136">Example 9: Import performance log data from multiple files and then save it</span></span>

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

<span data-ttu-id="5f166-137">이 명령은 두 개의 로그에서 성능 로그 데이터를 가져온 다음 데이터를 $Counters 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-137">This command imports performance log data from two logs and saves the data in the $Counters variable.</span></span>
<span data-ttu-id="5f166-138">파이프라인 연산자를 사용하여 성능 로그 경로를 Import-Counter로 보내면 이 명령이 지정한 경로에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-138">The command uses a pipeline operator to send the performance log paths to Import-Counter, which imports the data from the specified paths.</span></span>

<span data-ttu-id="5f166-139">각 경로는 따옴표로 묶여 있으며 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-139">Notice that each path is enclosed in quotation marks and that the paths are separated from each other by a comma.</span></span>

## <span data-ttu-id="5f166-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f166-140">PARAMETERS</span></span>

### <span data-ttu-id="5f166-141">-Counter</span><span class="sxs-lookup"><span data-stu-id="5f166-141">-Counter</span></span>

<span data-ttu-id="5f166-142">는 성능 카운터를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-142">Specifies, as a string array, the performance counters.</span></span>
<span data-ttu-id="5f166-143">기본적으로 **import-module** 은 입력 파일에 있는 모든 카운터의 모든 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-143">By default, **Import-Counter** imports all data from all counters in the input files.</span></span>
<span data-ttu-id="5f166-144">카운터 경로를 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-144">Enter one or more counter paths.</span></span>
<span data-ttu-id="5f166-145">경로의 인스턴스 부분에 와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-145">Wildcards are permitted in the Instance part of the path.</span></span>

<span data-ttu-id="5f166-146">각 카운터 경로의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-146">Each counter path has the following format.</span></span>
<span data-ttu-id="5f166-147">ComputerName 값은 경로에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-147">The ComputerName value is required in the path.</span></span>
<span data-ttu-id="5f166-148">예:</span><span class="sxs-lookup"><span data-stu-id="5f166-148">For instance:</span></span>

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

<span data-ttu-id="5f166-149">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="5f166-149">For example:</span></span>

- `\\Server01\Processor(2)\% User Time`
- `\\Server01\Processor(*)\% Processor Time`

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: All counter
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5f166-150">-EndTime</span><span class="sxs-lookup"><span data-stu-id="5f166-150">-EndTime</span></span>

<span data-ttu-id="5f166-151">이 cmdlet이 *StartTime* 및이 매개 변수 타임 스탬프 사이에서 카운터 데이터를 가져오는 종료 날짜와 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-151">Specifies an end date and time that this cmdlet imports counter data between the *StartTime* and this parameter timestamps.</span></span>
<span data-ttu-id="5f166-152">Get-Date cmdlet에 의해 생성 된 것과 같은 **DateTime** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-152">Enter a **DateTime** object, such as one created by the Get-Date cmdlet.</span></span>
<span data-ttu-id="5f166-153">기본적으로 **import-module** 은 *Path* 매개 변수로 지정 된 파일에 있는 모든 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-153">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No end time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f166-154">-ListSet</span><span class="sxs-lookup"><span data-stu-id="5f166-154">-ListSet</span></span>

<span data-ttu-id="5f166-155">내보낸 파일에 표시 되는 성능 카운터 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-155">Specifies the performance counter sets that are represented in the exported files.</span></span>
<span data-ttu-id="5f166-156">이 매개 변수를 사용한 명령은 데이터를 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-156">Commands with this parameter do not import any data.</span></span>

<span data-ttu-id="5f166-157">카운터 집합 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-157">Enter one or more counter set names.</span></span>
<span data-ttu-id="5f166-158">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-158">Wildcards are permitted.</span></span>
<span data-ttu-id="5f166-159">파일의 모든 카운터 집합을 가져오려면를 입력 `Import-Counter -ListSet *` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-159">To get all counter sets in the file, type `Import-Counter -ListSet *`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5f166-160">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="5f166-160">-MaxSamples</span></span>

<span data-ttu-id="5f166-161">가져올 각 카운터의 최대 샘플 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-161">Specifies the maximum number of samples of each counter to import.</span></span>
<span data-ttu-id="5f166-162">기본적으로 **Get 카운터** 는 *Path* 매개 변수로 지정 된 파일의 모든 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-162">By default, **Get-Counter** imports all of the data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No maximum
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f166-163">-Path</span><span class="sxs-lookup"><span data-stu-id="5f166-163">-Path</span></span>

<span data-ttu-id="5f166-164">가져올 파일의 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-164">Specifies the file paths of the files to be imported.</span></span>
<span data-ttu-id="5f166-165">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-165">This parameter is required.</span></span>

<span data-ttu-id="5f166-166">Tsv **cmdlet을 사용 하 여 내보낸** , .csv,,. 또는 .blg 파일의 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-166">Enter the path and file name of a, .csv,, .tsv, or .blg file that you exported by using the **Export-Counter** cmdlet.</span></span>
<span data-ttu-id="5f166-167">.csv 또는 .tsv 파일은 하나만 지정할 수 있지만 .blg 파일은 각 명령에서 여러 개(최대 32개)를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-167">You can specify only one .csv or .tsv file, but you can specify multiple .blg files (up to 32) in each command.</span></span>
<span data-ttu-id="5f166-168">파일 경로 문자열을 인용 부호로 파이프 하 여 **가져올** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-168">You can also pipe file path strings (in quotation marks) to **Import-Counter** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="5f166-169">-StartTime</span><span class="sxs-lookup"><span data-stu-id="5f166-169">-StartTime</span></span>

<span data-ttu-id="5f166-170">이 cmdlet이 카운터 데이터를 가져오는 시작 날짜와 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-170">Specifies the start date and time in which this cmdlet gets counter data.</span></span>
<span data-ttu-id="5f166-171">**날짜** **/시간** cmdlet에 의해 생성 된 것과 같은 DateTime 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-171">Enter a **DateTime** object, such as one created by the **Get-Date** cmdlet.</span></span>
<span data-ttu-id="5f166-172">기본적으로 **import-module** 은 *Path* 매개 변수로 지정 된 파일에 있는 모든 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-172">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No start time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f166-173">-요약</span><span class="sxs-lookup"><span data-stu-id="5f166-173">-Summary</span></span>

<span data-ttu-id="5f166-174">이 cmdlet은 개별 카운터 데이터 샘플을 가져오는 대신 가져온 데이터의 요약을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-174">Indicates that this cmdlet gets a summary of the imported data, instead of getting individual counter data samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SummarySet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f166-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f166-175">CommonParameters</span></span>

<span data-ttu-id="5f166-176">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f166-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f166-177">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f166-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f166-178">입력</span><span class="sxs-lookup"><span data-stu-id="5f166-178">INPUTS</span></span>

### <span data-ttu-id="5f166-179">System.String</span><span class="sxs-lookup"><span data-stu-id="5f166-179">System.String</span></span>

<span data-ttu-id="5f166-180">이 cmdlet에 대 한 성능 카운터 로그 경로를 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-180">You can pipe performance counter log paths to this cmdlet.</span></span>

## <span data-ttu-id="5f166-181">출력</span><span class="sxs-lookup"><span data-stu-id="5f166-181">OUTPUTS</span></span>

### <span data-ttu-id="5f166-182">PerformanceCounterSampleSet, Microsoft. powershell.. i.............</span><span class="sxs-lookup"><span data-stu-id="5f166-182">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo</span></span>

<span data-ttu-id="5f166-183">이 cmdlet은 **PerformanceCounterSampleSet** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-183">This cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet** .</span></span>
<span data-ttu-id="5f166-184">*Listset* 매개 변수를 사용 하는 경우이 Cmdlet은 **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="5f166-184">If you use the *ListSet* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterSet** object.</span></span>
<span data-ttu-id="5f166-185">*Summary* 매개 변수를 사용 하는 경우이 Cmdlet은 **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="5f166-185">If you use the *Summary* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo** object.</span></span>

## <span data-ttu-id="5f166-186">참고</span><span class="sxs-lookup"><span data-stu-id="5f166-186">NOTES</span></span>

* <span data-ttu-id="5f166-187">이 cmdlet에는 *ComputerName* 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-187">This cmdlet does not have a *ComputerName* parameter.</span></span> <span data-ttu-id="5f166-188">그러나 컴퓨터가 Windows PowerShell 원격을 사용 하도록 구성 된 경우에는 Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 **Import-Counter** 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f166-188">However, if the computer is configured for Windows PowerShell remoting, you can use the Invoke-Command cmdlet to run an **Import-Counter** command on a remote computer.</span></span>

## <span data-ttu-id="5f166-189">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5f166-189">RELATED LINKS</span></span>

[<span data-ttu-id="5f166-190">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="5f166-190">Export-Counter</span></span>](Export-Counter.md)

[<span data-ttu-id="5f166-191">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="5f166-191">Get-Counter</span></span>](Get-Counter.md)
