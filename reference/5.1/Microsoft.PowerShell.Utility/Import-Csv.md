---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: 6d060e0325ba10391f04348178f28b2793fe37fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213882"
---
# Import-Csv

## 개요
쉼표로 구분 된 값 (CSV) 파일의 항목에서 테이블 형태의 사용자 지정 개체를 만듭니다.

## SYNTAX

### 구분 기호 (기본값)

```
Import-Csv [[-Path] <string[]>] [[-Delimiter] <char>] [-LiteralPath <string[]>] [-Header <string[]>]
 [-Encoding <string>] [<CommonParameters>]
```

### UseCulture

```
Import-Csv [[-Path] <string[]>] -UseCulture [-LiteralPath <string[]>] [-Header <string[]>]
 [-Encoding <string>] [<CommonParameters>]
```

## 설명

`Import-Csv`Cmdlet은 CSV 파일의 항목에서 테이블 유사 사용자 지정 개체를 만듭니다. CSV 파일의 각 열은 사용자 지정 개체의 속성이 되 고 행의 항목은 속성 값이 됩니다. `Import-Csv` cmdlet에서 생성 된 파일을 포함 하 여 모든 CSV 파일에서 작동 `Export-Csv` 합니다.

Cmdlet의 매개 변수를 사용 하 여 `Import-Csv` 열 머리글 행과 항목 구분 기호를 지정 하거나, `Import-Csv` 현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용할 수 있습니다.

`ConvertTo-Csv`및 cmdlet을 사용 하 여 `ConvertFrom-Csv` 개체를 CSV 문자열로 변환 하 고 다시 변환할 수도 있습니다. 이러한 cmdlet은 `Export-CSV` `Import-Csv` 파일을 처리 하지 않는다는 점을 제외 하 고 및 cmdlet과 동일 합니다.

CSV 파일의 머리글 행 항목에 빈 값 이나 null 값이 포함 되어 있으면 PowerShell에서 기본 머리글 행 이름을 삽입 하 고 경고 메시지를 표시 합니다.

`Import-Csv` 는 BOM (바이트 순서 표시)을 사용 하 여 파일의 인코딩 형식을 검색 합니다. 파일에 BOM이 없으면 인코딩이 UTF8 이라고 가정 합니다.

## 예제

### 예제 1: 프로세스 개체 가져오기

이 예제에서는 프로세스 개체의 CSV 파일을 내보낸 다음 가져오는 방법을 보여 줍니다.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

`Get-Process`Cmdlet은 프로세스 개체를 파이프라인에서로 보냅니다 `Export-Csv` . `Export-Csv`Cmdlet은 프로세스 개체를 CSV 문자열로 변환 하 고 Processes.csv 파일에 문자열을 저장 합니다. `Import-Csv`Cmdlet은 Processes.csv 파일에서 CSV 문자열을 가져옵니다.
문자열은 변수에 저장 됩니다 `$P` . `$P`변수는 `Get-Member` 가져온 CSV 문자열의 속성을 표시 하는 cmdlet에 파이프라인으로 전송 됩니다. `$P`변수는 파이프라인에서 cmdlet으로 전송 되 `Format-Table` 고 개체를 표시 합니다.

### 예제 2: 구분 기호 지정

이 예에서는 cmdlet의 **Delimiter** 매개 변수를 사용 하는 방법을 보여 줍니다 `Import-Csv` .

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

`Get-Process`Cmdlet은 프로세스 개체를 파이프라인에서로 보냅니다 `Export-Csv` . `Export-Csv`Cmdlet은 프로세스 개체를 CSV 문자열로 변환 하 고 Processes.csv 파일에 문자열을 저장 합니다.
**구분 기호** 매개 변수는 콜론 구분 기호를 지정 하는 데 사용 됩니다. `Import-Csv`Cmdlet은 Processes.csv 파일에서 CSV 문자열을 가져옵니다. 문자열은 변수에 저장 됩니다 `$P` . To `$P` variable은 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Table` .

### 예제 3: 구분 기호에 대 한 현재 문화권 지정

이 예에서는 `Import-Csv` **UseCulture** 매개 변수와 함께 cmdlet을 사용 하는 방법을 보여 줍니다.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 여 현재 문화권의 기본 목록 구분 기호를 가져옵니다. `Get-Process`Cmdlet은 프로세스 개체를 파이프라인에서로 보냅니다 `Export-Csv` . `Export-Csv`Cmdlet은 프로세스 개체를 CSV 문자열로 변환 하 고 Processes.csv 파일에 문자열을 저장 합니다. **UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 사용 합니다. `Import-Csv`Cmdlet은 Processes.csv 파일에서 CSV 문자열을 가져옵니다.

### 예제 4: 가져온 개체의 속성 이름 변경

이 예제에서는의 **Header** 매개 변수를 사용 하 여 `Import-Csv` 가져온 결과 개체의 속성 이름을 변경 하는 방법을 보여 줍니다.

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished',
  'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error',
  'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
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

Cmdlet은를 `Start-Job` 실행 하는 백그라운드 작업을 시작 `Get-Process` 합니다. 작업 개체는 파이프라인에서 cmdlet으로 전송 되 `Export-Csv` 고 CSV 문자열로 변환 됩니다. **Notypeinformation** 매개 변수는 CSV 출력에서 형식 정보 헤더를 제거 하 고 PowerShell Core에서 선택 사항입니다.
`$Header`변수에는 다음과 같은 기본값을 대체 하는 사용자 지정 헤더가 포함 됩니다. **HasMoreData** , **jobstateinfo** , **Psbegintime** , **psendtime** 및 **PSJobTypeName** . 변수는 cmdlet을 사용 하 여 `$A` `Get-Content` Jobs.csv 파일에서 CSV 문자열을 가져옵니다. `$A`변수는 파일에서 기본 헤더를 제거 하는 데 사용 됩니다. `Out-File`Cmdlet은 Jobs.csv 파일의 새 버전을 변수에 저장 합니다 `$A` . `Import-Csv`Cmdlet은 Jobs.csv 파일을 가져오고 **Header** 매개 변수를 사용 하 여 변수를 적용 `$Header` 합니다. `$J`변수는 가져온 **PSCustomObject** 를 포함 하 고 PowerShell 콘솔에 개체를 표시 합니다.

### 예 5: CSV 파일을 사용 하 여 사용자 지정 개체 만들기

이 예제에서는 CSV 파일을 사용 하 여 PowerShell에서 사용자 지정 개체를 만드는 방법을 보여 줍니다.

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

Links.csv 파일을 만들려면 출력에 표시 된 값을 사용 합니다 `Get-Content` .

`Get-Content`Cmdlet은 Links.csv 파일을 표시 합니다. `Import-Csv`Cmdlet은 Links.csv 파일을 가져옵니다. **Header** 매개 변수는 속성 이름 **LinkId** 및 **TopicTitle** 를 지정 합니다. 개체는 변수에 저장 됩니다 `$A` . `Get-Member`Cmdlet은 **헤더** 매개 변수에서 속성 이름을 표시 합니다. `Where-Object`Cmdlet은 **별칭** 을 포함 하는 **TopicTitle** 속성을 사용 하 여 개체를 선택 합니다.

### 예 6: 값이 누락 된 CSV 가져오기

이 예에서는 `Import-Csv` CSV 파일의 머리글 행에 null 값 또는 빈 값이 포함 된 경우 PowerShell의 cmdlet이 응답 하는 방법을 보여 줍니다. `Import-Csv` 에서 반환 하는 개체의 속성 이름이 되는 누락 된 헤더 행의 기본 이름을 대체 `Import-Csv` 합니다.

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

Projects.csv 파일을 만들려면 예제의 출력에 표시 된 값을 사용 합니다 `Get-Content` .

`Get-Content`Cmdlet은 Projects.csv 파일을 표시 합니다. 머리글 행에서 **ProjectName** 과 **Completed** 사이의 값이 누락 되었습니다. `Import-Csv` **H1** 이 기본 헤더 이름이 기 때문에 cmdlet은 Projects.csv 파일을 가져오고 경고 메시지를 표시 합니다. `(Import-Csv -Path
.\Projects.csv).H1`명령은 **H1** 속성 값을 가져오고 경고를 표시 합니다.

## PARAMETERS

### -구분 기호

CSV 파일의 속성 값을 구분하는 구분 기호를 지정합니다.
기본값은 쉼표(,)입니다.

콜론(:)과 같은 문자를 입력합니다.
세미콜론 (;)을 지정 하려면 작은따옴표로 묶습니다.

파일의 실제 문자열 구분 기호 이외의 문자를 지정 하는 경우는 `Import-Csv` csv 문자열에서 개체를 만들 수 없으며 csv 문자열을 반환 합니다.

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

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `Default`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ASCII` ASCII (7 비트) 문자 집합을 사용 합니다.
- `BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.
- `Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).
- `OEM` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.
- `Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.
- `UTF7` 는 u t f-7을 사용 합니다.
- `UTF8` 는 u t f-8을 사용 합니다.
- `UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -헤더

가져온 파일의 대체 열 머리글 행을 지정합니다. 열 머리글은에서 만든 개체의 속성 이름을 결정 합니다 `Import-Csv` .

열 머리글을 쉼표로 구분 된 목록으로 입력 합니다. 머리글 문자열을 따옴표로 묶지 마세요. 각 열 머리글을 작은따옴표로 묶습니다.

데이터 열 보다 더 작은 수의 열 머리글을 입력 하면 나머지 데이터 열이 삭제 됩니다. 데이터 열 보다 많은 열 머리글을 입력 하면 빈 데이터 열이 포함 된 추가 열 머리글이 만들어집니다.

**Header** 매개 변수를 사용 하는 경우 CSV 파일에서 원래 머리글 행을 삭제 합니다. 그렇지 않으면는 `Import-Csv` 머리글 행의 항목에서 개체를 추가로 만듭니다.

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

### -LiteralPath

가져올 CSV 파일의 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

가져올 CSV 파일의 경로를 지정합니다.
에 대 한 경로를 파이프 할 수도 있습니다 `Import-Csv` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -UseCulture

현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다. 문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
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

경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Import-Csv` .

## 출력

### Object

이 cmdlet은 CSV 파일의 내용으로 설명 되는 개체를 반환 합니다.

## 참고

가져온 개체는 개체 유형의 CSV 버전 이므로 CSV가 아닌 버전의 개체 유형을 포맷 하는 PowerShell 유형 형식 지정 항목을 통해 인식 되지 않으며 형식이 지정 되지 않습니다.

명령의 결과는 `Import-Csv` 테이블 형식의 사용자 지정 개체를 구성 하는 문자열의 컬렉션입니다. 각 행은 별도의 문자열 이므로 개체의 **count** 속성을 사용 하 여 테이블 행 수를 계산할 수 있습니다. 열은 개체의 속성이고 행의 항목은 속성 값입니다.

열 머리글 행에 따라 열 수와 열 이름이 결정됩니다. 또한 열 이름은 개체의 속성 이름입니다. **Header** 매개 변수를 사용 하 여 열 머리글을 지정 하지 않는 한 첫 번째 행은 열 머리글로 해석 됩니다. 모든 행에 머리글 행보다 많은 값이 있으면 추가 값이 무시됩니다.

열 머리글 행이 값을 누락 하거나 null 또는 빈 값을 포함 하는 경우에는가 `Import-Csv` 누락 된 열 머리글 및 속성 이름에 대해 **H** 다음에 숫자를 사용 합니다.

CSV 파일에서 각 개체는 쉼표로 구분된 개체 속성 값 목록으로 표시됩니다. 속성 값은 개체의 **ToString ()** 메서드를 사용 하 여 문자열로 변환 되므로 속성 값의 이름으로 표시 됩니다. `Export-Csv` 는 개체의 메서드를 내보내지 않습니다.

## 관련 링크

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Export-Csv](Export-Csv.md)

[Get-Culture](Get-Culture.md)
