---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 2e2bd5474198745d72ad2b87c3c305695a198f22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601055"
---
# <span data-ttu-id="1b541-102">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="1b541-102">Write-Progress</span></span>

## <span data-ttu-id="1b541-103">개요</span><span class="sxs-lookup"><span data-stu-id="1b541-103">SYNOPSIS</span></span>
<span data-ttu-id="1b541-104">PowerShell 명령 창 내에 진행률 표시줄을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-104">Displays a progress bar within a PowerShell command window.</span></span>

## <span data-ttu-id="1b541-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b541-105">SYNTAX</span></span>

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="1b541-106">설명</span><span class="sxs-lookup"><span data-stu-id="1b541-106">DESCRIPTION</span></span>

<span data-ttu-id="1b541-107">`Write-Progress`Cmdlet은 실행 중인 명령이 나 스크립트의 상태를 보여 주는 PowerShell 명령 창에 진행률 표시줄을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-107">The `Write-Progress` cmdlet displays a progress bar in a PowerShell command window that depicts the status of a running command or script.</span></span> <span data-ttu-id="1b541-108">표시줄이 반영하는 표시기 및 진행률 표시줄 위/아래에 나타나는 텍스트를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-108">You can select the indicators that the bar reflects and the text that appears above and below the progress bar.</span></span>

## <span data-ttu-id="1b541-109">예제</span><span class="sxs-lookup"><span data-stu-id="1b541-109">EXAMPLES</span></span>

### <span data-ttu-id="1b541-110">예제 1: For 루프의 진행률 표시</span><span class="sxs-lookup"><span data-stu-id="1b541-110">Example 1: Display the progress of a For loop</span></span>

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

<span data-ttu-id="1b541-111">이 명령은 1부터 100까지의 For 루프 진행률을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-111">This command displays the progress of a For loop that counts from 1 to 100.</span></span>

<span data-ttu-id="1b541-112">Cmdlet에는 `Write-Progress` `Activity` 작업의 상대 완전성을 나타내는 상태 표시줄 제목, 상태 줄 및 변수 `$i` (for 루프의 카운터)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-112">The `Write-Progress` cmdlet includes a status bar heading `Activity`, a status line, and the variable `$i` (the counter in the For loop), which indicates the relative completeness of the task.</span></span>

### <span data-ttu-id="1b541-113">예 2: 중첩 된 For 루프의 진행률 표시</span><span class="sxs-lookup"><span data-stu-id="1b541-113">Example 2: Display the progress of nested For loops</span></span>

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

<span data-ttu-id="1b541-114">이 예제에서는 각각 진행률 표시줄로 표시되는 중첩된 두 For 루프의 진행률을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-114">This example displays the progress of two nested For loops, each of which is represented by a progress bar.</span></span>

<span data-ttu-id="1b541-115">`Write-Progress`두 번째 진행률 표시줄의 명령은 첫 번째 진행률 표시줄과 구별 하는 **Id** 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-115">The `Write-Progress` command for the second progress bar includes the **Id** parameter that distinguishes it from the first progress bar.</span></span>

<span data-ttu-id="1b541-116">**Id** 매개 변수를 사용 하지 않으면 진행률 표시줄이 서로 표시 되지 않고 서로 겹쳐서 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-116">Without the **Id** parameter, the progress bars would be superimposed on each other instead of being displayed one below the other.</span></span>

### <span data-ttu-id="1b541-117">예제 3: 문자열을 검색 하는 동안 진행률 표시</span><span class="sxs-lookup"><span data-stu-id="1b541-117">Example 3: Display the progress while searching for a string</span></span>

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

<span data-ttu-id="1b541-118">이 명령은 시스템 이벤트 로그에서 "bios"라는 문자열을 찾는 명령의 진행률을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-118">This command displays the progress of a command to find the string "bios" in the System event log.</span></span>

<span data-ttu-id="1b541-119">**완료율** 매개 변수 값은 검색 된 총 이벤트 수에 의해 처리 된 이벤트 수를 나눈 `$I` `$Events.count` 다음 그 결과를 100로 곱하여 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-119">The **PercentComplete** parameter value is calculated by dividing the number of events that have been processed `$I` by the total number of events retrieved `$Events.count` and then multiplying that result by 100.</span></span>

### <span data-ttu-id="1b541-120">예 4: 중첩 된 프로세스의 각 수준에 대 한 진행률 표시</span><span class="sxs-lookup"><span data-stu-id="1b541-120">Example 4: Display progress for each level of a nested process</span></span>

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

<span data-ttu-id="1b541-121">이 예에서는 **ParentId** 매개 변수를 사용 하 여 각 단계의 진행률에 부모/자식 관계를 표시 하도록 들여쓰기 된 출력을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-121">In this example you can use the **ParentId** parameter to have indented output to show parent/child relationships in the progress of each step.</span></span>

## <span data-ttu-id="1b541-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b541-122">PARAMETERS</span></span>

### <span data-ttu-id="1b541-123">-작업</span><span class="sxs-lookup"><span data-stu-id="1b541-123">-Activity</span></span>

<span data-ttu-id="1b541-124">상태 표시줄 위 제목의 첫 번째 텍스트 줄을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-124">Specifies the first line of text in the heading above the status bar.</span></span>
<span data-ttu-id="1b541-125">이 텍스트는 진행률이 보고되는 있는 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-125">This text describes the activity whose progress is being reported.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-126">-완료 됨</span><span class="sxs-lookup"><span data-stu-id="1b541-126">-Completed</span></span>

<span data-ttu-id="1b541-127">진행률 표시줄이 표시되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-127">Indicates whether the progress bar is visible.</span></span>
<span data-ttu-id="1b541-128">이 매개 변수를 생략 하면에서 `Write-Progress` 진행률 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-128">If this parameter is omitted, `Write-Progress` displays progress information.</span></span>

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

### <span data-ttu-id="1b541-129">-CurrentOperation</span><span class="sxs-lookup"><span data-stu-id="1b541-129">-CurrentOperation</span></span>

<span data-ttu-id="1b541-130">진행률 표시줄 아래의 텍스트 줄을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-130">Specifies the line of text below the progress bar.</span></span>
<span data-ttu-id="1b541-131">이 텍스트는 현재 발생하고 있는 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-131">This text describes the operation that is currently taking place.</span></span>

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

### <span data-ttu-id="1b541-132">-Id</span><span class="sxs-lookup"><span data-stu-id="1b541-132">-Id</span></span>

<span data-ttu-id="1b541-133">각 진행률 표시줄을 다른 진행률 표시줄과 구별하는 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-133">Specifies an ID that distinguishes each progress bar from the others.</span></span> <span data-ttu-id="1b541-134">하나의 명령으로 여러 개의 진행률 표시줄을 만들 때 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-134">Use this parameter when you are creating more than one progress bar in a single command.</span></span> <span data-ttu-id="1b541-135">진행률 표시줄의 ID가 같으면 일렬로 표시되지 않고 겹쳐서 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-135">If the progress bars do not have different IDs, they are superimposed instead of being displayed in a series.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-136">-ParentId</span><span class="sxs-lookup"><span data-stu-id="1b541-136">-ParentId</span></span>

<span data-ttu-id="1b541-137">현재 활동의 부모 활동을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-137">Specifies the parent activity of the current activity.</span></span>
<span data-ttu-id="1b541-138">현재 작업에 상위 작업이 없으면 -1 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-138">Use the value -1 if the current activity has no parent activity.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-139">-완료율</span><span class="sxs-lookup"><span data-stu-id="1b541-139">-PercentComplete</span></span>

<span data-ttu-id="1b541-140">완료된 작업의 비율(백분율)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-140">Specifies the percentage of the activity that is completed.</span></span>
<span data-ttu-id="1b541-141">완료율을 알 수 없거나 해당 사항이 없으면 -1 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-141">Use the value -1 if the percentage complete is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-142">-SecondsRemaining</span><span class="sxs-lookup"><span data-stu-id="1b541-142">-SecondsRemaining</span></span>

<span data-ttu-id="1b541-143">작업이 완료될 때까지 남아 있는 예상 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-143">Specifies the projected number of seconds remaining until the activity is completed.</span></span>
<span data-ttu-id="1b541-144">남아 있는 시간(초)을 알 수 없거나 해당 사항이 없으면 -1 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-144">Use the value -1 if the number of seconds remaining is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-145">-SourceId</span><span class="sxs-lookup"><span data-stu-id="1b541-145">-SourceId</span></span>

<span data-ttu-id="1b541-146">레코드의 원본을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-146">Specifies the source of the record.</span></span> <span data-ttu-id="1b541-147">**Id** 대신이 매개 변수를 사용할 수 있지만 **ParentId** 와 같은 다른 매개 변수와 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-147">You can use this in place of **Id** but cannot be used with other parameters like **ParentId**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-148">-상태</span><span class="sxs-lookup"><span data-stu-id="1b541-148">-Status</span></span>

<span data-ttu-id="1b541-149">상태 표시줄 위 제목의 두 번째 텍스트 줄을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-149">Specifies the second line of text in the heading above the status bar.</span></span>
<span data-ttu-id="1b541-150">이 텍스트는 작업의 현재 상태를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-150">This text describes current state of the activity.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b541-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b541-151">CommonParameters</span></span>

<span data-ttu-id="1b541-152">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b541-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b541-153">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b541-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1b541-154">입력</span><span class="sxs-lookup"><span data-stu-id="1b541-154">INPUTS</span></span>

### <span data-ttu-id="1b541-155">없음</span><span class="sxs-lookup"><span data-stu-id="1b541-155">None</span></span>

<span data-ttu-id="1b541-156">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-156">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1b541-157">출력</span><span class="sxs-lookup"><span data-stu-id="1b541-157">OUTPUTS</span></span>

### <span data-ttu-id="1b541-158">없음</span><span class="sxs-lookup"><span data-stu-id="1b541-158">None</span></span>

<span data-ttu-id="1b541-159">`Write-Progress` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-159">`Write-Progress` does not generate any output.</span></span>

## <span data-ttu-id="1b541-160">참고</span><span class="sxs-lookup"><span data-stu-id="1b541-160">NOTES</span></span>

<span data-ttu-id="1b541-161">진행률 표시줄이 나타나지 않으면 변수의 값을 확인 `$ProgressPreference` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-161">If the progress bar does not appear, check the value of the `$ProgressPreference` variable.</span></span> <span data-ttu-id="1b541-162">값이 SilentlyContinue로 설정되어 있으면 진행률 표시줄이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-162">If the value is set to SilentlyContinue, the progress bar is not displayed.</span></span> <span data-ttu-id="1b541-163">PowerShell 기본 설정에 대 한 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b541-163">For more information about PowerShell preferences, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="1b541-164">Cmdlet의 매개 변수는 **ProgressRecord** 클래스의 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b541-164">The parameters of the cmdlet correspond to the properties of the **System.Management.Automation.ProgressRecord** class.</span></span> <span data-ttu-id="1b541-165">자세한 내용은 [ProgressRecord 클래스](/dotnet/api/system.management.automation.progressrecord)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b541-165">For more information, see [ProgressRecord Class](/dotnet/api/system.management.automation.progressrecord).</span></span>

## <span data-ttu-id="1b541-166">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1b541-166">RELATED LINKS</span></span>

[<span data-ttu-id="1b541-167">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="1b541-167">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="1b541-168">Write-Error</span><span class="sxs-lookup"><span data-stu-id="1b541-168">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="1b541-169">Write-Host</span><span class="sxs-lookup"><span data-stu-id="1b541-169">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="1b541-170">Write-Output</span><span class="sxs-lookup"><span data-stu-id="1b541-170">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="1b541-171">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="1b541-171">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="1b541-172">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="1b541-172">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="1b541-173">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="1b541-173">Write-Warning</span></span>](Write-Warning.md)
