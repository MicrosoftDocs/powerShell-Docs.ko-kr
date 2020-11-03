---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 45a7a8a44bdb116e2e7d9327fd23972cb7af1246
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209316"
---
# Get-Host

## 개요
현재 호스트 프로그램을 나타내는 개체를 가져옵니다.

## SYNTAX

```
Get-Host [<CommonParameters>]
```

## 설명

`Get-Host`Cmdlet은 Windows PowerShell을 호스트 하는 프로그램을 나타내는 개체를 가져옵니다.

기본 표시에는 호스트가 사용 중인 Windows PowerShell 버전 번호 및 현재 국가별 및 언어 설정이 포함되지만 호스트 개체에는 현재 실행 중인 Windows PowerShell 버전, Windows PowerShell의 현재 문화권 및 UI 문화권에 대한 자세한 정보 등 다양한 정보가 포함되어 있습니다. 이 cmdlet을 사용 하 여 텍스트 및 배경색과 같은 호스트 프로그램 사용자 인터페이스의 기능을 사용자 지정할 수도 있습니다.

## 예제

### 예 1: PowerShell 콘솔 호스트에 대 한 정보 가져오기

```
PS C:\> Get-Host
Name             : ConsoleHost
Version          : 2.0
InstanceId       : e4e0ab54-cc5e-4261-9117-4081f20ce7a2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : en-US
CurrentUICulture : en-US
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

이 명령은 이 예제에서 Windows PowerShell의 현재 호스트 프로그램인 Windows PowerShell 콘솔에 대한 정보를 표시합니다. 여기에는 호스트 이름, 호스트에서 실행 중인 Windows PowerShell 버전, 현재 문화권 및 UI 문화권이 포함됩니다.

Version, UI, CurrentCulture, CurrentUICulture, PrivateData 및 Runspace 속성에는 각각 유용한 속성이 있는 개체가 포함되어 있습니다. 뒤에 나오는 예제에서 이러한 속성을 검사합니다.

### 예 2: PowerShell 창 크기 조정

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

이 명령은 Windows PowerShell 창의 크기를 10픽셀 x 10픽셀로 조정합니다.

### 예 3: 호스트의 PowerShell 버전 가져오기

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

이 명령은 호스트에서 실행 중인 Windows PowerShell 버전에 대한 자세한 정보를 가져옵니다.
이러한 값은 볼 수는 있지만 변경할 수 없습니다.

의 Version 속성에는 `Get-Host` **system.object** 개체가 포함 되어 있습니다. 이 명령은 파이프라인 연산자 (|)를 사용 하 여 버전 개체를 cmdlet으로 보냅니다 `Format-List` . 이 `Format-List` 명령은 all (*) 값과 함께 *Property* 매개 변수를 사용 하 여 버전 개체의 모든 속성과 속성 값을 표시 합니다.

### 예 4: 호스트에 대 한 현재 문화권 가져오기

```powershell
PS C:\> (Get-Host).CurrentCulture | Format-List -Property *
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
IsReadOnly                     : False
```

이 명령은 호스트에서 실행 중인 Windows PowerShell에 설정된 현재 문화권에 대한 자세한 정보를 가져옵니다. 이는 cmdlet에서 반환 되는 정보와 동일 합니다 `Get-Culture` .

마찬가지로 **CurrentUICulture** 속성은가 반환 하는 것과 동일한 개체를 반환 합니다 `Get-UICulture` .

호스트 개체의 **CurrentCulture** 속성에는 System.object. **CultureInfo** 개체가 포함 되어 있습니다. 이 명령은 파이프라인 연산자 (|)를 사용 하 여 **CultureInfo** 개체를 cmdlet으로 보냅니다 `Format-List` . 이 `Format-List` 명령은 all (*) 값과 함께 *Property* 매개 변수를 사용 하 여 **CultureInfo** 개체의 모든 속성과 속성 값을 표시 합니다.

### 예 5: 현재 문화권에 대 한 DateTimeFormat 가져오기

```powershell
PS C:\> (Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *
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
MonthGenitiveNames               : {January, February, March, April...}
```

이 명령은 Windows PowerShell에 사용 중인 현재 문화권의 DateTimeFormat에 대한 자세한 정보를 반환합니다.

호스트 개체의 **CurrentCulture** 속성에는 여러 유용한 속성이 있는 **CultureInfo** 개체가 포함 되어 있습니다. **DateTimeFormat** 속성 중 하나에는 유용한 속성이 많은 **DateTimeFormatInfo** 개체가 포함 되어 있습니다.

개체 속성에 저장 된 개체의 형식을 찾으려면 cmdlet을 사용 합니다 `Get-Member` . 개체의 속성 값을 표시 하려면 cmdlet을 사용 합니다 `Format-List` .

### 예제 6: 호스트에 대 한 RawUI 속성 가져오기

```
PS C:\> (Get-Host).UI.RawUI | Format-List -Property *
ForegroundColor       : DarkYellow
BackgroundColor       : DarkBlue
CursorPosition        : 0,390
WindowPosition        : 0,341
CursorSize            : 25
BufferSize            : 120,3000
WindowSize            : 120,50
MaxWindowSize         : 120,81
MaxPhysicalWindowSize : 182,81
KeyAvailable          : False
WindowTitle           : Windows PowerShell 2.0 (04/11/2008 00:08:14)
```

이 명령은 호스트 개체의 **RawUI** 속성 속성을 표시 합니다. 이러한 값을 변경하면 호스트 프로그램의 모양을 변경할 수 있습니다.

### 예 7: PowerShell 콘솔의 배경색 설정

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

이 명령은 Windows PowerShell 콘솔의 배경색을 검은색으로 변경합니다. **Cls** 명령은 `Clear-Host` 화면을 지우고 전체 화면을 새 색으로 변경 하는 함수에 대 한 별칭입니다.

이 변경 내용은 현재 세션에서만 적용됩니다. 모든 세션에 대해 콘솔 배경색을 변경하려면 Windows PowerShell 프로필에 명령을 추가합니다.

### 예 8: 오류 메시지의 배경색 설정

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

이 명령은 오류 메시지의 배경색을 흰색으로 변경합니다.

이 명령은 `$Host` 현재 호스트 프로그램의 호스트 개체를 포함 하는 자동 변수를 사용 합니다. `Get-Host` 는를 포함 하는 동일한 개체를 반환 `$Host` 하므로 서로 바꿔 사용할 수 있습니다.

이 명령은의 **PrivateData** 속성을 `$Host` ErrorBackgroundColor 속성으로 사용 합니다. 에서 개체의 모든 속성을 확인 하려면 `$Host` 입니다. PrivateData 속성에를 입력 `$host.privatedata | format-list *` 합니다.

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.web.. n a m.

`Get-Host`**system.object** .. i n a m.

## 참고

`$Host`자동 변수는에서 반환 하는 것과 동일한 개체를 포함 하 `Get-Host` 고 동일한 방식으로 사용할 수 있습니다. 마찬가지로 `$PSCulture` 및 `$PSUICulture` 자동 변수에는 호스트 개체의 CurrentCulture 및 CurrentUICulture 속성에 포함 된 것과 동일한 개체가 포함 되어 있습니다. 이러한 기능을 서로 교환해서 사용할 수 있습니다.

자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

## 관련 링크

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Read-Host](Read-Host.md)

[Write-Host](Write-Host.md)

