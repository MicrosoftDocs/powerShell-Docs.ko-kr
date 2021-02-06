---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 0775940f210cb028d7a0919bb8e5ca9f256b70d8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600629"
---
# <span data-ttu-id="858d9-102">Get-Host</span><span class="sxs-lookup"><span data-stu-id="858d9-102">Get-Host</span></span>

## <span data-ttu-id="858d9-103">개요</span><span class="sxs-lookup"><span data-stu-id="858d9-103">SYNOPSIS</span></span>
<span data-ttu-id="858d9-104">현재 호스트 프로그램을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-104">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="858d9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="858d9-105">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="858d9-106">설명</span><span class="sxs-lookup"><span data-stu-id="858d9-106">DESCRIPTION</span></span>

<span data-ttu-id="858d9-107">`Get-Host`Cmdlet은 Windows PowerShell을 호스트 하는 프로그램을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-107">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="858d9-108">기본 표시에는 호스트가 사용 중인 Windows PowerShell 버전 번호 및 현재 국가별 및 언어 설정이 포함되지만 호스트 개체에는 현재 실행 중인 Windows PowerShell 버전, Windows PowerShell의 현재 문화권 및 UI 문화권에 대한 자세한 정보 등 다양한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-108">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="858d9-109">이 cmdlet을 사용 하 여 텍스트 및 배경색과 같은 호스트 프로그램 사용자 인터페이스의 기능을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-109">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="858d9-110">예제</span><span class="sxs-lookup"><span data-stu-id="858d9-110">EXAMPLES</span></span>

### <span data-ttu-id="858d9-111">예 1: PowerShell 콘솔 호스트에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="858d9-111">Example 1: Get information about the PowerShell console host</span></span>

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

<span data-ttu-id="858d9-112">이 명령은 이 예제에서 Windows PowerShell의 현재 호스트 프로그램인 Windows PowerShell 콘솔에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-112">This command displays information about the Windows PowerShell console, which is the current host program for Windows PowerShell in this example.</span></span> <span data-ttu-id="858d9-113">여기에는 호스트 이름, 호스트에서 실행 중인 Windows PowerShell 버전, 현재 문화권 및 UI 문화권이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-113">It includes the name of the host, the version of Windows PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="858d9-114">Version, UI, CurrentCulture, CurrentUICulture, PrivateData 및 Runspace 속성에는 각각 유용한 속성이 있는 개체가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-114">The Version, UI, CurrentCulture, CurrentUICulture, PrivateData, and Runspace properties each contain an object with very useful properties.</span></span> <span data-ttu-id="858d9-115">뒤에 나오는 예제에서 이러한 속성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-115">Later examples examine these properties.</span></span>

### <span data-ttu-id="858d9-116">예 2: PowerShell 창 크기 조정</span><span class="sxs-lookup"><span data-stu-id="858d9-116">Example 2: Resize the PowerShell window</span></span>

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="858d9-117">이 명령은 Windows PowerShell 창의 크기를 10픽셀 x 10픽셀로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-117">This command resizes the Windows PowerShell window to 10 pixels by 10 pixels.</span></span>

### <span data-ttu-id="858d9-118">예 3: 호스트의 PowerShell 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="858d9-118">Example 3: Get the PowerShell version for the host</span></span>

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="858d9-119">이 명령은 호스트에서 실행 중인 Windows PowerShell 버전에 대한 자세한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-119">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="858d9-120">이러한 값은 볼 수는 있지만 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-120">You can view, but not change, these values.</span></span>

<span data-ttu-id="858d9-121">의 Version 속성에는 `Get-Host` **system.object** 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-121">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="858d9-122">이 명령은 파이프라인 연산자 (|)를 사용 하 여 버전 개체를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="858d9-122">This command uses a pipeline operator (|) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="858d9-123">이 `Format-List` 명령은 all (\*) 값과 함께 *Property* 매개 변수를 사용 하 여 버전 개체의 모든 속성과 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-123">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="858d9-124">예 4: 호스트에 대 한 현재 문화권 가져오기</span><span class="sxs-lookup"><span data-stu-id="858d9-124">Example 4: Get the current culture for the host</span></span>

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

<span data-ttu-id="858d9-125">이 명령은 호스트에서 실행 중인 Windows PowerShell에 설정된 현재 문화권에 대한 자세한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-125">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="858d9-126">이는 cmdlet에서 반환 되는 정보와 동일 합니다 `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="858d9-126">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="858d9-127">마찬가지로 **CurrentUICulture** 속성은가 반환 하는 것과 동일한 개체를 반환 합니다 `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="858d9-127">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="858d9-128">호스트 개체의 **CurrentCulture** 속성에는 System.object. **CultureInfo** 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-128">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="858d9-129">이 명령은 파이프라인 연산자 (|)를 사용 하 여 **CultureInfo** 개체를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="858d9-129">This command uses a pipeline operator (|) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="858d9-130">이 `Format-List` 명령은 all (\*) 값과 함께 *Property* 매개 변수를 사용 하 여 **CultureInfo** 개체의 모든 속성과 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-130">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="858d9-131">예 5: 현재 문화권에 대 한 DateTimeFormat 가져오기</span><span class="sxs-lookup"><span data-stu-id="858d9-131">Example 5: Get the DateTimeFormat for the current culture</span></span>

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

<span data-ttu-id="858d9-132">이 명령은 Windows PowerShell에 사용 중인 현재 문화권의 DateTimeFormat에 대한 자세한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-132">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="858d9-133">호스트 개체의 **CurrentCulture** 속성에는 여러 유용한 속성이 있는 **CultureInfo** 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-133">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="858d9-134">**DateTimeFormat** 속성 중 하나에는 유용한 속성이 많은 **DateTimeFormatInfo** 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-134">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="858d9-135">개체 속성에 저장 된 개체의 형식을 찾으려면 cmdlet을 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="858d9-135">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="858d9-136">개체의 속성 값을 표시 하려면 cmdlet을 사용 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="858d9-136">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="858d9-137">예제 6: 호스트에 대 한 RawUI 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="858d9-137">Example 6: Get the RawUI property for the host</span></span>

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

<span data-ttu-id="858d9-138">이 명령은 호스트 개체의 **RawUI** 속성 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-138">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="858d9-139">이러한 값을 변경하면 호스트 프로그램의 모양을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-139">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="858d9-140">예 7: PowerShell 콘솔의 배경색 설정</span><span class="sxs-lookup"><span data-stu-id="858d9-140">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

<span data-ttu-id="858d9-141">이 명령은 Windows PowerShell 콘솔의 배경색을 검은색으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-141">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="858d9-142">**Cls** 명령은 `Clear-Host` 화면을 지우고 전체 화면을 새 색으로 변경 하는 함수에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-142">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="858d9-143">이 변경 내용은 현재 세션에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-143">This change is effective only in the current session.</span></span> <span data-ttu-id="858d9-144">모든 세션에 대해 콘솔 배경색을 변경하려면 Windows PowerShell 프로필에 명령을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-144">To change the background color of the console for all sessions, add the command to your Windows PowerShell profile.</span></span>

### <span data-ttu-id="858d9-145">예 8: 오류 메시지의 배경색 설정</span><span class="sxs-lookup"><span data-stu-id="858d9-145">Example 8: Set the background color for error messages</span></span>

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="858d9-146">이 명령은 오류 메시지의 배경색을 흰색으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-146">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="858d9-147">이 명령은 `$Host` 현재 호스트 프로그램의 호스트 개체를 포함 하는 자동 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-147">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="858d9-148">`Get-Host` 는를 포함 하는 동일한 개체를 반환 `$Host` 하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-148">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="858d9-149">이 명령은의 **PrivateData** 속성을 `$Host` ErrorBackgroundColor 속성으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-149">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="858d9-150">에서 개체의 모든 속성을 확인 하려면 `$Host` 입니다. PrivateData 속성에를 입력 `$host.privatedata | format-list *` 합니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-150">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.privatedata | format-list *`.</span></span>

## <span data-ttu-id="858d9-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="858d9-151">PARAMETERS</span></span>

### <span data-ttu-id="858d9-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="858d9-152">CommonParameters</span></span>

<span data-ttu-id="858d9-153">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="858d9-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="858d9-154">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="858d9-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="858d9-155">입력</span><span class="sxs-lookup"><span data-stu-id="858d9-155">INPUTS</span></span>

### <span data-ttu-id="858d9-156">없음</span><span class="sxs-lookup"><span data-stu-id="858d9-156">None</span></span>
<span data-ttu-id="858d9-157">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="858d9-158">출력</span><span class="sxs-lookup"><span data-stu-id="858d9-158">OUTPUTS</span></span>

### <span data-ttu-id="858d9-159">System.web.. n a m.</span><span class="sxs-lookup"><span data-stu-id="858d9-159">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="858d9-160">`Get-Host`**system.object** .. i n a m.</span><span class="sxs-lookup"><span data-stu-id="858d9-160">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="858d9-161">참고</span><span class="sxs-lookup"><span data-stu-id="858d9-161">NOTES</span></span>

<span data-ttu-id="858d9-162">`$Host`자동 변수는에서 반환 하는 것과 동일한 개체를 포함 하 `Get-Host` 고 동일한 방식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-162">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="858d9-163">마찬가지로 `$PSCulture` 및 `$PSUICulture` 자동 변수에는 호스트 개체의 CurrentCulture 및 CurrentUICulture 속성에 포함 된 것과 동일한 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-163">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="858d9-164">이러한 기능을 서로 교환해서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="858d9-164">You can use these features interchangeably.</span></span>

<span data-ttu-id="858d9-165">자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="858d9-165">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="858d9-166">관련 링크</span><span class="sxs-lookup"><span data-stu-id="858d9-166">RELATED LINKS</span></span>

[<span data-ttu-id="858d9-167">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="858d9-167">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="858d9-168">Read-Host</span><span class="sxs-lookup"><span data-stu-id="858d9-168">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="858d9-169">Write-Host</span><span class="sxs-lookup"><span data-stu-id="858d9-169">Write-Host</span></span>](Write-Host.md)

