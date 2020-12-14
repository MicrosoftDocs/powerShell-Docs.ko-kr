---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: f920130ec8354b61b0bb3617e061520271df0eed
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913239"
---
# Export-Csv

## 개요
개체를 일련의 쉼표로 구분 된 값 (CSV) 문자열로 변환 하 고 문자열을 파일에 저장 합니다.

## SYNTAX

### 구분 기호 (기본값)

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UseCulture

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## 설명

`Export-CSV`Cmdlet은 제출한 개체의 CSV 파일을 만듭니다. 각 개체는 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 하는 행입니다. Cmdlet을 사용 `Export-CSV` 하 여 CSV 파일을 입력으로 수락 하는 프로그램을 사용 하 여 스프레드시트를 만들고 데이터를 공유할 수 있습니다.

개체를 cmdlet으로 보내기 전에 서식을 지정 하지 마십시오 `Export-CSV` . `Export-CSV`에서 형식이 지정 된 개체를 받으면 CSV 파일에 개체 속성이 아닌 형식 속성이 포함 됩니다. 개체의 선택 된 속성만 내보내려면 cmdlet을 사용 `Select-Object` 합니다.

## 예제

### 예제 1: CSV 파일로 프로세스 속성 내보내기

이 예제에서는 특정 속성을 사용 하 여 개체 **처리** 를 선택 하 고 개체를 CSV 파일로 내보냅니다.

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다. **Name** 매개 변수는 WmiPrvSE process 개체만 포함 하도록 출력을 필터링 합니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` . `Select-Object`**Property** 매개 변수를 사용 하 여 프로세스 개체 속성의 하위 집합을 선택 합니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다. **Path** 매개 변수는 WmiData.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. `Import-Csv`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예제 2: 쉼표로 구분 된 파일로 프로세스 내보내기

이 예제에서는 **프로세스** 개체를 가져오고 개체를 CSV 파일로 내보냅니다.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.
**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예제 3: 세미콜론으로 구분 된 파일로 프로세스 내보내기

이 예제에서는 **프로세스** 개체를 가져오고 세미콜론 구분 기호를 사용 하 여 개체를 파일로 내보냅니다.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.
**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Delimiter** 매개 변수는 문자열 값을 구분 하기 위해 세미콜론을 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예제 4: 현재 문화권의 목록 구분 기호를 사용 하 여 프로세스 내보내기

이 예제에서는 **프로세스** 개체를 가져오고 개체를 파일로 내보냅니다. 구분 기호는 현재 문화권의 목록 구분 기호입니다.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 고 현재 문화권의 기본 목록 구분 기호를 표시 합니다. `Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.
프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다. **Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 구분 기호로 사용 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예 5: 형식 정보를 사용 하 여 프로세스 내보내기

이 예제에서는 **#TYPE** 헤더 정보를 CSV 파일에 포함 하는 방법을 설명 합니다. **#TYPE** 헤더는 PowerShell 6.0 이전 버전의 기본값입니다.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.
**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Includetypeinformation** 에는 CSV 출력의 **#TYPE** 정보 헤더가 포함 됩니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예제 6: CSV 파일에 개체 내보내기 및 추가

이 예제에서는 개체를 CSV 파일로 내보내고 **Append** 매개 변수를 사용 하 여 기존 파일에 개체를 추가 하는 방법을 설명 합니다.

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

`Get-Service`Cmdlet은 서비스 개체를 가져옵니다. **DisplayName** 매개 변수는 Word 응용 프로그램을 포함 하는 서비스를 반환 합니다. Service 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` . `Select-Object`**Property** 매개 변수를 사용 하 여 **DisplayName** 및 **Status** 속성을 지정 합니다. `$AppService`변수는 개체를 저장 합니다.

`$AppService`개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 서비스 개체를 일련의 CSV 문자열로 변환 합니다. **Path** 매개 변수는 Services.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

`Get-Service`및 `Select-Object` Cmdlet은 Windows 라는 단어를 포함 하는 서비스에 대해 반복 됩니다. `$WinService`변수는 서비스 개체를 저장 합니다. `Export-Csv`Cmdlet은 **추가** 매개 변수를 사용 하 여 `$WinService` 개체가 기존 Services.csv 파일에 추가 되도록 지정 합니다. `Get-Content`추가 된 데이터가 포함 된 업데이트 된 파일을 표시 하기 위해 cmdlet이 반복 됩니다.

### 예 7: 파이프라인 내의 Format cmdlet은 예기치 않은 결과를 생성 합니다.

이 예제에서는 파이프라인 내에서 format cmdlet을 사용 하지 않는 것이 중요 한 이유를 보여 줍니다. 예기치 않은 출력이 수신 되 면 파이프라인 구문 문제를 해결 합니다.

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

`Get-Date`Cmdlet은 **DateTime** 개체를 가져옵니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` . `Select-Object`**Property** 매개 변수를 사용 하 여 개체 속성의 하위 집합을 선택 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 개체를 CSV 형식으로 변환 합니다. **Path** 매개 변수는 DateTime.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 CSV 파일을 표시 합니다.

`Format-Table`파이프라인 내에서 cmdlet을 사용 하 여 속성을 선택 하면 예기치 않은 결과가 수신 됩니다. `Format-Table` 테이블 형식 개체를 파이프라인에서 `Export-Csv` **DateTime** 개체가 아닌 cmdlet으로 보냅니다. `Export-Csv` 테이블 형식 개체를 일련의 CSV 문자열로 변환 합니다. `Get-Content`Cmdlet은 테이블 형식 개체를 포함 하는 CSV 파일을 표시 합니다.

### 예 8: Force 매개 변수를 사용 하 여 읽기 전용 파일 덮어쓰기

이 예제에서는 비어 있는 읽기 전용 파일을 만들고 **Force** 매개 변수를 사용 하 여 파일을 업데이트 합니다.

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`New-Item`Cmdlet은 **Path** 및 **ItemType** 매개 변수를 사용 하 여 현재 디렉터리에 ReadOnly.csv 파일을 만듭니다. `Set-ItemProperty`Cmdlet은 **Name** 및 **Value** 매개 변수를 사용 하 여 파일의 **IsReadOnly** 속성을 true로 변경 합니다. `Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다. **Path** 매개 변수는 ReadOnly.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다. 이 출력은 액세스가 거부 되었기 때문에 파일이 작성 되지 않은 것을 보여 줍니다.

**Force** 매개 변수를 cmdlet에 추가 하 여 `Export-Csv` 내보내기를 강제로 파일에 쓰도록 합니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예 9: Append에 Force 매개 변수 사용

이 예제에서는 **Force** 매개 변수를 사용 하 여 매개 변수를 **추가** 하는 방법을 보여 줍니다. 이러한 매개 변수를 결합 하면 일치 하지 않는 개체 속성을 CSV 파일에 쓸 수 있습니다.

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

식은 **Name** 및 **Version** 속성을 사용 하 여 **PSCustomObject** 를 만듭니다. 값은 변수에 저장 됩니다 `$Content` . `$Content`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . `Export-Csv`**Path** 매개 변수를 사용 하 여 현재 디렉터리에 ParmFile.csv 파일을 저장 합니다. **Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.

다른 식은 **Name** 및 **Edition** 속성을 사용 하 여 **PSCustomObject** 를 만듭니다. 값은 변수에 저장 됩니다 `$AdditionalContent` . `$AdditionalContent`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` . **추가** 매개 변수는 파일에 데이터를 추가 하는 데 사용 됩니다. **버전** 및 버전 간에 속성 이름이 일치 하지 않으므로 추가 작업이 **실패 합니다.**

`Export-Csv`Cmdlet **force** 매개 변수를 사용 하 여 내보내기를 강제로 파일에 쓰도록 합니다. **Edition** 속성이 무시 됩니다. `Import-Csv`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.

### 예 10: 두 열 주위에 따옴표를 사용 하 여 CSV로 내보내기

이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### 예 11: 필요한 경우에만 따옴표를 사용 하 여 CSV로 내보내기

이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## PARAMETERS

### -추가

이 매개 변수를 사용 하 여 `Export-CSV` 지정 된 파일의 끝에 CSV 출력을 추가 합니다. 이 매개 변수를 사용 하지 않으면 `Export-CSV` 는 경고 없이 파일 내용을 바꿉니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -구분 기호

속성 값을 구분하는 구분 기호를 지정합니다. 기본값은 쉼표 ()입니다 `,` . 콜론 ()과 같은 문자를 입력 `:` 합니다. 세미콜론 ()을 지정 하려면 `;` 따옴표로 묶으십시오.

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

### -Encoding

내보낸 CSV 파일의 인코딩을 지정합니다. 기본값은 `utf8NoBOM`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

> [!NOTE]
> **U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다. PowerShell 7.1에서는 `utf7` _ *Encoding** 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 매개 변수 `Export-Csv` 를 사용 하면 **읽기 전용** 특성으로 파일을 덮어쓸 수 있습니다.

**Force** 및 **Append** 매개 변수를 결합 하면 일치 하지 않는 속성을 포함 하는 개체를 CSV 파일에 쓸 수 있습니다. 일치 하는 속성만 파일에 기록 됩니다. 일치 하지 않는 속성은 무시 됩니다.

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

### -IncludeTypeInformation

이 매개 변수를 사용 하면 CSV 출력의 첫 번째 줄에 **#TYPE** 와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다. 예를 들어, **#TYPE를 처리** 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

CSV 문자열로 내보낼 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 개체를로 파이프 할 수도 있습니다 `Export-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

CSV 출력 파일의 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 경로에 이스케이프 문자가 포함 된 경우 작은따옴표를 사용 합니다. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

이 매개 변수를 사용 하 여 `Export-CSV` 기존 파일을 덮어쓰지 않도록 합니다. 기본적으로 지정 된 경로에 파일이 있으면는 `Export-CSV` 경고 없이 파일을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -Path

CSV 출력 파일을 저장할 위치를 지정 하는 필수 매개 변수입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Cmdlet이 처리 되지 않거나 변경 되지 않도록 합니다. 출력은 cmdlet이 실행 될 때 발생 하는 상황을 보여 줍니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -QuoteFields

따옴표로 묶을 열의 이름을 지정 합니다. 이 매개 변수를 사용 하면 지정 된 열만 따옴표로 묶여 있습니다. 이 매개 변수는 PowerShell 7.0에 추가 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseQuotes 기술

CSV 파일에서 따옴표를 사용 하는 경우를 지정 합니다. 가능한 값은 다음과 같습니다.

- 안 함-아무것도 인용 하지 않음
- 항상 따옴표 모든 항목 (기본 동작)
- AsNeeded-구분 문자를 포함 하는 견적 필드만

이 매개 변수는 PowerShell 7.0에 추가 되었습니다.

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

Any (확장 형식 시스템) 어댑터를 사용 하 여 개체를로 파이프 할 수 있습니다 `Export-CSV` .

## 출력

### System.String

CSV 목록이 Path 매개 변수에 지정된 파일로 보내집니다.

## 참고

`Export-CSV`Cmdlet은 제출한 개체를 일련의 CSV 문자열로 변환 하 고 지정 된 텍스트 파일에 저장 합니다. `Export-CSV -IncludeTypeInformation`를 사용 하 여 개체를 csv 파일에 저장 한 다음 cmdlet을 사용 하 여 `Import-Csv` csv 파일의 텍스트에서 개체를 만들 수 있습니다.

CSV 파일에서 각 개체는 쉼표로 구분된 개체 속성 값 목록으로 표시됩니다. 속성 값은 **ToString ()** 메서드를 사용 하 여 문자열로 변환 됩니다. 문자열은 속성 값 이름으로 표시 됩니다. `Export-CSV -IncludeTypeInformation` 는 개체의 메서드를 내보내지 않습니다.

CSV 문자열은 다음과 같이 출력 됩니다.

- **Includetypeinformation** 이 사용 되는 경우 첫 번째 문자열에는 **#TYPE** information 헤더와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다.
  예를 들어, **#TYPE를 처리** 합니다.
- **Includetypeinformation** 을 사용 하지 않으면 첫 번째 문자열에 열 머리글이 포함 됩니다. 헤더는 첫 번째 개체의 속성 이름을 쉼표로 구분 된 목록으로 포함 합니다.
- 나머지 문자열은 각 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 합니다.

PowerShell 6.0부터의 기본 동작은 `Export-CSV` CSV에 **#TYPE** 정보를 포함 하지 않는 것이 고 **notypeinformation** 이 암시 됩니다. **Includetypeinformation** 은 **#TYPE** 정보를 포함 하 고 PowerShell 6.0 이전의 기본 동작을 에뮬레이트하는 데 사용할 수 있습니다 `Export-CSV` .

여러 개체를에 제출할 때 `Export-CSV` 는 `Export-CSV` 제출한 첫 번째 개체의 속성을 기반으로 파일을 구성 합니다. 나머지 개체에 지정된 속성 중 하나가 없는 경우 해당 개체의 속성 값은 null이며, 두 개의 연속된 쉼표로 표시됩니다. 나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.

Cmdlet을 사용 `Import-Csv` 하 여 파일에 있는 CSV 문자열에서 개체를 다시 만들 수 있습니다. 결과 개체는 속성 값(메서드는 포함 안 됨)의 문자열 표시로 이루어진 원래 개체의 CSV 버전입니다.

및 cmdlet은 개체를 csv 문자열과 csv 문자열로 `ConvertTo-Csv` `ConvertFrom-Csv` 변환 합니다. `Export-CSV` 은 `ConvertTo-CSV` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고와 동일 합니다.

## 관련 링크

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Format-Table](Format-Table.md)

[Import-Csv](Import-Csv.md)

[Select-Object](Select-Object.md)
