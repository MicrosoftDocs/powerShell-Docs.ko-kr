---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220777"
---
# <span data-ttu-id="cd289-103">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="cd289-103">Export-Counter</span></span>

## <span data-ttu-id="cd289-104">개요</span><span class="sxs-lookup"><span data-stu-id="cd289-104">SYNOPSIS</span></span>
<span data-ttu-id="cd289-105">성능 카운터 데이터를 로그 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-105">Exports performance counter data to log files.</span></span>

## <span data-ttu-id="cd289-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd289-106">SYNTAX</span></span>

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## <span data-ttu-id="cd289-107">설명</span><span class="sxs-lookup"><span data-stu-id="cd289-107">DESCRIPTION</span></span>

<span data-ttu-id="cd289-108">`Export-Counter`Cmdlet은 성능 카운터 데이터 (PerformanceCounterSampleSet 개체)를 이진 성능 로그 (.blg), 쉼표로 구분 된 값 (.csv) 또는 탭으로 구분 된 값 (. tsv) 형식의 로그 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-108">The `Export-Counter` cmdlet exports performance counter data (PerformanceCounterSampleSet objects) to log files in binary performance log (.blg), comma-separated value (.csv), or tab-separated value (.tsv) format.</span></span> <span data-ttu-id="cd289-109">이 cmdlet을 사용 하 여 성능 카운터 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-109">You use this cmdlet to log performance counter data.</span></span>

<span data-ttu-id="cd289-110">`Export-Counter`Cmdlet은 및 cmdlet에 의해 반환 되는 데이터를 내보내도록 설계 되었습니다 `Get-Counter` `Import-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-110">The `Export-Counter` cmdlet is designed to export data that is returned by the `Get-Counter` and `Import-Counter` cmdlets.</span></span>

<span data-ttu-id="cd289-111">이 cmdlet은 windows 7, Windows Server 2008 R2 및 이후 버전의 Windows 에서만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-111">This cmdlet runs only on Windows 7, Windows Server 2008 R2, and later versions of Windows.</span></span>

## <span data-ttu-id="cd289-112">예제</span><span class="sxs-lookup"><span data-stu-id="cd289-112">EXAMPLES</span></span>

### <span data-ttu-id="cd289-113">예제 1: 카운터 데이터를 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="cd289-113">EXAMPLE 1: Export counter data to a file</span></span>

<span data-ttu-id="cd289-114">이 예제에서는 카운터 데이터를 .BLG 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-114">This example exports counter data to a BLG file.</span></span>

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

<span data-ttu-id="cd289-115">이 명령은 cmdlet을 사용 하 여 `Get-Counter` 프로세서 시간 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-115">The command uses the `Get-Counter` cmdlet to collect processor time data.</span></span> <span data-ttu-id="cd289-116">파이프라인 연산자 (|)를 사용 하 여 cmdlet에 데이터를 보냅니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-116">It uses a pipeline operator (|) to send the data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="cd289-117">이 `Export-Counter` 명령은 **Path** 변수를 사용 하 여 출력 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-117">The `Export-Counter` command uses the **Path** variable to specify the output file.</span></span>

<span data-ttu-id="cd289-118">데이터 집합이 매우 클 수 있기 때문에이 예제에서는 파이프라인을 통해 데이터를로 보냅니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-118">Because the data set might be very large, this example sends the data to `Export-Counter` through the pipeline.</span></span> <span data-ttu-id="cd289-119">데이터를 변수에 저장 한 경우에는 불균형 크기의 메모리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-119">If the data were saved in a variable, you might use a disproportionate amount of memory.</span></span>

### <span data-ttu-id="cd289-120">예제 2: 파일을 카운터 파일 형식으로 내보내기</span><span class="sxs-lookup"><span data-stu-id="cd289-120">Example 2: Export a file to a counter file format</span></span>

<span data-ttu-id="cd289-121">이 예에서는 CSV 파일을 카운터 데이터 .BLG 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-121">This example converts a CSV file to a counter data BLG format.</span></span>

<span data-ttu-id="cd289-122">`Import-Counter`Cmdlet은 파일에서 성능 카운터 데이터를 가져옵니다 `Threads.csv` .</span><span class="sxs-lookup"><span data-stu-id="cd289-122">The `Import-Counter` cmdlet imports performance counter data from the `Threads.csv` file.</span></span> <span data-ttu-id="cd289-123">이 예에서는 cmdlet을 사용 하 여이 파일을 이전에 내보낸 것으로 가정 합니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-123">The example presumes that this file was previously exported by using the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="cd289-124">파이프라인 연산자 ( `|` )는 가져온 데이터를 cmdlet으로 보냅니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-124">A pipeline operator (`|`) sends the imported data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="cd289-125">이 명령은 **Path** 매개 변수를 사용하여 출력 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-125">The command uses the **Path** parameter to specify the location of the output file.</span></span> <span data-ttu-id="cd289-126">이 cmdlet은 **순환** 및 **MaxSize** 매개 변수를 사용 하 여 cmdlet이 1gb로 `Export-Counter` 래핑하는 순환 로그를 만들도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-126">It uses the **Circular** and **MaxSize** parameters to direct the `Export-Counter` cmdlet to create a circular log that wraps at 1 GB.</span></span> <span data-ttu-id="cd289-127">**MaxSize** 매개 변수는 메가바이트 단위로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-127">The **MaxSize** parameter is expressed in megabytes.</span></span>

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### <span data-ttu-id="cd289-128">예 3: 원격 컴퓨터에서 카운터 데이터 가져오기 및 파일에 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="cd289-128">Example 3: Get counter data from a remote computer and save the data to a file</span></span>

<span data-ttu-id="cd289-129">이 예제에서는 원격 컴퓨터에서 성능 카운터 데이터를 가져와 원격 컴퓨터의 파일에 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-129">This example shows how to get performance counter data from a remote computer and save the data in a file on the remote computer.</span></span>

<span data-ttu-id="cd289-130">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Counter` 원격 컴퓨터인 Server01에서 작업 집합 카운터 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-130">The first command uses the `Get-Counter` cmdlet to collect working set counter data from Server01, a remote computer.</span></span> <span data-ttu-id="cd289-131">이 명령은 데이터를 `$C` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-131">The command saves the data in the `$C` variable.</span></span>

<span data-ttu-id="cd289-132">두 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 데이터를 `$C` cmdlet으로 전송 합니다. 그러면 `Export-Counter` 이 cmdlet이 `Workingset.blg` Server01 컴퓨터의 성능 공유에 있는 파일에 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-132">The second command uses a pipeline operator (`|`) to send the data in `$C` to the `Export-Counter` cmdlet, which saves it in the `Workingset.blg` file in the Perf share of the Server01 computer.</span></span>

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### <span data-ttu-id="cd289-133">예제 4: 기존 데이터 다시 로그</span><span class="sxs-lookup"><span data-stu-id="cd289-133">Example 4: Re-log existing data</span></span>

<span data-ttu-id="cd289-134">이 예제에서는 및 cmdlet을 사용 하 여 `Import-Counter` 기존 데이터를 다시 로그 하는 방법을 보여 줍니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-134">This example shows how to use the `Import-Counter` and `Export-Counter` cmdlets to re-log existing data.</span></span>

<span data-ttu-id="cd289-135">첫 번째 명령은 cmdlet을 사용 하 여 `Import-Counter` DiskSpace 로그에서 성능 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-135">The first command uses the `Import-Counter` cmdlet to import performance counter data from the DiskSpace.blg log.</span></span> <span data-ttu-id="cd289-136">변수에 데이터를 저장 `$All` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-136">It saves the data in the `$All` variable.</span></span> <span data-ttu-id="cd289-137">이 파일에는 \% 기업에서 200 대 이상의 원격 컴퓨터에 있는 "논리 디스크 Free Space" 카운터 샘플이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-137">This file contains samples of the "LogicalDisk\% Free Space" counter on more than 200 remote computers in the enterprise.</span></span>

<span data-ttu-id="cd289-138">두 번째 명령은 cmdlet을 사용 하 여 `Where-Object` 15 (%) 보다 작은 **CookedValue** 의 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-138">The second command uses the `Where-Object` cmdlet to select objects with **CookedValue** of less than 15 (percent).</span></span> <span data-ttu-id="cd289-139">이 명령은 결과를 `$LowSpace` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-139">The command saves the results in the `$LowSpace` variable.</span></span>

<span data-ttu-id="cd289-140">세 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 변수의 데이터를 `$LowSpace` cmdlet으로 보냅니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-140">The third command uses a pipeline operator (`|`) to send the data in the `$LowSpace` variable to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="cd289-141">이 명령은 **Path** 매개 변수를 사용하여 선택한 데이터가 LowDiskSpace.blg 파일에 기록되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-141">The command uses the **Path** parameter to indicate that the selected data should be logged in the LowDiskSpace.blg file.</span></span>

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## <span data-ttu-id="cd289-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd289-142">PARAMETERS</span></span>

### <span data-ttu-id="cd289-143">-순환</span><span class="sxs-lookup"><span data-stu-id="cd289-143">-Circular</span></span>

<span data-ttu-id="cd289-144">출력 파일이 FIFO (선입 선출) 형식을 사용 하는 순환 로그 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-144">Indicates that the output file is a circular log with first in, first out (FIFO) format.</span></span>
<span data-ttu-id="cd289-145">이 매개 변수를 포함하는 경우 **MaxSize** 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-145">When you include this parameter, the **MaxSize** parameter is required.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd289-146">-FileFormat</span><span class="sxs-lookup"><span data-stu-id="cd289-146">-FileFormat</span></span>

<span data-ttu-id="cd289-147">출력 로그 파일의 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-147">Specifies the output format of the output log file.</span></span>

<span data-ttu-id="cd289-148">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cd289-149">CSV</span><span class="sxs-lookup"><span data-stu-id="cd289-149">CSV</span></span>
- <span data-ttu-id="cd289-150">TSV</span><span class="sxs-lookup"><span data-stu-id="cd289-150">TSV</span></span>
- <span data-ttu-id="cd289-151">BLG</span><span class="sxs-lookup"><span data-stu-id="cd289-151">BLG</span></span>

<span data-ttu-id="cd289-152">기본값은 BLG입니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-152">The default value is BLG.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd289-153">-Force</span><span class="sxs-lookup"><span data-stu-id="cd289-153">-Force</span></span>

<span data-ttu-id="cd289-154">**Path** 매개 변수에 지정 된 위치에 존재 하는 경우 기존 파일을 덮어쓰고 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-154">Overwrites and replaces an existing file if one exists in the location specified by the **Path** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd289-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cd289-155">-InputObject</span></span>

<span data-ttu-id="cd289-156">내보낼 카운터 데이터를 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-156">Specifies, as an array, the counter data to export.</span></span> <span data-ttu-id="cd289-157">데이터를 포함 하는 변수 또는 데이터를 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `Get-Counter` `Import-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-157">Enter a variable that contains the data or a command that gets the data, such as the `Get-Counter` or `Import-Counter` cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cd289-158">-MaxSize</span><span class="sxs-lookup"><span data-stu-id="cd289-158">-MaxSize</span></span>

<span data-ttu-id="cd289-159">출력 파일의 최대 크기 (mb)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-159">Specifies the maximum size of the output file in megabytes (MB).</span></span>

<span data-ttu-id="cd289-160">**순환** 매개 변수가 지정 된 경우 로그 파일이 지정 된 최대 크기에 도달 하면 새 항목이 추가 될 때 가장 오래 된 항목이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-160">If the **Circular** parameter is specified, then when the log file reaches the specified maximum size, the oldest entries are deleted as newer ones are added.</span></span> <span data-ttu-id="cd289-161">**순환** 매개 변수가 지정 되지 않은 경우 로그 파일이 지정 된 최대 크기에 도달 하면 새 데이터가 추가 되지 않고 cmdlet에서 종료 되지 않는 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-161">If the **Circular** parameter is not specified, then when the log file reaches the specified maximum size, no new data is added and the cmdlet generates a non-terminating error.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd289-162">-Path</span><span class="sxs-lookup"><span data-stu-id="cd289-162">-Path</span></span>

<span data-ttu-id="cd289-163">출력 파일의 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-163">Specifies the path and file name of the output file.</span></span> <span data-ttu-id="cd289-164">로컬 컴퓨터에 상대 또는 절대 경로를 입력 하거나와 같은 원격 컴퓨터에 대 한 UNC (Uniform 명명 규칙) 경로를 입력 `\\Computer\Share\file.blg` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-164">Enter a relative or absolute path on the local computer, or a Uniform Naming Convention (UNC) path to a remote computer, such as `\\Computer\Share\file.blg`.</span></span> <span data-ttu-id="cd289-165">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-165">This parameter is required.</span></span>

<span data-ttu-id="cd289-166">파일 형식은 경로에서 파일 이름 확장명이 아닌 **FileFormat** 매개 변수의 값에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-166">The file format is determined by the value of the **FileFormat** parameter, not by the file name extension in the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cd289-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd289-167">CommonParameters</span></span>

<span data-ttu-id="cd289-168">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd289-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd289-169">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd289-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd289-170">입력</span><span class="sxs-lookup"><span data-stu-id="cd289-170">INPUTS</span></span>

### <span data-ttu-id="cd289-171">PerformanceCounterSampleSet. GetCounter.</span><span class="sxs-lookup"><span data-stu-id="cd289-171">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet</span></span>

<span data-ttu-id="cd289-172">`Get-Counter`또는이 cmdlet에서 성능 카운터 데이터를 파이프 할 수 있습니다 `Import-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-172">You can pipe performance counter data from `Get-Counter` or `Import-Counter` to this cmdlet.</span></span>

## <span data-ttu-id="cd289-173">출력</span><span class="sxs-lookup"><span data-stu-id="cd289-173">OUTPUTS</span></span>

### <span data-ttu-id="cd289-174">없음</span><span class="sxs-lookup"><span data-stu-id="cd289-174">None</span></span>

## <span data-ttu-id="cd289-175">참고</span><span class="sxs-lookup"><span data-stu-id="cd289-175">NOTES</span></span>

<span data-ttu-id="cd289-176">로그 파일 생성기에서는 모든 입력 개체의 카운터 경로가 동일하며 개체가 오름차순으로 정렬되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-176">The log file generator expects that all input objects have the same counter path and that the objects are arranged in ascending time order.</span></span>

<span data-ttu-id="cd289-177">첫 번째 입력 개체의 카운터 유형 및 경로가 로그 파일에 기록되는 속성을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-177">The counter type and path of the first input object determines the properties recorded in the log file.</span></span> <span data-ttu-id="cd289-178">다른 입력 개체에 기록된 속성 값이 없으면 속성 필드는 비게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-178">If other input objects do not have a value for a recorded property, the property field is empty.</span></span> <span data-ttu-id="cd289-179">해당 개체에 기록되지 않은 속성 값이 있으면 추가 속성 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-179">If the objects have property values that were not recorded, the extra property values are ignored.</span></span>

<span data-ttu-id="cd289-180">성능 모니터에서 생성 하는 모든 로그를 읽지 못할 수 있습니다 `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="cd289-180">Performance Monitor might not be able to read all logs that `Export-Counter` generates.</span></span> <span data-ttu-id="cd289-181">예를 들어 성능 모니터에서는 모든 개체의 경로가 동일 하며 모든 개체가 동일한 시간 간격으로 분리 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-181">For instance, Performance Monitor requires that all objects have the same path and that all objects are separated by the same time interval.</span></span>

<span data-ttu-id="cd289-182">`Import-Counter`Cmdlet에 **ComputerName** 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-182">The `Import-Counter` cmdlet does not have a **ComputerName** parameter.</span></span> <span data-ttu-id="cd289-183">그러나 컴퓨터가 원격 Windows PowerShell Windows PowerShell 용으로 구성 된 경우에는 cmdlet을 사용 `Invoke-Command` 하 여 `Import-Counter` 원격 컴퓨터에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd289-183">However, if the computer is configured for remote Windows PowerShell Windows PowerShell, you can use the `Invoke-Command` cmdlet to run an `Import-Counter` command on a remote computer.</span></span>

## <span data-ttu-id="cd289-184">관련 링크</span><span class="sxs-lookup"><span data-stu-id="cd289-184">RELATED LINKS</span></span>

[<span data-ttu-id="cd289-185">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="cd289-185">Get-Counter</span></span>](Get-Counter.md)

[<span data-ttu-id="cd289-186">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="cd289-186">Import-Counter</span></span>](Import-Counter.md)
