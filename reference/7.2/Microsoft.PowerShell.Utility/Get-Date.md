---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 8c0a1b7a14f5dfa071a85808f5d7dfba4d06048e
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "99599580"
---
# Get-Date

## 개요
현재 날짜 및 시간을 가져옵니다.

## SYNTAX

### 날짜 (기본값)

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### DateUFormat

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### UnixTimeSeconds

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### UnixTimeSecondsUFormat

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## 설명

`Get-Date`Cmdlet은 현재 날짜 또는 지정한 날짜를 나타내는 **DateTime** 개체를 가져옵니다. `Get-Date` 에서는 날짜 및 시간을 여러 .NET 및 UNIX 형식으로 지정할 수 있습니다. `Get-Date`를 사용 하 여 날짜 또는 시간 문자열을 생성 한 다음 다른 cmdlet 또는 프로그램으로 문자열을 보낼 수 있습니다.

`Get-Date` 컴퓨터의 문화권 설정을 사용 하 여 출력의 형식 지정 방법을 결정 합니다. 컴퓨터의 설정을 보려면를 사용 `(Get-Culture).DateTimeFormat` 합니다.

## 예제

### 예 1: 현재 날짜 및 시간 가져오기

이 예에서는 `Get-Date` 현재 시스템 날짜 및 시간을 표시 합니다. 출력은 자세한 날짜 및 자세한 시간 형식으로 되어 있습니다.

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### 예제 2: 현재 날짜 및 시간의 요소 가져오기

이 예제에서는를 사용 하 여 `Get-Date` 날짜 또는 시간 요소를 가져오는 방법을 보여 줍니다. 매개 변수는 **Date**, **Time** 또는 **DateTime** 인수를 사용 합니다.

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

`Get-Date`**date 인수와 함께** **displayhint** 매개 변수를 사용 하 여 날짜만 가져옵니다.

### 예제 3: .NET 서식 지정자를 사용 하 여 날짜 및 시간 가져오기

이 예제에서는 .NET 형식 지정자를 사용 하 여 출력 형식을 사용자 지정 합니다. 출력은 **문자열** 개체입니다.

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

`Get-Date`**format** 매개 변수를 사용 하 여 여러 형식 지정자를 지정 합니다.

이 예제에서 사용 되는 .NET 형식 지정자는 다음과 같이 정의 됩니다.

| 지정자 |                      정의                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | 요일-전체 이름                           |
| `MM`      | 월 번호                                          |
| `dd`      | 월의 날짜-2 자리                           |
| `yyyy`    | 4 자리 형식의 연도                                |
| `HH:mm`   | 24 시간 형식의 시간-초 없음                    |
| `K`       | UTC (Universal Time 좌표의)의 표준 시간대 오프셋 |

.NET 형식 지정자에 대 한 자세한 내용은 [사용자 지정 날짜 및 시간 형식 문자열](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)을 참조 하세요.

### 예제 4: UFormat 지정자를 사용 하 여 날짜 및 시간 가져오기

이 예제에서는 출력 형식을 사용자 지정 하는 데 몇 가지 **uformat** 형식 지정자를 사용 합니다.
출력은 **문자열** 개체입니다.

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

`Get-Date`**uformat** 매개 변수를 사용 하 여 여러 형식 지정자를 지정 합니다.

이 예제에 사용 된 **Uformat** 서식 지정자는 다음과 같이 정의 됩니다.

| 지정자 |                      정의                       |
| --------- | ----------------------------------------------------- |
| `%A`      | 요일-전체 이름                           |
| `%m`      | 월 번호                                          |
| `%d`      | 월의 날짜-2 자리                           |
| `%Y`      | 4 자리 형식의 연도                                |
| `%R`      | 24 시간 형식의 시간-초 없음                    |
| `%Z`      | UTC (Universal Time 좌표의)의 표준 시간대 오프셋 |

유효한 **uformat** 형식 지정자 목록은 [참고](#notes) 섹션을 참조 하세요.

### 예 5: 날짜의 날짜 가져오기

이 예에서는 속성을 사용 하 여 연간 일을 가져옵니다.

회교식 달력에는 366 일이 있는 윤년을 제외 하 고 365 일이 있습니다. 예를 들어, 2020 년 12 월 31 일은 366입니다.

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

`Get-Date` 는 세 개의 매개 변수를 사용 하 여 **년**, **월**, **일** 을 지정 합니다. 명령은 **DayofYear** 속성을 통해 결과가 계산 되도록 괄호를 사용 하 여 래핑됩니다.

### 예 6: 일광 절약 시간제에 따라 날짜가 조정 되었는지 확인

이 예제에서는 부울 메서드를 사용 하 여 날짜가 일광 절약 시간제에 따라 조정 되는지 확인 합니다.

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

변수는 `$DST` 의 결과를 저장 `Get-Date` 합니다. `$DST`**IsDaylightSavingTime** 메서드를 사용 하 여 일광 절약 시간제에 따라 날짜가 조정 되었는지 테스트 합니다.

### 예 7: 현재 시간을 UTC 시간으로 변환

이 예제에서 현재 시간은 UTC 시간으로 변환 됩니다. 시스템 로캘의 UTC 오프셋은 시간을 변환 하는 데 사용 됩니다. [메모](#notes) 섹션의 테이블에는 유효한 **uformat** 형식 지정 자가 나열 됩니다.

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

`Get-Date` 형식 지정자와 함께 **Uformat** 매개 변수를 사용 하 여 현재 시스템 날짜 및 시간을 표시 합니다. 형식 지정자 **% Z** 은 **(는)-07** 의 UTC 오프셋을 나타냅니다.

`$Time`변수는 현재 시스템 날짜 및 시간을 저장 합니다. `$Time`**ToUniversalTime ()** 메서드를 사용 하 여 컴퓨터의 UTC 오프셋을 기반으로 시간을 변환 합니다.

### 예 8: 타임 스탬프 만들기

이 예제에서 서식 지정자는 디렉터리 이름에 대 한 타임 스탬프 **문자열** 개체를 만듭니다. 타임 스탬프에는 날짜, 시간 및 UTC 오프셋이 포함 됩니다.

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

`$timestamp`변수는 명령 결과를 저장 `Get-Date` 합니다. `Get-Date`**format 매개 변수** 를 소문자의 형식 지정자와 함께 사용 하 여 `o` 타임 스탬프 **문자열** 개체를 만듭니다. 개체는 파이프라인에서로 전송 됩니다 `ForEach-Object` . **ScriptBlock** 에는 `$_` 현재 파이프라인 개체를 나타내는 변수가 포함 되어 있습니다. 타임 스탬프 문자열은 마침표로 대체 된 콜론으로 구분 됩니다.

`New-Item`**Path** 매개 변수를 사용 하 여 새 디렉터리의 위치를 지정 합니다. 경로는 변수를 `$timestamp` 디렉터리 이름으로 포함 합니다. **형식** 매개 변수는 디렉터리를 만들도록 지정 합니다.

### 예 9: Unix 타임 스탬프 변환

이 예에서는 Unix 시간 (1970-01-01 0:00:00 이후의 초 수로 나타냄)을 DateTime으로 변환 합니다.

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### 예 10: UTC로 해석 된 날짜 값 반환

이 예제에서는 날짜 값을 UTC와 동일 하 게 해석 하는 방법을 보여 줍니다. 예를 들어이 컴퓨터는 **태평양** 표준시로 설정 됩니다. 기본적으로 `Get-Date` 는 해당 표준 시간대에 대 한 값을 반환 합니다. **Asutc** 매개 변수를 사용 하 여 값을 해당 하는 UTC 시간으로 변환 합니다.

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## PARAMETERS

### -AsUTC

날짜 값을 해당 하는 UTC 시간으로 변환 합니다.

이 매개 변수는 PowerShell 7.1에서 도입 되었습니다.

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

### -날짜

날짜 및 시간을 지정합니다. Time은 선택 사항이 며 지정 되지 않은 경우 00:00:00을 반환 합니다.

시스템 로캘의 표준 형식으로 날짜 및 시간을 입력 합니다.

예를 들어 미국 영어:

`Get-Date -Date "6/25/2019 12:30:22"` 화요일, June 25, 2019 12:30:22 반환

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -일

표시되는 월의 날짜를 지정합니다. 1에서 31 사이의 값을 입력합니다.

지정 된 값이 한 달의 일 수보다 크면 PowerShell에서 해당 월에 일 수를 더 합니다. 예를 들어,는 `Get-Date -Month 2 -Day 31` **2 월 31 일** 이 아닌 **3 월 3** 일을 표시 합니다.

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

### -DisplayHint

표시되는 날짜 및 시간 요소를 결정합니다.

허용 되는 값은 다음과 같습니다.

- **날짜**: 날짜만 표시 합니다.
- **Time**: 시간만 표시 합니다.
- **DateTime**: 날짜와 시간을 표시 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -형식

형식 지정자가 나타내는 Microsoft .NET Framework 형식의 날짜 및 시간을 표시합니다.
**Format** 매개 변수는 **문자열** 개체를 출력 합니다.

사용 가능한 .NET 형식 지정자 목록은 [사용자 지정 날짜 및 시간 형식 문자열](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)을 참조 하세요.

**Format** 매개 변수를 사용 하는 경우 `Get-Date` 날짜를 표시 하는 데 필요한 **DateTime** 개체의 속성만 가져옵니다. 따라서 **DateTime** 개체의 일부 속성 및 메서드를 사용하지 못할 수 있습니다.

PowerShell 5.0부터 다음 추가 형식을 **Format** 매개 변수에 대 한 값으로 사용할 수 있습니다.

- **Filedate**. 현재 날짜를 현지 시간으로 표현 하는 파일 또는 경로입니다. 형식은 `yyyyMMdd` (4 자리 연도, 2 자리 월 및 2 자리 일을 사용 하는 대/소문자 구분)입니다. 다음은 그 예입니다. 
  20190627.

- **Filedateuniversal**. 현재 날짜를 UTC (universal time)로 표현 하는 파일 또는 경로에 대 한 친숙 한 표현입니다. 형식은입니다 `yyyyMMddZ` . 여기에는 4 자리 연도, 2 자리 월, 2 자리 날짜 및 문자를 UTC 표시기로 사용 하 여 대/소문자를 구분 합니다 `Z` . 예: 20190627Z

- **FileDateTime**. 현재 날짜와 시간을 24 시간 형식으로 표시 하는 파일 또는 경로에 대 한 친숙 한 표현입니다. 형식은 `yyyyMMddTHHmmssffff` (대/소문자 구분, 4 자리 연도, 2 자리 월, 2 자리 날짜, `T` 시간 구분 기호, 2 자리 시간, 2 자리 분, 2 자리 초 및 4 자리 밀리초)입니다. 예: 20190627T0840107271.

- **FileDateTimeUniversal**. 현재 날짜와 시간을 24 시간 형식으로 표시 하는 파일 또는 경로 (UTC)를 표시 합니다. 형식은 `yyyyMMddTHHmmssffffZ` (대/소문자 구분, 4 자리 연도, 2 자리 월, 2 자리 날짜, `T` 시간 구분 기호, 2 자리 시간, 2 자리 분, 2 자리 초, 4 자리 밀리초 및 `Z` UTC 표시기로 문자)입니다. 예: 20190627T1540500718Z

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -시간

표시되는 시간을 지정합니다. 0에서 23 사이의 값을 입력 합니다.

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

### -밀리초

날짜에서 밀리초를 지정합니다. 0에서 999 사이의 값을 입력합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### -분

표시되는 분을 지정합니다. 0에서 59 사이의 값을 입력 합니다.

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

### -월

표시되는 월을 지정합니다. 1에서 12 사이의 값을 입력 합니다.

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

### -초

표시되는 초를 지정합니다. 0에서 59 사이의 값을 입력 합니다.

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

### -UFormat

날짜 및 시간을 UNIX 형식으로 표시합니다. **Uformat** 매개 변수는 문자열 개체를 출력 합니다.

**Uformat** 지정자 앞에는 백분율 기호 ()가 있습니다 ( `%` 예: `%m` , `%d` 및) `%Y` . [참고](#notes) 섹션에는 유효한 **uformat 지정자** 의 테이블이 포함 되어 있습니다.

**Uformat** 매개 변수를 사용 하는 경우 `Get-Date` 날짜를 표시 하는 데 필요한 **DateTime** 개체의 속성만 가져옵니다. 따라서 **DateTime** 개체의 일부 속성 및 메서드를 사용하지 못할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnixTimeSeconds

0:00:00 1970 년 1 월 1 일 이후의 시간 (초)을 나타내는 날짜 및 시간입니다.

이 매개 변수는 PowerShell 7.1에서 도입 되었습니다.

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -연도

표시되는 연도를 지정합니다. 1에서 9999 사이의 값을 입력 합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 파이프라인 입력

`Get-Date` 파이프라인 입력을 허용 합니다. 예를 들어 `Get-ChildItem | Get-Date`입니다.

## 출력

### System.string 또는 System.string

`Get-Date`**format** 및 **uformat** 매개 변수를 사용 하는 경우를 제외 하 고는 **DateTime** 개체를 반환 합니다. **Format** 또는 **uformat** 매개 변수는 **문자열** 개체를 반환 합니다.

**DateTime** 개체가 문자열 입력을 필요로 하는 것과 같은 cmdlet으로 파이프라인으로 전송 되는 경우 `Add-Content` PowerShell은 개체를 **문자열** 개체로 변환 합니다.

메서드는 `(Get-Date).ToString()` **DateTime** 개체를 **문자열** 개체로 변환 합니다.

개체의 속성 및 메서드를 표시 하려면 개체를 파이프라인에서로 보냅니다 `Get-Member` .
예를 들어 `Get-Date | Get-Member`입니다.

## 참고

**DateTime** 개체는 시스템 로캘의 자세한 날짜 및 자세한 시간 형식입니다.

유효한 **Uformat 지정 자가** 다음 표에 표시 됩니다.

| 형식 지정자 |                                 의미                     |         예제          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | 요일-전체 이름                                             | 월요일                   |
| `%a` | 요일-약식 이름                                      | Mon                      |
| `%B` | 월 이름-전체                                                       | January                  |
| `%b` | 월 이름-약식                                                | 1월                      |
| `%C` | 궁서                                                                 | 2019의 경우 20              |
| `%c` | 날짜 및 시간-약식                                             | 6 월 27 08:44:18 2019 |
| `%D` | Mm/dd/yy 형식의 날짜                                                 | 06/27/19                 |
| `%d` | 월의 날짜-2 자리                                             | 05                       |
| `%e` | 월의 날짜-한 자리로 된 경우 공백을 앞에 옵니다.           | \<space\>5               |
| `%F` | YYYY-mm-dd 형식의 날짜 (% Y-% m-% d) (ISO 8601 날짜 형식) | 2019-06-27               |
| `%G` | ' Y '와 동일                                                             |                          |
| `%g` | ' Y '와 동일                                                             |                          |
| `%H` | 24 시간 형식의 시간                                                  | 17                       |
| `%h` | ' B '와 동일                                                             |                          |
| `%I` | 12 시간 형식의 시간                                                  | 05                       |
| `%j` | 연간 일자                                                         | 1-366                    |
| `%k` | ' H '와 동일                                                             |                          |
| `%l` | ' I '와 동일 (대문자 I)                                              | 05                       |
| `%M` | 분                                                                 | 35                       |
| `%m` | 월 번호                                                            | 06                       |
| `%n` | 줄 바꿈 문자                                                       |                          |
| `%p` | AM 또는 PM                                                                |                          |
| `%R` | 24 시간 형식의 시간-초 없음                                      | 17:45                    |
| `%r` | 12 시간 형식의 시간                                                  | 오전 09:15:36              |
| `%S` | 초                                                                 | 05                       |
| `%s` | 1970 00:00:00 1 월 1 일 이후 경과 된 시간 (초)                          | 1150451174               |
| `%t` | 가로 탭 문자                                                |                          |
| `%T` | 24 시간 형식의 시간                                                  | 17:45:52                 |
| `%U` | ' W '와 동일                                                             |                          |
| `%u` | 요일-번호                                                | 일요일 = 0               |
| `%V` | 연간 주                                                        | 01-53                    |
| `%w` | ' U '와 동일                                                             |                          |
| `%W` | 연간 주                                                        | 00-52                    |
| `%X` | ' T '와 동일                                                             |                          |
| `%x` | 로캘의 표준 형식 날짜                                      | 영어 (미국)의 경우 06/27/19  |
| `%Y` | 4 자리 형식의 연도                                                  | 2019                     |
| `%y` | 2 자리 형식의 연도                                                  | 19                       |
| `%Z` | UTC (Universal Time 좌표의)의 표준 시간대 오프셋                   | -07                      |

## 관련 링크

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Culture](Get-Culture.md)

[Get-Member](Get-Member.md)

[New-Item](../Microsoft.PowerShell.Management/New-Item.md)

[New-TimeSpan](New-TimeSpan.md)

[Set-Date](Set-Date.md)
