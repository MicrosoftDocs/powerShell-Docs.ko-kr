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
# Import-Counter

## 개요
성능 카운터 로그 파일을 가져오고 로그의 각 카운터 샘플을 나타내는 개체를 만듭니다.

## SYNTAX

### GetCounterSet (기본값)

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### ListSetSet

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### 요약 집합

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## 설명

**Import-module** cmdlet은 성능 카운터 로그 파일에서 성능 카운터 데이터를 가져오고 파일의 각 카운터 샘플에 대 한 개체를 만듭니다.
생성 되는 **PerformanceCounterSampleSet** 개체는 성능 카운터 데이터를 수집할 때 **Get Counter** 에서 반환 하는 개체와 동일 합니다.

쉼표로 구분된 값(.csv), 탭으로 구분된 값( .tsv) 및 이진 성능 로그(.blg) 성능 로그 파일에서 데이터를 가져올 수 있습니다.
.Blg 파일을 사용 하는 경우 각 명령에서 최대 32 개의 파일을 가져올 수 있습니다.
Import **-Counter** 의 매개 변수를 사용 하 여 가져온 데이터를 필터링 할 수 있습니다.

Get-Counter 및 Export-Counter cmdlet과 함께이 기능을 사용 하면 Windows PowerShell 내에서 성능 카운터 데이터를 수집 하 고, 내보내고, 가져오고, 결합 하 고, 필터링 하 고, 조작 하 고, 다시 내보낼 수 있습니다.

## 예제

### 예제 1: 파일에서 모든 카운터 데이터 가져오기

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

이 명령은 ProcessorData.csv 파일에서 $Data 변수로 모든 카운터 데이터를 가져옵니다.

### 예제 2: 파일에서 특정 카운터 데이터 가져오기

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

이 명령은 Processordata.csv 파일의 **"Processor (_total) \ 인터럽트/sec"** 카운터 데이터만 $I 변수로 가져옵니다.

### 예제 3: 성능 카운터에서 데이터를 선택 하 고 파일로 내보내기

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

이 예제에서는 성능 카운터 로그 파일(.blg)에서 데이터를 선택한 다음 선택한 데이터를 .csv 파일로 내보내는 방법을 보여 줍니다.
처음 4 개 명령은 파일에서 카운터 경로를 가져와 $Data 라는 변수에 저장 합니다.
마지막 두 명령은 선택한 데이터를 가져온 다음 선택한 데이터만 내보냅니다.

### 예제 4: 가져온 카운터 집합 그룹의 모든 카운터 경로 표시

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

이 예제에서는 가져온 카운터 집합 그룹에 있는 모든 카운터 경로를 표시하는 방법을 보여 줍니다.

### 예 5: 타임 스탬프 범위에서 카운터 데이터 가져오기

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

이 예제에서는 타임스탬프가 명령에 지정된 시작 범위와 끝 범위 사이에 있는 카운터 데이터만 가져옵니다.

### 예 6: 성능 카운터 로그 파일에서 지정 된 수의 가장 오래 된 샘플 가져오기

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

이 예제에서는 성능 카운터 로그 파일에서 가장 오래된 샘플 5개와 최신 샘플 5개를 가져오는 방법을 보여 줍니다.

### 예 7: 파일에서 카운터 데이터 요약 가져오기

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

이 명령은 *Import-Counter* cmdlet의 **Summary** 매개 변수를 사용하여 Memory.blg 파일에 있는 카운터 데이터의 요약을 가져옵니다.

### 예 8: 성능 카운터 로그 파일 업데이트

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

이 예제에서는 성능 카운터 로그 파일을 업데이트합니다.

### 예 9: 여러 파일에서 성능 로그 데이터 가져오기 및 저장

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

이 명령은 두 개의 로그에서 성능 로그 데이터를 가져온 다음 데이터를 $Counters 변수에 저장합니다.
파이프라인 연산자를 사용하여 성능 로그 경로를 Import-Counter로 보내면 이 명령이 지정한 경로에서 데이터를 가져옵니다.

각 경로는 따옴표로 묶여 있으며 쉼표로 구분됩니다.

## PARAMETERS

### -Counter

는 성능 카운터를 문자열 배열로 지정 합니다.
기본적으로 **import-module** 은 입력 파일에 있는 모든 카운터의 모든 데이터를 가져옵니다.
카운터 경로를 하나 이상 입력합니다.
경로의 인스턴스 부분에 와일드카드가 지원됩니다.

각 카운터 경로의 형식은 다음과 같습니다.
ComputerName 값은 경로에 필요 합니다.
예:

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

다음은 그 예입니다. 

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

### -EndTime

이 cmdlet이 *StartTime* 및이 매개 변수 타임 스탬프 사이에서 카운터 데이터를 가져오는 종료 날짜와 시간을 지정 합니다.
Get-Date cmdlet에 의해 생성 된 것과 같은 **DateTime** 개체를 입력 합니다.
기본적으로 **import-module** 은 *Path* 매개 변수로 지정 된 파일에 있는 모든 카운터 데이터를 가져옵니다.

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

### -ListSet

내보낸 파일에 표시 되는 성능 카운터 집합을 지정 합니다.
이 매개 변수를 사용한 명령은 데이터를 가져오지 않습니다.

카운터 집합 이름을 하나 이상 입력합니다.
와일드카드가 지원됩니다.
파일의 모든 카운터 집합을 가져오려면를 입력 `Import-Counter -ListSet *` 합니다.

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

### -MaxSamples

가져올 각 카운터의 최대 샘플 수를 지정합니다.
기본적으로 **Get 카운터** 는 *Path* 매개 변수로 지정 된 파일의 모든 데이터를 가져옵니다.

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

### -Path

가져올 파일의 파일 경로를 지정합니다.
이 매개 변수는 필수적 요소입니다.

Tsv **cmdlet을 사용 하 여 내보낸** , .csv,,. 또는 .blg 파일의 경로와 파일 이름을 입력 합니다.
.csv 또는 .tsv 파일은 하나만 지정할 수 있지만 .blg 파일은 각 명령에서 여러 개(최대 32개)를 지정할 수 있습니다.
파일 경로 문자열을 인용 부호로 파이프 하 여 **가져올** 수 있습니다.

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

### -StartTime

이 cmdlet이 카운터 데이터를 가져오는 시작 날짜와 시간을 지정 합니다.
**날짜** **/시간** cmdlet에 의해 생성 된 것과 같은 DateTime 개체를 입력 합니다.
기본적으로 **import-module** 은 *Path* 매개 변수로 지정 된 파일에 있는 모든 카운터 데이터를 가져옵니다.

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

### -요약

이 cmdlet은 개별 카운터 데이터 샘플을 가져오는 대신 가져온 데이터의 요약을 가져옵니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 성능 카운터 로그 경로를 파이프 할 수 있습니다.

## 출력

### PerformanceCounterSampleSet, Microsoft. powershell.. i.............

이 cmdlet은 **PerformanceCounterSampleSet** 를 반환 합니다.
*Listset* 매개 변수를 사용 하는 경우이 Cmdlet은 **Microsoft. PowerShell** .
*Summary* 매개 변수를 사용 하는 경우이 Cmdlet은 **Microsoft. PowerShell** .

## 참고

* 이 cmdlet에는 *ComputerName* 매개 변수가 없습니다. 그러나 컴퓨터가 Windows PowerShell 원격을 사용 하도록 구성 된 경우에는 Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 **Import-Counter** 명령을 실행할 수 있습니다.

## 관련 링크

[Export-Counter](Export-Counter.md)

[Get-Counter](Get-Counter.md)
