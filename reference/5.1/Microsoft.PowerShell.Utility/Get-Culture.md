---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: d7e9ebd56db3ad9de2bfbcec62f73f1f8c0e2eaa
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209064"
---
# Get-Culture

## 개요
운영 체제의 현재 문화권 집합을 가져옵니다.

## SYNTAX

```
Get-Culture [<CommonParameters>]
```

## 설명
**Get culture** cmdlet은 현재 문화권 설정에 대 한 정보를 가져옵니다.
여기에는 자판 배열, 숫자, 통화 및 날짜와 같은 항목의 표시 형식 등 시스템의 현재 언어 설정에 대한 정보가 포함됩니다.

Get-UICulture cmdlet을 사용할 수도 있습니다 .이 cmdlet은 시스템에서 현재 사용자 인터페이스 문화권을 가져오고 국가별 모듈의 [Set-culture](https://go.microsoft.com/fwlink/?LinkID=242258) cmdlet을 가져옵니다.
UI(사용자 인터페이스) 문화권에 따라 메뉴와 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다.

## 예제

### 예제 1: 문화권 설정 가져오기

```
PS C:\> Get-Culture
```

이 명령은 컴퓨터의 국가별 설정에 대한 정보를 표시합니다.

### 예제 2: culture 개체의 속성 서식 지정

```
PS C:\> $C = Get-Culture
PS C:\> $C | Format-List -Property *
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False PS C:\> $C.DateTimeFormat
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...} PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

이 예제에서는 문화권 개체에 있는 방대한 분량의 데이터를 보여 줍니다.
이 예제는 개체의 속성 및 하위 속성을 표시하는 방법을 보여 줍니다.

첫 번째 명령은 **Get Culture** cmdlet을 사용 하 여 컴퓨터의 현재 문화권 설정을 가져옵니다.
결과 문화권 개체를 $C 변수에 저장 합니다.

두 번째 명령은 문화권 개체의 모든 속성을 표시하고
파이프라인 연산자 (|)를 사용 하 여 $C의 culture 개체를 Format-List cmdlet으로 보냅니다.
*Property* 매개 변수를 사용 하 여 개체의 모든 (*) 속성을 표시 합니다.
이 명령은로 약식으로 지정할 수 있습니다 `$c | fl *` .

나머지 명령은 점 표기법을 사용하여 개체 속성의 값을 표시하면서 문화권 개체의 속성을 살펴봅니다.
이 표기법을 사용하여 개체의 모든 속성 값을 표시할 수 있습니다.

세 번째 명령은 점 표기법을 사용하여 문화권 개체의 Calendar 속성 값을 표시합니다.

네 번째 명령은 점 표기법을 사용하여 문화권 개체의 DataTimeFormat 속성 값을 표시합니다.

많은 개체 속성은 속성을 포함하고 있습니다.
다섯 번째 명령은 점 표기법을 사용하여 DateTimeFormat 속성의 FirstDayOfWeek 속성 값을 표시합니다.

## PARAMETERS

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.object. CultureInfo
**Get culture** 는 현재 문화권을 나타내는 개체를 반환 합니다.

## 참고

* $PsCulture 및 $PsUICulture 변수를 사용할 수도 있습니다. $PsCulture 변수는 현재 문화권의 이름을 저장하고 $PsUICulture 변수는 현재 UI 문화권의 이름을 저장합니다.

*

## 관련 링크

[설정-문화권](/powershell/module/internationalcmdlets/set-culture)

[Get-UICulture](Get-UICulture.md)
