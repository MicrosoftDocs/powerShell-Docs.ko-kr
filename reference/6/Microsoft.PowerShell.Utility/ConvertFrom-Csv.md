---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 68b101d0ff36fe9417118dd97d112c070672c9b7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216841"
---
# ConvertFrom-Csv

## 개요
CSV(쉼표로 구분된 값) 형식의 개체 속성을 원래 개체의 CSV 버전으로 변환합니다.

## SYNTAX

### DelimiterPath (기본값)

```
ConvertFrom-Csv [[-Delimiter] <Char>] [-InputObject] <PSObject[]> [-Header <String[]>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
ConvertFrom-Csv -UseCulture [-InputObject] <PSObject[]> [-Header <String[]>] [<CommonParameters>]
```

### CulturePath

```
ConvertFrom-Csv -UseCulture [-InputObject] <PSObject[]> [-Header <String[]>] [<CommonParameters>]
```

## 설명

`ConvertFrom-Csv`Cmdlet은 cmdlet에 의해 생성 된 CSV 가변 길이 문자열에서 개체를 만듭니다 `ConvertTo-Csv` .

이 cmdlet의 매개 변수를 사용 하 여 결과 개체의 속성 이름을 결정 하는 열 머리글 행을 지정 하거나, 항목 구분 기호를 지정 하거나,이 cmdlet이 현재 문화권의 목록 구분 기호를 구분 기호로 사용 하도록 지시할 수 있습니다.

에서 만드는 개체는 `ConvertFrom-Csv` 원래 개체의 CSV 버전입니다. CSV 개체의 속성 값은 원래 개체 속성 값의 문자열 버전입니다. 개체의 CSV 버전에는 메서드가 없습니다.

`Export-Csv`및 cmdlet을 사용 하 여 `Import-Csv` 개체를 파일에서 CSV 문자열로 변환할 수도 있습니다. 이러한 cmdlet은 `ConvertTo-Csv` `ConvertFrom-Csv` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고 및 cmdlet과 동일 합니다.

## 예제

### 예 1: 로컬 컴퓨터의 프로세스를 CSV 형식으로 변환

이 예에서는 로컬 컴퓨터의 프로세스를 CSV 형식으로 변환한 다음 개체 형식으로 복원 하는 방법을 보여 줍니다.

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

`Get-Process`Cmdlet은 파이프라인에서로 프로세스를 보냅니다 `ConvertTo-Csv` . `ConvertTo-Csv`Cmdlet은 프로세스 개체를 일련의 CSV 문자열로 변환 합니다. `ConvertFrom-Csv`Cmdlet은 csv 문자열을 원래 프로세스 개체의 csv 버전으로 변환 합니다. CSV 문자열은 변수에 저장 됩니다 `$P` .

### 예제 2: 데이터 개체를 CSV 형식으로 변환한 다음 CSV 개체 형식으로 변환

이 예제에서는 데이터 개체를 CSV 형식으로 변환한 다음 CSV 개체 형식으로 변환 하는 방법을 보여 줍니다.

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

첫 번째 명령은를 사용 하 여 `Get-Date` 파이프라인의 현재 날짜 및 시간을로 보냅니다 `ConvertTo-Csv` . `ConvertTo-Csv`Cmdlet은 날짜 개체를 일련의 CSV 문자열로 변환 합니다.
**구분 기호** 매개 변수는 세미콜론 구분 기호를 지정 하는 데 사용 됩니다. 문자열은 변수에 저장 됩니다 `$Date` .

### 예제 3: 헤더 매개 변수를 사용 하 여 속성 이름 변경

이 예제에서는의 **Header** 매개 변수를 사용 하 여 `ConvertFrom-Csv` 가져온 결과 개체의 속성 이름을 변경 하는 방법을 보여 줍니다.

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

Cmdlet은를 `Start-Job` 실행 하는 백그라운드 작업을 시작 `Get-Process` 합니다. 작업 개체는 파이프라인에서로 전송 되 `ConvertTo-Csv` 고 CSV 문자열로 변환 됩니다. **Notypeinformation** 매개 변수는 CSV 출력에서 형식 정보 헤더를 제거 하 고 PowerShell Core에서 선택 사항입니다. `$Header`변수에는 다음과 같은 기본값을 대체 하는 사용자 지정 헤더가 포함 됩니다. **HasMoreData** , **jobstateinfo** , **Psbegintime** , **psendtime** 및 **PSJobTypeName** . `$J`변수는 CSV 문자열을 포함 하 고 기본 헤더를 제거 하는 데 사용 됩니다. `ConvertFrom-Csv`Cmdlet은 CSV 문자열을 **PSCustomObject** 변환 하 고 **Header** 매개 변수를 사용 하 여 변수를 적용 `$Header` 합니다.

### 예제 4: 서비스 개체의 CSV 문자열 변환

이 예에서는 `ConvertFrom-Csv` **UseCulture** 매개 변수와 함께 cmdlet을 사용 하는 방법을 보여 줍니다.

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 여 현재 문화권의 기본 목록 구분 기호를 가져옵니다. `Get-Service`Cmdlet은 파이프라인에서로 서비스 개체를 보냅니다 `ConvertTo-Csv` . 는 `ConvertTo-Csv` 서비스 개체를 일련의 CSV 문자열로 변환 합니다. CSV 문자열은 변수에 저장 됩니다 `$Services` . 이 `ConvertFrom-Csv` cmdlet은 **InputObject** 매개 변수를 사용 하 여 변수에서 CSV 문자열을 변환 합니다 `$Services` . **UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 사용 합니다.

**UseCulture** 매개 변수를 사용 하는 경우 현재 문화권의 기본 목록 구분 기호가 CSV 문자열에 사용 된 구분 기호와 일치 해야 합니다. 그렇지 않으면는 `ConvertFrom-Csv` CSV 문자열에서 개체를 생성할 수 없습니다.

## PARAMETERS

### -구분 기호

CSV 문자열의 속성 값을 구분하는 구분 기호를 지정합니다.
기본값은 쉼표(,)입니다.

콜론(:)과 같은 문자를 입력합니다.
세미콜론 (;)을 지정 하려면 작은따옴표로 묶습니다.

파일의 실제 문자열 구분 기호 이외의 문자를 지정 하는 경우는 `ConvertFrom-Csv` csv 문자열에서 개체를 만들 수 없으며 csv 문자열을 반환 합니다.

```yaml
Type: System.Char
Parameter Sets: DelimiterPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -헤더

가져온 문자열에 대해 대체 열 머리글 행을 지정합니다. 열 머리글은에서 만든 개체의 속성 이름을 결정 합니다 `ConvertFrom-Csv` .

열 머리글을 쉼표로 구분 된 목록으로 입력 합니다. 머리글 문자열을 따옴표로 묶지 마세요. 각 열 머리글을 작은따옴표로 묶습니다.

데이터 열 보다 더 작은 수의 열 머리글을 입력 하면 나머지 데이터 열이 삭제 됩니다. 데이터 열 보다 많은 열 머리글을 입력 하면 빈 데이터 열이 포함 된 추가 열 머리글이 만들어집니다.

**Header** 매개 변수를 사용할 때는 CSV 문자열에서 열 머리글 문자열을 생략 합니다. 그렇지 않으면이 cmdlet은 머리글 행의 항목에서 개체를 추가로 만듭니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

개체로 변환할 CSV 문자열을 지정합니다. CSV 문자열이 포함된 변수를 입력하거나 CSV 문자열을 가져오는 명령 또는 식을 입력하세요. CSV 문자열을로 파이프 할 수도 있습니다 `ConvertFrom-Csv` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다. 문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CultureLiteralPath, CulturePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

CSV 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.web. PSObject

이 cmdlet은 CSV 문자열의 속성이 설명 하는 개체를 반환 합니다.

## 참고

가져온 개체는 개체 유형의 CSV 버전 이므로 CSV가 아닌 버전의 개체 유형을 포맷 하는 PowerShell 유형 형식 지정 항목을 통해 인식 되지 않으며 형식이 지정 되지 않습니다.

CSV 형식에서 각 개체는 개체 속성 값을 쉼표로 구분한 목록으로 표현됩니다. 속성 값은 개체의 **ToString ()** 메서드를 사용 하 여 문자열로 변환 되므로 속성 값의 이름으로 표시 됩니다. 이 cmdlet은 개체의 메서드를 내보내지 않습니다.

## 관련 링크

[ConvertTo-Csv](ConvertTo-Csv.md)

[Export-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)
