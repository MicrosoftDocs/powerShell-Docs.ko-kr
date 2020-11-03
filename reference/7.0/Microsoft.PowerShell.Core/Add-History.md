---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 1c0a4c958ae60ab6bde170a71f6bc69e09079074
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210818"
---
# Add-History

## 개요
세션 기록에 항목을 추가합니다.

## SYNTAX

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## 설명

`Add-History`Cmdlet은 세션 기록 끝, 즉 현재 세션 중에 입력 된 명령 목록에 항목을 추가 합니다.

세션 기록은 세션 중에 입력된 명령 목록입니다. 세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다. 각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다. 세션 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.

세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.
**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다. 이 cmdlet은 세션 기록 에서만 작동 합니다. 자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

Cmdlet을 사용 `Get-History` 하 여 명령을 가져오고이를에 전달 하거나, `Add-History` 명령을 CSV 또는 XML 파일로 내보낸 다음, 명령을 가져와 가져온 파일을에 전달할 수 있습니다 `Add-History` . 이 cmdlet을 사용하여 기록에 특정 명령을 추가하거나 두 개 이상의 세션 명령을 포함하는 하나의 기록 파일을 만들 수 있습니다.

## 예제

### 예제 1: 다른 세션의 기록에 명령 추가

이 예에서는 하나의 PowerShell 세션에서 입력 된 명령을 다른 PowerShell 세션의 기록에 추가 합니다.

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

첫 번째 명령은 기록의 명령을 나타내는 개체를 가져와 `History.csv` 파일로 내보냅니다.

두 번째 명령은 다른 세션의 명령줄에 입력합니다. Cmdlet을 사용 하 여 `Import-Csv` 파일의 개체를 가져옵니다 `History.csv` . 파이프라인 연산자 ( `|` )는 개체를 cmdlet으로 전달 합니다 `Add-History` . 그러면이 cmdlet이 파일의 명령을 나타내는 개체를 `History.csv` 현재 세션 기록에 추가 합니다.

### 예제 2: 명령 가져오기 및 실행

이 예제에서는 파일에서 명령을 가져와 `History.xml` 현재 세션 기록에 추가한 다음 결합 된 기록에서 명령을 실행 합니다.

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

첫 번째 명령은 cmdlet을 사용 하 여 `Import-Clixml` 파일로 내보낸 명령 기록을 가져옵니다 `History.xml` . 파이프라인 연산자는 명령을 `Add-History` 현재 세션 기록에 추가 하는 cmdlet에 전달 합니다. **PassThru** 매개 변수는 추가 된 명령을 나타내는 개체를 파이프라인으로 전달 합니다.

그런 다음이 명령은 cmdlet을 사용 하 여 `ForEach-Object` `Invoke-History` 결합 된 기록의 각 명령에 명령을 적용 합니다. `Invoke-History`명령은 `{}` Cmdlet의 **Process** 매개 변수에서 요구 하는 대로 중괄호 ()로 묶인 스크립트 블록으로 형식이 지정 됩니다 `ForEach-Object` .

### 예제 3: 기록의 끝 부분에 명령 추가

이 예에서는 기록의 처음 5 개 명령을 기록 목록의 끝에 추가 합니다.

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

`Get-History`Cmdlet은 명령 5에서 끝나는 5 개의 명령을 가져옵니다. 파이프라인 연산자가 cmdlet에 전달 하 여 `Add-History` 현재 기록에 추가 합니다. 명령에는 `Add-History` 매개 변수가 포함 되어 있지 않지만 PowerShell은 파이프라인을 통해 전달 된 개체를의 **InputObject** 매개 변수와 연결 합니다 `Add-History` .

### 예제 4: .csv 파일의 명령을 현재 기록에 추가

이 예에서는 파일의 명령을 `History.csv` 현재 세션 기록에 추가 합니다.

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

`Import-Csv`Cmdlet은 파일의 명령을 가져와 `History.csv` 변수에 해당 내용을 저장 `$a` 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Add-History` 의 명령을 `History.csv` 현재 세션 기록에 추가 합니다. **InputObject** 매개 변수를 사용 하 여 변수를 지정 하 `$a` 고 **PassThru** 매개 변수를 사용 하 여 명령줄에 표시할 개체를 생성 합니다. **PassThru** 매개 변수를 사용 하지 않으면 `Add-History` cmdlet은 출력을 생성 하지 않습니다.

### 예 5: .xml 파일의 명령을 현재 기록에 추가

이 예에서는 파일의 명령을 `history.xml` 현재 세션 기록에 추가 합니다.

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

**InputObject** 매개 변수는 명령 결과를 괄호 안에 cmdlet에 전달 합니다 `Add-History` . 괄호 안의 명령은 먼저 실행 되 고 `history.xml` 파일을 PowerShell로 가져옵니다. `Add-History`그런 다음 cmdlet은 파일의 명령을 세션 기록에 추가 합니다.

## PARAMETERS

### -InputObject

**HistoryInfo** 개체로 기록에 추가할 항목의 배열을 세션 기록에 지정 합니다.
이 매개 변수를 사용 하 여 **HistoryInfo** `Get-History` , `Import-Clixml` 또는 cmdlet에서 반환 된 개체와 같은 HistoryInfo 개체를로 전송할 수 있습니다 `Import-Csv` `Add-History` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Passthru

이 cmdlet이 각 기록 항목에 대 한 **HistoryInfo** 개체를 반환 함을 나타냅니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### HistoryInfo.

**HistoryInfo** 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None 또는 HistoryInfo

**PassThru** 매개 변수를 지정 하는 경우이 Cmdlet은 **HistoryInfo** 개체를 반환 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

세션 기록은 ID와 함께 세션 중에 입력 된 명령 목록입니다. 세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다. 각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다. 세션 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.

기록에 추가할 명령을 지정하려면 **InputObject** 매개 변수를 사용합니다. `Add-History`명령은 cmdlet에 의해 각 명령에 대해 반환 된 개체와 같은 **HistoryInfo** 개체만 허용 `Get-History` 합니다. 경로 및 파일 이름이나 명령 목록은 전달할 수 없습니다.

**InputObject** 매개 변수를 사용 하 여 **HistoryInfo** 개체의 파일을에 전달할 수 있습니다 `Add-History` . 이렇게 하려면 `Get-History` 또는 cmdlet을 사용 하 여 명령 결과를 파일로 내보낸 `Export-Csv` `Export-Clixml` 다음 또는 cmdlet을 사용 하 여 파일을 가져옵니다 `Import-Csv` `Import-Clixml` . 그런 다음 파이프라인 또는 변수를 통해 가져온 **HistoryInfo** 개체의 파일을에 전달할 수 있습니다 `Add-History` . 자세한 내용은 예제를 참조하세요.

Cmdlet에 전달 하는 **HistoryInfo** 개체의 파일은 `Add-History` 유형 정보, 열 머리글 및 **HistoryInfo** 개체의 모든 속성을 포함 해야 합니다. 개체를 다시에 전달 하려는 경우 `Add-History` cmdlet의 **notypeinformation** 매개 변수를 사용 하지 말고 `Export-Csv` 파일의 유형 정보, 열 머리글 또는 필드를 삭제 하지 마십시오.

세션 기록을 수정 하려면 세션을 CSV 또는 XML 파일로 내보낸 다음 파일을 수정 하 고를 사용 하 여 `Add-History` 현재 세션 기록에 추가 합니다.

## 관련 링크

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[Get-PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)
