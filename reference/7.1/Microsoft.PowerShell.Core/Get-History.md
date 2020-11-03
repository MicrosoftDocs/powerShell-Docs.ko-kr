---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: 0c5e55d3f1bcc6d988b54a8747173d88acbdec35
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "93220153"
---
# Get-History

## 개요
현재 세션 중에 입력된 명령 목록을 가져옵니다.

## SYNTAX

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## 설명

`Get-History`Cmdlet은 세션 기록, 즉 현재 세션 중에 입력 된 명령 목록을 가져옵니다.

PowerShell은 각 세션의 기록을 자동으로 유지 관리 합니다. 세션 기록의 항목 수는 기본 설정 변수의 값에 따라 결정 됩니다 `$MaximumHistoryCount` . Windows PowerShell 3.0부터 기본값은 `4096` 입니다. 기본적으로 기록 파일은 홈 디렉터리에 저장되지만 원하는 위치에 파일을 저장할 수 있습니다. PowerShell의 기록 기능에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.

세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.
**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다. 이 cmdlet은 세션 기록 에서만 작동 합니다. 자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

## 예제

### 예제 1: 세션 기록 가져오기

이 예제에서는 세션 기록의 항목을 가져옵니다. 기본 표시에는 각 명령과 각 명령이 실행 된 순서를 나타내는 해당 ID가 표시 됩니다.

```powershell
Get-History
```

### 예제 2: 문자열을 포함 하는 항목 가져오기

이 예제에서는 문자열 서비스를 포함 하는 명령 기록의 항목을 가져옵니다. 첫 번째 명령은 세션 기록의 모든 항목을 가져옵니다. 파이프라인 연산자 ( `|` )는 결과를 cmdlet으로 전달 합니다 `Where-Object` .이 cmdlet은 서비스를 포함 하는 명령만 선택 합니다.

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### 예 3: 특정 ID까지 기록 항목 내보내기

이 예제에서는 항목 7로 끝나는 5 개의 최근 기록 항목을 가져옵니다. 파이프라인 연산자는 결과를 cmdlet으로 전달 합니다 `Export-Csv` .이 cmdlet은 기록을 쉼표로 구분 된 텍스트로 포맷 하 고 History.csv 파일에 저장 합니다. 이 파일에는 기록의 형식을 목록으로 지정할 때 표시 되는 데이터가 포함 됩니다. 여기에는 명령의 상태와 시작 및 종료 시간이 포함 됩니다.

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### 예제 4: 최신 명령 표시

이 예제에서는 명령 기록의 마지막 명령을 가져옵니다. 마지막 명령은 가장 최근에 입력 한 명령입니다. 이 명령은 **Count** 매개 변수를 사용 하 여 하나의 명령만 표시 합니다. 기본적으로 `Get-History` 가장 최근 명령을 가져옵니다. 이 명령은 "h -c 1"로 간략하게 표시할 수 있으며 위쪽 화살표 키를 누르는 것과 같습니다.

```powershell
Get-History -Count 1
```

### 예 5: 기록에 있는 항목의 모든 속성을 표시 합니다.

이 예에서는 세션 기록에 있는 항목의 모든 속성을 표시 합니다. 파이프라인 연산자는 명령 결과를 `Get-History` cmdlet에 전달 합니다 `Format-List` . 그러면이 cmdlet이 각 기록 항목의 모든 속성을 표시 합니다. 여기에는 명령의 ID, 상태 및 시작 시간과 종료 시간이 포함 됩니다.

```powershell
Get-History | Format-List -Property *
```

## PARAMETERS

### -개수

이 cmdlet이 가져오는 최근 기록 항목의 수를 지정 합니다. 기본적으로 `Get-History` 세션 기록의 모든 항목을 가져옵니다. 명령에서 **Count** 및 **Id** 매개 변수를 모두 사용하는 경우 표시는 **Id** 매개 변수에 지정된 명령으로 끝납니다.

Windows PowerShell 2.0에서는 기본적으로 32의 `Get-History` 가장 최근 항목을 가져옵니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

세션 기록에 있는 항목의 Id 배열을 지정 합니다. `Get-History` 지정 된 항목만 가져옵니다. 명령에서 **id** 및 **Count** 매개 변수를 모두 사용 하는 경우 `Get-History` **id** 매개 변수로 지정 된 항목으로 끝나는 가장 최근 항목을 가져옵니다.

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Int64

기록 ID를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### HistoryInfo.

이 cmdlet은 가져온 각 기록 항목에 대 한 기록 개체를 반환 합니다.

## 참고

세션 기록은 세션 중에 입력된 명령 목록입니다. 세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다. 각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다. 명령 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.

Windows PowerShell 3.0부터 기본 `$MaximumHistoryCount` 설정 변수의 기본값은 `4096` 입니다. Windows PowerShell 2.0에서 기본값은 `64` 입니다. 변수에 대 한 자세한 내용은 `$MaximumHistoryCount` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

## 관련 링크

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Invoke-History](Invoke-History.md)

[about_History](About/about_History.md)
