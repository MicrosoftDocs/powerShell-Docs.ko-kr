---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: be590368539f396f0aac694e9565674393543f2c
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913205"
---
# ConvertTo-Csv

## 개요
.NET 개체를 일련의 CSV (쉼표로 구분 된 값) 문자열로 변환 합니다.

## SYNTAX

### 구분 기호 (기본값)

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## 설명

`ConvertTo-CSV`Cmdlet은 제출한 개체를 나타내는 일련의 CSV (쉼표로 구분 된 값) 문자열을 반환 합니다. 그런 다음 cmdlet을 사용 `ConvertFrom-Csv` 하 여 CSV 문자열에서 개체를 다시 만들 수 있습니다. CSV에서 변환 된 개체는 속성 값을 포함 하 고 메서드를 포함 하지 않는 원래 개체의 문자열 값입니다.

Cmdlet을 사용 `Export-Csv` 하 여 개체를 CSV 문자열로 변환할 수 있습니다. `Export-CSV` 은 `ConvertTo-CSV` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.

Cmdlet에는 `ConvertTo-CSV` 쉼표 이외의 구분 기호를 지정 하거나 현재 문화권을 구분 기호로 사용 하는 매개 변수가 있습니다.

## 예제

### 예제 1: 개체를 CSV로 변환

이 예에서는 **프로세스** 개체를 CSV 문자열로 변환 합니다.

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

`Get-Process`Cmdlet은 **프로세스** 개체를 가져오고 **Name** 매개 변수를 사용 하 여 PowerShell 프로세스를 지정 합니다. Process 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `ConvertTo-CSV` . `ConvertTo-CSV`Cmdlet은 개체를 CSV 문자열로 변환 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** 정보 헤더를 제거 합니다.

### 예제 2: DateTime 개체를 CSV로 변환

이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

`Get-Date`Cmdlet은 **DateTime** 개체를 가져와서 변수에 저장 합니다 `$Date` . `ConvertTo-Csv`Cmdlet은 **DateTime** 개체를 문자열로 변환 합니다. **InputObject** 매개 변수는 변수에 저장 된 **DateTime** 개체를 사용 합니다 `$Date` . **Delimiter** 매개 변수는 문자열 값을 구분 하기 위해 세미콜론을 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** 정보 헤더를 제거 합니다.

### 예 3: PowerShell 이벤트 로그를 CSV로 변환

이 예에서는 PowerShell에 대 한 Windows 이벤트 로그를 일련의 CSV 문자열로 변환 합니다.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 고 현재 문화권의 기본 목록 구분 기호를 표시 합니다. `Get-WinEvent`Cmdlet은 이벤트 로그 개체를 가져오고 **LogName** 매개 변수를 사용 하 여 로그 파일 이름을 지정 합니다. 이벤트 로그 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `ConvertTo-Csv` . `ConvertTo-Csv`Cmdlet은 이벤트 로그 개체를 일련의 CSV 문자열로 변환 합니다. **UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 구분 기호로 사용 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** 정보 헤더를 제거 합니다.

## PARAMETERS

### -구분 기호

CSV 문자열의 속성 값을 구분 하는 구분 기호를 지정 합니다. 기본값은 쉼표 ()입니다 `,` . 콜론 ()과 같은 문자를 입력 `:` 합니다. 세미콜론 ()을 지정 하려면 작은따옴표로 `;` 묶습니다.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

CSV 문자열로 변환 되는 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 개체를로 파이프 할 수도 있습니다 `ConvertTo-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

출력에서 **#TYPE** 정보 헤더를 제거 합니다. 이 매개 변수는 PowerShell 6.0의 기본값이 며 이전 버전과의 호환성을 위해 포함 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다. 문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
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

### System.web. PSObject

Any (확장 형식 시스템) 어댑터가 있는 개체를로 파이프 할 수 있습니다 `ConvertTo-CSV` .

## 출력

### System.String

CSV 출력은 문자열 컬렉션으로 반환됩니다.

## 참고

CSV 형식에서 각 개체는 해당 속성 값의 쉼표로 구분된 목록으로 표시됩니다. 속성 값은 개체의 **ToString ()** 메서드를 사용 하 여 문자열로 변환 됩니다. 문자열은 속성 값 이름으로 표시 됩니다. `ConvertTo-CSV` 개체의 메서드를 내보내지 않습니다.

CSV 문자열은 다음과 같이 출력 됩니다.

- 기본적으로 첫 번째 문자열에는 **#TYPE** 정보 헤더와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다. 예를 들어, **#TYPE를 처리** 합니다.
- **Notypeinformation** 이 사용 되는 경우 첫 번째 문자열에는 열 머리글이 포함 됩니다. 헤더는 첫 번째 개체의 속성 이름을 쉼표로 구분 된 목록으로 포함 합니다.
- 나머지 문자열은 각 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 합니다.

에 여러 개체를 제출 하는 경우는 `ConvertTo-CSV` `ConvertTo-CSV` 제출한 첫 번째 개체의 속성을 기반으로 문자열을 정렬 합니다. 나머지 개체에 지정 된 속성 중 하나가 없는 경우 해당 개체의 속성 값은 Null 이며, 두 개의 연속 된 쉼표로 표시 됩니다. 나머지 개체에 추가 속성이 있으면 해당 속성 값은 무시됩니다.

## 관련 링크

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[내보내기-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)
