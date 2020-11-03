---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: 1f4b18899c3c62eefe1beab212ad1143fed402be
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239974"
---
# <span data-ttu-id="d08dc-103">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="d08dc-103">Get-Culture</span></span>

## <span data-ttu-id="d08dc-104">개요</span><span class="sxs-lookup"><span data-stu-id="d08dc-104">SYNOPSIS</span></span>
<span data-ttu-id="d08dc-105">운영 체제의 현재 문화권 집합을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-105">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="d08dc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d08dc-106">SYNTAX</span></span>

### <span data-ttu-id="d08dc-107">CurrentCulture (기본값)</span><span class="sxs-lookup"><span data-stu-id="d08dc-107">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="d08dc-108">속성</span><span class="sxs-lookup"><span data-stu-id="d08dc-108">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="d08dc-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d08dc-109">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="d08dc-110">설명</span><span class="sxs-lookup"><span data-stu-id="d08dc-110">DESCRIPTION</span></span>

<span data-ttu-id="d08dc-111">`Get-Culture`Cmdlet은 현재 문화권 설정에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-111">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span> <span data-ttu-id="d08dc-112">여기에는 자판 배열, 숫자, 통화 및 날짜와 같은 항목의 표시 형식 등 시스템의 현재 언어 설정에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-112">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="d08dc-113">또한 cmdlet을 사용 하 여 `Get-UICulture` 시스템에서 현재 사용자 인터페이스 문화권을 가져오고 국가별 모듈의 [Set-culture](/powershell/module/international/set-culture) cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-113">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture) cmdlet in the International module.</span></span> <span data-ttu-id="d08dc-114">UI(사용자 인터페이스) 문화권에 따라 메뉴와 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-114">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="d08dc-115">예제</span><span class="sxs-lookup"><span data-stu-id="d08dc-115">EXAMPLES</span></span>

### <span data-ttu-id="d08dc-116">예제 1: 문화권 설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="d08dc-116">Example 1: Get culture settings</span></span>

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="d08dc-117">이 명령은 컴퓨터의 국가별 설정에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-117">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="d08dc-118">예제 2: culture 개체의 속성 서식 지정</span><span class="sxs-lookup"><span data-stu-id="d08dc-118">Example 2: Format the properties of a culture object</span></span>

```powershell
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
IsReadOnly                     : False

PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False

PS C:\> $C.DateTimeFormat
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

PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

<span data-ttu-id="d08dc-119">이 예제에서는 문화권 개체에 있는 방대한 분량의 데이터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-119">This example demonstrates the vast amount of data in the culture object.</span></span> <span data-ttu-id="d08dc-120">이 예제는 개체의 속성 및 하위 속성을 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-120">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="d08dc-121">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Culture` 컴퓨터의 현재 문화권 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-121">The first command uses the `Get-Culture` cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="d08dc-122">결과 문화권 개체를 변수에 저장 합니다 `$C` .</span><span class="sxs-lookup"><span data-stu-id="d08dc-122">It stores the resulting culture object in the `$C` variable.</span></span>

<span data-ttu-id="d08dc-123">두 번째 명령은 문화권 개체의 모든 속성을 표시하고</span><span class="sxs-lookup"><span data-stu-id="d08dc-123">The second command displays all of the properties of the culture object.</span></span> <span data-ttu-id="d08dc-124">파이프라인 연산자 ()를 사용 하 여 `|` 문화권 개체를 `$C` cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="d08dc-124">It uses a pipeline operator (`|`) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span> <span data-ttu-id="d08dc-125">**Property** 매개 변수를 사용 하 여 `*` 개체의 모든 () 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-125">It uses the **Property** parameter to display all (`*`) properties of the object.</span></span> <span data-ttu-id="d08dc-126">이 명령은로 약식으로 지정할 수 있습니다 `$c | fl *` .</span><span class="sxs-lookup"><span data-stu-id="d08dc-126">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="d08dc-127">나머지 명령은 점 표기법을 사용하여 개체 속성의 값을 표시하면서 문화권 개체의 속성을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-127">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span> <span data-ttu-id="d08dc-128">이 표기법을 사용하여 개체의 모든 속성 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-128">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="d08dc-129">세 번째 명령은 점 표기법을 사용 하 여 문화권 개체의 **Calendar** 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-129">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="d08dc-130">네 번째 명령은 점 표기법을 사용 하 여 문화권 개체의 **DataTimeFormat** 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-130">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="d08dc-131">많은 개체 속성은 속성을 포함하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-131">Many object properties have properties.</span></span> <span data-ttu-id="d08dc-132">다섯 번째 명령은 점 표기법을 사용 하 여 **DateTimeFormat** 속성의 **FirstDayOfWeek** 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-132">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="d08dc-133">예 3: 특정 문화권 가져오기</span><span class="sxs-lookup"><span data-stu-id="d08dc-133">Example 3: Get a specific culture</span></span>

<span data-ttu-id="d08dc-134">프랑스의 프랑스어에 대 한 CultureInfo 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-134">Get the CultureInfo object for French in France.</span></span>

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## <span data-ttu-id="d08dc-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d08dc-135">PARAMETERS</span></span>

### <span data-ttu-id="d08dc-136">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d08dc-136">-ListAvailable</span></span>

<span data-ttu-id="d08dc-137">현재 운영 체제에서 지 원하는 모든 문화권을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-137">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="d08dc-138">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-138">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d08dc-139">-Name</span><span class="sxs-lookup"><span data-stu-id="d08dc-139">-Name</span></span>

<span data-ttu-id="d08dc-140">이름을 기준으로 특정 문화권을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-140">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="d08dc-141">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-141">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d08dc-142">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="d08dc-142">-NoUserOverrides</span></span>

<span data-ttu-id="d08dc-143">현재 문화권에 대 한 사용자 변경 내용을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-143">Ignore user changes for current culture.</span></span>

<span data-ttu-id="d08dc-144">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-144">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CurrentCulture, Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d08dc-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d08dc-145">CommonParameters</span></span>

<span data-ttu-id="d08dc-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d08dc-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d08dc-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d08dc-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d08dc-148">입력</span><span class="sxs-lookup"><span data-stu-id="d08dc-148">INPUTS</span></span>

### <span data-ttu-id="d08dc-149">없음</span><span class="sxs-lookup"><span data-stu-id="d08dc-149">None</span></span>

<span data-ttu-id="d08dc-150">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d08dc-151">출력</span><span class="sxs-lookup"><span data-stu-id="d08dc-151">OUTPUTS</span></span>

### <span data-ttu-id="d08dc-152">System.object. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="d08dc-152">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="d08dc-153">`Get-Culture` 현재 문화권을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-153">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="d08dc-154">참고</span><span class="sxs-lookup"><span data-stu-id="d08dc-154">NOTES</span></span>

<span data-ttu-id="d08dc-155">및 변수를 사용할 수도 `$PsCulture` 있습니다 `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="d08dc-155">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="d08dc-156">`$PsCulture`변수는 현재 문화권의 이름을 저장 하 고 변수는 `$PsUICulture` 현재 UI 문화권의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d08dc-156">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="d08dc-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d08dc-157">RELATED LINKS</span></span>

[<span data-ttu-id="d08dc-158">설정-문화권</span><span class="sxs-lookup"><span data-stu-id="d08dc-158">Set-Culture</span></span>](/powershell/module/international/set-culture)

[<span data-ttu-id="d08dc-159">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="d08dc-159">Get-UICulture</span></span>](Get-UICulture.md)
