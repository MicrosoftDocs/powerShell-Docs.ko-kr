---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 5a0c197387f67dae1830b6d9ebd4145e96383b39
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224306"
---
# Write-Progress

## 개요
PowerShell 명령 창 내에 진행률 표시줄을 표시 합니다.

## SYNTAX

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## 설명

`Write-Progress`Cmdlet은 실행 중인 명령이 나 스크립트의 상태를 보여 주는 PowerShell 명령 창에 진행률 표시줄을 표시 합니다. 표시줄이 반영하는 표시기 및 진행률 표시줄 위/아래에 나타나는 텍스트를 선택할 수 있습니다.

## 예제

### 예제 1: For 루프의 진행률 표시

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

이 명령은 1부터 100까지의 For 루프 진행률을 표시합니다.

Cmdlet에는 `Write-Progress` `Activity` 작업의 상대 완전성을 나타내는 상태 표시줄 제목, 상태 줄 및 변수 `$i` (for 루프의 카운터)가 포함 됩니다.

### 예 2: 중첩 된 For 루프의 진행률 표시

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

이 예제에서는 각각 진행률 표시줄로 표시되는 중첩된 두 For 루프의 진행률을 표시합니다.

`Write-Progress`두 번째 진행률 표시줄의 명령은 첫 번째 진행률 표시줄과 구별 하는 **Id** 매개 변수를 포함 합니다.

**Id** 매개 변수를 사용 하지 않으면 진행률 표시줄이 서로 표시 되지 않고 서로 겹쳐서 표시 됩니다.

### 예제 3: 문자열을 검색 하는 동안 진행률 표시

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

이 명령은 시스템 이벤트 로그에서 "bios"라는 문자열을 찾는 명령의 진행률을 표시합니다.

**완료율** 매개 변수 값은 검색 된 총 이벤트 수에 의해 처리 된 이벤트 수를 나눈 `$I` `$Events.count` 다음 그 결과를 100로 곱하여 계산 합니다.

### 예 4: 중첩 된 프로세스의 각 수준에 대 한 진행률 표시

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

이 예에서는 **ParentId** 매개 변수를 사용 하 여 각 단계의 진행률에 부모/자식 관계를 표시 하도록 들여쓰기 된 출력을 포함할 수 있습니다.

## PARAMETERS

### -작업

상태 표시줄 위 제목의 첫 번째 텍스트 줄을 지정합니다.
이 텍스트는 진행률이 보고되는 있는 작업을 설명합니다.

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

### -완료 됨

진행률 표시줄이 표시되는지 여부를 나타냅니다.
이 매개 변수를 생략 하면에서 `Write-Progress` 진행률 정보를 표시 합니다.

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

### -CurrentOperation

진행률 표시줄 아래의 텍스트 줄을 지정합니다.
이 텍스트는 현재 발생하고 있는 작업을 설명합니다.

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

### -Id

각 진행률 표시줄을 다른 진행률 표시줄과 구별하는 ID를 지정합니다. 하나의 명령으로 여러 개의 진행률 표시줄을 만들 때 이 매개 변수를 사용합니다. 진행률 표시줄의 ID가 같으면 일렬로 표시되지 않고 겹쳐서 표시됩니다.

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

### -ParentId

현재 활동의 부모 활동을 지정 합니다.
현재 작업에 상위 작업이 없으면 -1 값을 사용합니다.

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

### -완료율

완료된 작업의 비율(백분율)을 지정합니다.
완료율을 알 수 없거나 해당 사항이 없으면 -1 값을 사용합니다.

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

### -SecondsRemaining

작업이 완료될 때까지 남아 있는 예상 시간(초)을 지정합니다.
남아 있는 시간(초)을 알 수 없거나 해당 사항이 없으면 -1 값을 사용합니다.

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

### -SourceId

레코드의 원본을 지정 합니다. **Id** 대신이 매개 변수를 사용할 수 있지만 **ParentId** 와 같은 다른 매개 변수와 함께 사용할 수는 없습니다.

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

### -상태

상태 표시줄 위 제목의 두 번째 텍스트 줄을 지정합니다.
이 텍스트는 작업의 현재 상태를 설명합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음

`Write-Progress` 는 출력을 생성 하지 않습니다.

## 참고

진행률 표시줄이 나타나지 않으면 변수의 값을 확인 `$ProgressPreference` 합니다. 값이 SilentlyContinue로 설정되어 있으면 진행률 표시줄이 표시되지 않습니다. PowerShell 기본 설정에 대 한 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

Cmdlet의 매개 변수는 **ProgressRecord** 클래스의 속성에 해당 합니다. 자세한 내용은 [ProgressRecord 클래스](/dotnet/api/system.management.automation.progressrecord)를 참조 하세요.

## 관련 링크

[Write-Debug](Write-Debug.md)

[쓰기 오류](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
