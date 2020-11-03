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
# Export-Counter

## 개요
성능 카운터 데이터를 로그 파일로 내보냅니다.

## SYNTAX

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## 설명

`Export-Counter`Cmdlet은 성능 카운터 데이터 (PerformanceCounterSampleSet 개체)를 이진 성능 로그 (.blg), 쉼표로 구분 된 값 (.csv) 또는 탭으로 구분 된 값 (. tsv) 형식의 로그 파일로 내보냅니다. 이 cmdlet을 사용 하 여 성능 카운터 데이터를 기록 합니다.

`Export-Counter`Cmdlet은 및 cmdlet에 의해 반환 되는 데이터를 내보내도록 설계 되었습니다 `Get-Counter` `Import-Counter` .

이 cmdlet은 windows 7, Windows Server 2008 R2 및 이후 버전의 Windows 에서만 실행 됩니다.

## 예제

### 예제 1: 카운터 데이터를 파일로 내보내기

이 예제에서는 카운터 데이터를 .BLG 파일로 내보냅니다.

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

이 명령은 cmdlet을 사용 하 여 `Get-Counter` 프로세서 시간 데이터를 수집 합니다. 파이프라인 연산자 (|)를 사용 하 여 cmdlet에 데이터를 보냅니다 `Export-Counter` . 이 `Export-Counter` 명령은 **Path** 변수를 사용 하 여 출력 파일을 지정 합니다.

데이터 집합이 매우 클 수 있기 때문에이 예제에서는 파이프라인을 통해 데이터를로 보냅니다 `Export-Counter` . 데이터를 변수에 저장 한 경우에는 불균형 크기의 메모리를 사용할 수 있습니다.

### 예제 2: 파일을 카운터 파일 형식으로 내보내기

이 예에서는 CSV 파일을 카운터 데이터 .BLG 형식으로 변환 합니다.

`Import-Counter`Cmdlet은 파일에서 성능 카운터 데이터를 가져옵니다 `Threads.csv` . 이 예에서는 cmdlet을 사용 하 여이 파일을 이전에 내보낸 것으로 가정 합니다 `Export-Counter` . 파이프라인 연산자 ( `|` )는 가져온 데이터를 cmdlet으로 보냅니다 `Export-Counter` . 이 명령은 **Path** 매개 변수를 사용하여 출력 파일의 위치를 지정합니다. 이 cmdlet은 **순환** 및 **MaxSize** 매개 변수를 사용 하 여 cmdlet이 1gb로 `Export-Counter` 래핑하는 순환 로그를 만들도록 지시 합니다. **MaxSize** 매개 변수는 메가바이트 단위로 표현 됩니다.

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### 예 3: 원격 컴퓨터에서 카운터 데이터 가져오기 및 파일에 데이터 저장

이 예제에서는 원격 컴퓨터에서 성능 카운터 데이터를 가져와 원격 컴퓨터의 파일에 저장하는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Counter` 원격 컴퓨터인 Server01에서 작업 집합 카운터 데이터를 수집 합니다. 이 명령은 데이터를 `$C` 변수에 저장 합니다.

두 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 데이터를 `$C` cmdlet으로 전송 합니다. 그러면 `Export-Counter` 이 cmdlet이 `Workingset.blg` Server01 컴퓨터의 성능 공유에 있는 파일에 데이터를 저장 합니다.

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### 예제 4: 기존 데이터 다시 로그

이 예제에서는 및 cmdlet을 사용 하 여 `Import-Counter` 기존 데이터를 다시 로그 하는 방법을 보여 줍니다 `Export-Counter` .

첫 번째 명령은 cmdlet을 사용 하 여 `Import-Counter` DiskSpace 로그에서 성능 카운터 데이터를 가져옵니다. 변수에 데이터를 저장 `$All` 합니다. 이 파일에는 \% 기업에서 200 대 이상의 원격 컴퓨터에 있는 "논리 디스크 Free Space" 카운터 샘플이 포함 되어 있습니다.

두 번째 명령은 cmdlet을 사용 하 여 `Where-Object` 15 (%) 보다 작은 **CookedValue** 의 개체를 선택 합니다. 이 명령은 결과를 `$LowSpace` 변수에 저장 합니다.

세 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 변수의 데이터를 `$LowSpace` cmdlet으로 보냅니다 `Export-Counter` . 이 명령은 **Path** 매개 변수를 사용하여 선택한 데이터가 LowDiskSpace.blg 파일에 기록되도록 지정합니다.

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## PARAMETERS

### -순환

출력 파일이 FIFO (선입 선출) 형식을 사용 하는 순환 로그 임을 나타냅니다.
이 매개 변수를 포함하는 경우 **MaxSize** 매개 변수가 필요합니다.

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

### -FileFormat

출력 로그 파일의 출력 형식을 지정합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- CSV
- TSV
- BLG

기본값은 BLG입니다.

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

### -Force

**Path** 매개 변수에 지정 된 위치에 존재 하는 경우 기존 파일을 덮어쓰고 대체 합니다.

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

### -InputObject

내보낼 카운터 데이터를 배열로 지정 합니다. 데이터를 포함 하는 변수 또는 데이터를 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `Get-Counter` `Import-Counter` .

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

### -MaxSize

출력 파일의 최대 크기 (mb)를 지정 합니다.

**순환** 매개 변수가 지정 된 경우 로그 파일이 지정 된 최대 크기에 도달 하면 새 항목이 추가 될 때 가장 오래 된 항목이 삭제 됩니다. **순환** 매개 변수가 지정 되지 않은 경우 로그 파일이 지정 된 최대 크기에 도달 하면 새 데이터가 추가 되지 않고 cmdlet에서 종료 되지 않는 오류를 생성 합니다.

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

### -Path

출력 파일의 경로와 파일 이름을 지정합니다. 로컬 컴퓨터에 상대 또는 절대 경로를 입력 하거나와 같은 원격 컴퓨터에 대 한 UNC (Uniform 명명 규칙) 경로를 입력 `\\Computer\Share\file.blg` 합니다. 이 매개 변수는 필수적 요소입니다.

파일 형식은 경로에서 파일 이름 확장명이 아닌 **FileFormat** 매개 변수의 값에 의해 결정 됩니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### PerformanceCounterSampleSet. GetCounter.

`Get-Counter`또는이 cmdlet에서 성능 카운터 데이터를 파이프 할 수 있습니다 `Import-Counter` .

## 출력

### 없음

## 참고

로그 파일 생성기에서는 모든 입력 개체의 카운터 경로가 동일하며 개체가 오름차순으로 정렬되어 있어야 합니다.

첫 번째 입력 개체의 카운터 유형 및 경로가 로그 파일에 기록되는 속성을 결정합니다. 다른 입력 개체에 기록된 속성 값이 없으면 속성 필드는 비게 됩니다. 해당 개체에 기록되지 않은 속성 값이 있으면 추가 속성 값은 무시됩니다.

성능 모니터에서 생성 하는 모든 로그를 읽지 못할 수 있습니다 `Export-Counter` . 예를 들어 성능 모니터에서는 모든 개체의 경로가 동일 하며 모든 개체가 동일한 시간 간격으로 분리 되어야 합니다.

`Import-Counter`Cmdlet에 **ComputerName** 매개 변수가 없습니다. 그러나 컴퓨터가 원격 Windows PowerShell Windows PowerShell 용으로 구성 된 경우에는 cmdlet을 사용 `Invoke-Command` 하 여 `Import-Counter` 원격 컴퓨터에서 명령을 실행할 수 있습니다.

## 관련 링크

[Get-Counter](Get-Counter.md)

[Import-Counter](Import-Counter.md)
