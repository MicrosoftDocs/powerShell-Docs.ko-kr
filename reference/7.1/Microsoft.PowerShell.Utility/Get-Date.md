---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 34b0d7833d858a8b71c28d0f872ddb9e4948b76d
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514986"
---
# <span data-ttu-id="97188-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="97188-103">Get-Date</span></span>

## <span data-ttu-id="97188-104">개요</span><span class="sxs-lookup"><span data-stu-id="97188-104">SYNOPSIS</span></span>
<span data-ttu-id="97188-105">현재 날짜 및 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-105">Gets the current date and time.</span></span>

## <span data-ttu-id="97188-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97188-106">SYNTAX</span></span>

### <span data-ttu-id="97188-107">날짜 (기본값)</span><span class="sxs-lookup"><span data-stu-id="97188-107">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="97188-108">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="97188-108">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="97188-109">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="97188-109">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="97188-110">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="97188-110">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="97188-111">설명</span><span class="sxs-lookup"><span data-stu-id="97188-111">DESCRIPTION</span></span>

<span data-ttu-id="97188-112">`Get-Date`Cmdlet은 현재 날짜 또는 지정한 날짜를 나타내는 **DateTime** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-112">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="97188-113">`Get-Date` 에서는 날짜 및 시간을 여러 .NET 및 UNIX 형식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-113">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="97188-114">`Get-Date`를 사용 하 여 날짜 또는 시간 문자열을 생성 한 다음 다른 cmdlet 또는 프로그램으로 문자열을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-114">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="97188-115">`Get-Date` 컴퓨터의 문화권 설정을 사용 하 여 출력의 형식 지정 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-115">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="97188-116">컴퓨터의 설정을 보려면를 사용 `(Get-Culture).DateTimeFormat` 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-116">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="97188-117">예제</span><span class="sxs-lookup"><span data-stu-id="97188-117">EXAMPLES</span></span>

### <span data-ttu-id="97188-118">예 1: 현재 날짜 및 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="97188-118">Example 1: Get the current date and time</span></span>

<span data-ttu-id="97188-119">이 예에서는 `Get-Date` 현재 시스템 날짜 및 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-119">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="97188-120">출력은 자세한 날짜 및 자세한 시간 형식으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-120">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="97188-121">예제 2: 현재 날짜 및 시간의 요소 가져오기</span><span class="sxs-lookup"><span data-stu-id="97188-121">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="97188-122">이 예제에서는를 사용 하 여 `Get-Date` 날짜 또는 시간 요소를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="97188-122">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="97188-123">매개 변수는 **Date**, **Time** 또는 **DateTime** 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-123">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="97188-124">`Get-Date`**date 인수와 함께** **displayhint** 매개 변수를 사용 하 여 날짜만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-124">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="97188-125">예제 3: .NET 서식 지정자를 사용 하 여 날짜 및 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="97188-125">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="97188-126">이 예제에서는 .NET 형식 지정자를 사용 하 여 출력 형식을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-126">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="97188-127">출력은 **문자열** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-127">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="97188-128">`Get-Date`**format** 매개 변수를 사용 하 여 여러 형식 지정자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-128">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="97188-129">이 예제에서 사용 되는 .NET 형식 지정자는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-129">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="97188-130">지정자</span><span class="sxs-lookup"><span data-stu-id="97188-130">Specifier</span></span> |                      <span data-ttu-id="97188-131">정의</span><span class="sxs-lookup"><span data-stu-id="97188-131">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="97188-132">요일-전체 이름</span><span class="sxs-lookup"><span data-stu-id="97188-132">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="97188-133">월 번호</span><span class="sxs-lookup"><span data-stu-id="97188-133">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="97188-134">월의 날짜-2 자리</span><span class="sxs-lookup"><span data-stu-id="97188-134">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="97188-135">4 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="97188-135">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="97188-136">24 시간 형식의 시간-초 없음</span><span class="sxs-lookup"><span data-stu-id="97188-136">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="97188-137">UTC (Universal Time 좌표의)의 표준 시간대 오프셋</span><span class="sxs-lookup"><span data-stu-id="97188-137">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="97188-138">.NET 형식 지정자에 대 한 자세한 내용은 [사용자 지정 날짜 및 시간 형식 문자열](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97188-138">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="97188-139">예제 4: UFormat 지정자를 사용 하 여 날짜 및 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="97188-139">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="97188-140">이 예제에서는 출력 형식을 사용자 지정 하는 데 몇 가지 **uformat** 형식 지정자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-140">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="97188-141">출력은 **문자열** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-141">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="97188-142">`Get-Date`**uformat** 매개 변수를 사용 하 여 여러 형식 지정자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-142">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="97188-143">이 예제에 사용 된 **Uformat** 서식 지정자는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-143">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="97188-144">지정자</span><span class="sxs-lookup"><span data-stu-id="97188-144">Specifier</span></span> |                      <span data-ttu-id="97188-145">정의</span><span class="sxs-lookup"><span data-stu-id="97188-145">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="97188-146">요일-전체 이름</span><span class="sxs-lookup"><span data-stu-id="97188-146">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="97188-147">월 번호</span><span class="sxs-lookup"><span data-stu-id="97188-147">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="97188-148">월의 날짜-2 자리</span><span class="sxs-lookup"><span data-stu-id="97188-148">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="97188-149">4 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="97188-149">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="97188-150">24 시간 형식의 시간-초 없음</span><span class="sxs-lookup"><span data-stu-id="97188-150">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="97188-151">UTC (Universal Time 좌표의)의 표준 시간대 오프셋</span><span class="sxs-lookup"><span data-stu-id="97188-151">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="97188-152">유효한 **uformat** 형식 지정자 목록은 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97188-152">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="97188-153">예 5: 날짜의 날짜 가져오기</span><span class="sxs-lookup"><span data-stu-id="97188-153">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="97188-154">이 예에서는 속성을 사용 하 여 연간 일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-154">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="97188-155">회교식 달력에는 366 일이 있는 윤년을 제외 하 고 365 일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-155">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="97188-156">예를 들어, 2020 년 12 월 31 일은 366입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-156">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="97188-157">`Get-Date` 는 세 개의 매개 변수를 사용 하 여 **년**, **월**, **일** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-157">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="97188-158">명령은 **DayofYear** 속성을 통해 결과가 계산 되도록 괄호를 사용 하 여 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-158">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="97188-159">예 6: 일광 절약 시간제에 따라 날짜가 조정 되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="97188-159">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="97188-160">이 예제에서는 부울 메서드를 사용 하 여 날짜가 일광 절약 시간제에 따라 조정 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-160">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="97188-161">변수는 `$DST` 의 결과를 저장 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-161">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="97188-162">`$DST`**IsDaylightSavingTime** 메서드를 사용 하 여 일광 절약 시간제에 따라 날짜가 조정 되었는지 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-162">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="97188-163">예 7: 현재 시간을 UTC 시간으로 변환</span><span class="sxs-lookup"><span data-stu-id="97188-163">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="97188-164">이 예제에서 현재 시간은 UTC 시간으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-164">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="97188-165">시스템 로캘의 UTC 오프셋은 시간을 변환 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-165">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="97188-166">[메모](#notes) 섹션의 테이블에는 유효한 **uformat** 형식 지정 자가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-166">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="97188-167">`Get-Date` 형식 지정자와 함께 **Uformat** 매개 변수를 사용 하 여 현재 시스템 날짜 및 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-167">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="97188-168">형식 지정자 **% Z** 은 **(는)-07** 의 UTC 오프셋을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97188-168">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="97188-169">`$Time`변수는 현재 시스템 날짜 및 시간을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-169">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="97188-170">`$Time`**ToUniversalTime ()** 메서드를 사용 하 여 컴퓨터의 UTC 오프셋을 기반으로 시간을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-170">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="97188-171">예 8: 타임 스탬프 만들기</span><span class="sxs-lookup"><span data-stu-id="97188-171">Example 8: Create a timestamp</span></span>

<span data-ttu-id="97188-172">이 예제에서 서식 지정자는 디렉터리 이름에 대 한 타임 스탬프 **문자열** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97188-172">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="97188-173">타임 스탬프에는 날짜, 시간 및 UTC 오프셋이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-173">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="97188-174">`$timestamp`변수는 명령 결과를 저장 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-174">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="97188-175">`Get-Date`**format 매개 변수** 를 소문자의 형식 지정자와 함께 사용 하 여 `o` 타임 스탬프 **문자열** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97188-175">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="97188-176">개체는 파이프라인에서로 전송 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="97188-176">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="97188-177">**ScriptBlock** 에는 `$_` 현재 파이프라인 개체를 나타내는 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-177">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="97188-178">타임 스탬프 문자열은 마침표로 대체 된 콜론으로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-178">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="97188-179">`New-Item`**Path** 매개 변수를 사용 하 여 새 디렉터리의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-179">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="97188-180">경로는 변수를 `$timestamp` 디렉터리 이름으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-180">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="97188-181">**형식** 매개 변수는 디렉터리를 만들도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-181">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="97188-182">예 9: Unix 타임 스탬프 변환</span><span class="sxs-lookup"><span data-stu-id="97188-182">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="97188-183">이 예에서는 Unix 시간 (1970-01-01 0:00:00 이후의 초 수로 나타냄)을 DateTime으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-183">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="97188-184">예 10: UTC로 해석 된 날짜 값 반환</span><span class="sxs-lookup"><span data-stu-id="97188-184">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="97188-185">이 예제에서는 날짜 값을 UTC와 동일 하 게 해석 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="97188-185">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="97188-186">예를 들어이 컴퓨터는 **태평양** 표준시로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-186">For the example, this machine is set to **Pacific Standard Time**.</span></span> <span data-ttu-id="97188-187">기본적으로 `Get-Date` 는 해당 표준 시간대에 대 한 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-187">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="97188-188">**Asutc** 매개 변수를 사용 하 여 값을 해당 하는 UTC 시간으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-188">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

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

## <span data-ttu-id="97188-189">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="97188-189">PARAMETERS</span></span>

### <span data-ttu-id="97188-190">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="97188-190">-AsUTC</span></span>

<span data-ttu-id="97188-191">날짜 값을 해당 하는 UTC 시간으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-191">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="97188-192">이 매개 변수는 PowerShell 7.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-192">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="97188-193">-날짜</span><span class="sxs-lookup"><span data-stu-id="97188-193">-Date</span></span>

<span data-ttu-id="97188-194">날짜 및 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-194">Specifies a date and time.</span></span> <span data-ttu-id="97188-195">Time은 선택 사항이 며 지정 되지 않은 경우 00:00:00을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-195">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="97188-196">시스템 로캘의 표준 형식으로 날짜 및 시간을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-196">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="97188-197">예를 들어 미국 영어:</span><span class="sxs-lookup"><span data-stu-id="97188-197">For example, in US English:</span></span>

<span data-ttu-id="97188-198">`Get-Date -Date "6/25/2019 12:30:22"` 화요일, June 25, 2019 12:30:22 반환</span><span class="sxs-lookup"><span data-stu-id="97188-198">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

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

### <span data-ttu-id="97188-199">-일</span><span class="sxs-lookup"><span data-stu-id="97188-199">-Day</span></span>

<span data-ttu-id="97188-200">표시되는 월의 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-200">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="97188-201">1에서 31 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-201">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="97188-202">지정 된 값이 한 달의 일 수보다 크면 PowerShell에서 해당 월에 일 수를 더 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-202">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="97188-203">예를 들어,는 `Get-Date -Month 2 -Day 31` **2 월 31 일** 이 아닌 **3 월 3** 일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-203">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="97188-204">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="97188-204">-DisplayHint</span></span>

<span data-ttu-id="97188-205">표시되는 날짜 및 시간 요소를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-205">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="97188-206">허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-206">The accepted values are as follows:</span></span>

- <span data-ttu-id="97188-207">**날짜**: 날짜만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-207">**Date**: displays only the date</span></span>
- <span data-ttu-id="97188-208">**Time**: 시간만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-208">**Time**: displays only the time</span></span>
- <span data-ttu-id="97188-209">**DateTime**: 날짜와 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-209">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="97188-210">-형식</span><span class="sxs-lookup"><span data-stu-id="97188-210">-Format</span></span>

<span data-ttu-id="97188-211">형식 지정자가 나타내는 Microsoft .NET Framework 형식의 날짜 및 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-211">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="97188-212">**Format** 매개 변수는 **문자열** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-212">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="97188-213">사용 가능한 .NET 형식 지정자 목록은 [사용자 지정 날짜 및 시간 형식 문자열](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97188-213">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="97188-214">**Format** 매개 변수를 사용 하는 경우 `Get-Date` 날짜를 표시 하는 데 필요한 **DateTime** 개체의 속성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-214">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="97188-215">따라서 **DateTime** 개체의 일부 속성 및 메서드를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-215">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="97188-216">PowerShell 5.0부터 다음 추가 형식을 **Format** 매개 변수에 대 한 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-216">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="97188-217">**Filedate**.</span><span class="sxs-lookup"><span data-stu-id="97188-217">**FileDate**.</span></span> <span data-ttu-id="97188-218">현재 날짜를 현지 시간으로 표현 하는 파일 또는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-218">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="97188-219">형식은 `yyyyMMdd` (4 자리 연도, 2 자리 월 및 2 자리 일을 사용 하는 대/소문자 구분)입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-219">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="97188-220">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="97188-220">For example:</span></span>
  20190627.

- <span data-ttu-id="97188-221">**Filedateuniversal**.</span><span class="sxs-lookup"><span data-stu-id="97188-221">**FileDateUniversal**.</span></span> <span data-ttu-id="97188-222">현재 날짜를 UTC (universal time)로 표현 하는 파일 또는 경로에 대 한 친숙 한 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-222">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="97188-223">형식은입니다 `yyyyMMddZ` . 여기에는 4 자리 연도, 2 자리 월, 2 자리 날짜 및 문자를 UTC 표시기로 사용 하 여 대/소문자를 구분 합니다 `Z` .</span><span class="sxs-lookup"><span data-stu-id="97188-223">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="97188-224">예: 20190627Z</span><span class="sxs-lookup"><span data-stu-id="97188-224">For example: 20190627Z.</span></span>

- <span data-ttu-id="97188-225">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="97188-225">**FileDateTime**.</span></span> <span data-ttu-id="97188-226">현재 날짜와 시간을 24 시간 형식으로 표시 하는 파일 또는 경로에 대 한 친숙 한 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-226">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="97188-227">형식은 `yyyyMMddTHHmmssffff` (대/소문자 구분, 4 자리 연도, 2 자리 월, 2 자리 날짜, `T` 시간 구분 기호, 2 자리 시간, 2 자리 분, 2 자리 초 및 4 자리 밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-227">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="97188-228">예: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="97188-228">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="97188-229">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="97188-229">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="97188-230">현재 날짜와 시간을 24 시간 형식으로 표시 하는 파일 또는 경로 (UTC)를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-230">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="97188-231">형식은 `yyyyMMddTHHmmssffffZ` (대/소문자 구분, 4 자리 연도, 2 자리 월, 2 자리 날짜, `T` 시간 구분 기호, 2 자리 시간, 2 자리 분, 2 자리 초, 4 자리 밀리초 및 `Z` UTC 표시기로 문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-231">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="97188-232">예: 20190627T1540500718Z</span><span class="sxs-lookup"><span data-stu-id="97188-232">For example: 20190627T1540500718Z.</span></span>

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

### <span data-ttu-id="97188-233">-시간</span><span class="sxs-lookup"><span data-stu-id="97188-233">-Hour</span></span>

<span data-ttu-id="97188-234">표시되는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-234">Specifies the hour that is displayed.</span></span> <span data-ttu-id="97188-235">0에서 23 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-235">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="97188-236">-밀리초</span><span class="sxs-lookup"><span data-stu-id="97188-236">-Millisecond</span></span>

<span data-ttu-id="97188-237">날짜에서 밀리초를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-237">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="97188-238">0에서 999 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-238">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="97188-239">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-239">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="97188-240">-분</span><span class="sxs-lookup"><span data-stu-id="97188-240">-Minute</span></span>

<span data-ttu-id="97188-241">표시되는 분을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-241">Specifies the minute that is displayed.</span></span> <span data-ttu-id="97188-242">0에서 59 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-242">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="97188-243">-월</span><span class="sxs-lookup"><span data-stu-id="97188-243">-Month</span></span>

<span data-ttu-id="97188-244">표시되는 월을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-244">Specifies the month that is displayed.</span></span> <span data-ttu-id="97188-245">1에서 12 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-245">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="97188-246">-초</span><span class="sxs-lookup"><span data-stu-id="97188-246">-Second</span></span>

<span data-ttu-id="97188-247">표시되는 초를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-247">Specifies the second that is displayed.</span></span> <span data-ttu-id="97188-248">0에서 59 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-248">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="97188-249">-UFormat</span><span class="sxs-lookup"><span data-stu-id="97188-249">-UFormat</span></span>

<span data-ttu-id="97188-250">날짜 및 시간을 UNIX 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-250">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="97188-251">**Uformat** 매개 변수는 문자열 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-251">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="97188-252">**Uformat** 지정자 앞에는 백분율 기호 ()가 있습니다 ( `%` 예: `%m` , `%d` 및) `%Y` .</span><span class="sxs-lookup"><span data-stu-id="97188-252">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="97188-253">[참고](#notes) 섹션에는 유효한 **uformat 지정자** 의 테이블이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-253">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="97188-254">**Uformat** 매개 변수를 사용 하는 경우 `Get-Date` 날짜를 표시 하는 데 필요한 **DateTime** 개체의 속성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-254">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="97188-255">따라서 **DateTime** 개체의 일부 속성 및 메서드를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-255">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

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

### <span data-ttu-id="97188-256">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="97188-256">-UnixTimeSeconds</span></span>

<span data-ttu-id="97188-257">0:00:00 1970 년 1 월 1 일 이후의 시간 (초)을 나타내는 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-257">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="97188-258">이 매개 변수는 PowerShell 7.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97188-258">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="97188-259">-연도</span><span class="sxs-lookup"><span data-stu-id="97188-259">-Year</span></span>

<span data-ttu-id="97188-260">표시되는 연도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-260">Specifies the year that is displayed.</span></span> <span data-ttu-id="97188-261">1에서 9999 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-261">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="97188-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="97188-262">CommonParameters</span></span>

<span data-ttu-id="97188-263">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="97188-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="97188-264">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97188-264">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="97188-265">입력</span><span class="sxs-lookup"><span data-stu-id="97188-265">INPUTS</span></span>

### <span data-ttu-id="97188-266">파이프라인 입력</span><span class="sxs-lookup"><span data-stu-id="97188-266">Pipeline input</span></span>

<span data-ttu-id="97188-267">`Get-Date` 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-267">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="97188-268">예: `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="97188-268">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="97188-269">출력</span><span class="sxs-lookup"><span data-stu-id="97188-269">OUTPUTS</span></span>

### <span data-ttu-id="97188-270">System.string 또는 System.string</span><span class="sxs-lookup"><span data-stu-id="97188-270">System.DateTime or System.String</span></span>

<span data-ttu-id="97188-271">`Get-Date`**format** 및 **uformat** 매개 변수를 사용 하는 경우를 제외 하 고는 **DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-271">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="97188-272">**Format** 또는 **uformat** 매개 변수는 **문자열** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-272">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="97188-273">**DateTime** 개체가 문자열 입력을 필요로 하는 것과 같은 cmdlet으로 파이프라인으로 전송 되는 경우 `Add-Content` PowerShell은 개체를 **문자열** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-273">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="97188-274">메서드는 `(Get-Date).ToString()` **DateTime** 개체를 **문자열** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97188-274">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="97188-275">개체의 속성 및 메서드를 표시 하려면 개체를 파이프라인에서로 보냅니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="97188-275">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="97188-276">예: `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="97188-276">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="97188-277">참고</span><span class="sxs-lookup"><span data-stu-id="97188-277">NOTES</span></span>

<span data-ttu-id="97188-278">**DateTime** 개체는 시스템 로캘의 자세한 날짜 및 자세한 시간 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="97188-278">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="97188-279">유효한 **Uformat 지정 자가** 다음 표에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97188-279">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="97188-280">형식 지정자</span><span class="sxs-lookup"><span data-stu-id="97188-280">Format specifier</span></span> |                                 <span data-ttu-id="97188-281">의미</span><span class="sxs-lookup"><span data-stu-id="97188-281">Meaning</span></span>                     |         <span data-ttu-id="97188-282">예제</span><span class="sxs-lookup"><span data-stu-id="97188-282">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="97188-283">요일-전체 이름</span><span class="sxs-lookup"><span data-stu-id="97188-283">Day of the week - full name</span></span>                                             | <span data-ttu-id="97188-284">월요일</span><span class="sxs-lookup"><span data-stu-id="97188-284">Monday</span></span>                   |
| `%a` | <span data-ttu-id="97188-285">요일-약식 이름</span><span class="sxs-lookup"><span data-stu-id="97188-285">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="97188-286">Mon</span><span class="sxs-lookup"><span data-stu-id="97188-286">Mon</span></span>                      |
| `%B` | <span data-ttu-id="97188-287">월 이름-전체</span><span class="sxs-lookup"><span data-stu-id="97188-287">Month name - full</span></span>                                                       | <span data-ttu-id="97188-288">January</span><span class="sxs-lookup"><span data-stu-id="97188-288">January</span></span>                  |
| `%b` | <span data-ttu-id="97188-289">월 이름-약식</span><span class="sxs-lookup"><span data-stu-id="97188-289">Month name - abbreviated</span></span>                                                | <span data-ttu-id="97188-290">1월</span><span class="sxs-lookup"><span data-stu-id="97188-290">Jan</span></span>                      |
| `%C` | <span data-ttu-id="97188-291">궁서</span><span class="sxs-lookup"><span data-stu-id="97188-291">Century</span></span>                                                                 | <span data-ttu-id="97188-292">2019의 경우 20</span><span class="sxs-lookup"><span data-stu-id="97188-292">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="97188-293">날짜 및 시간-약식</span><span class="sxs-lookup"><span data-stu-id="97188-293">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="97188-294">6 월 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="97188-294">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="97188-295">Mm/dd/yy 형식의 날짜</span><span class="sxs-lookup"><span data-stu-id="97188-295">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="97188-296">06/27/19</span><span class="sxs-lookup"><span data-stu-id="97188-296">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="97188-297">월의 날짜-2 자리</span><span class="sxs-lookup"><span data-stu-id="97188-297">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="97188-298">05</span><span class="sxs-lookup"><span data-stu-id="97188-298">05</span></span>                       |
| `%e` | <span data-ttu-id="97188-299">월의 날짜-한 자리로 된 경우 공백을 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97188-299">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="97188-300">\<space\>5</span><span class="sxs-lookup"><span data-stu-id="97188-300">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="97188-301">YYYY-mm-dd 형식의 날짜 (% Y-% m-% d) (ISO 8601 날짜 형식)</span><span class="sxs-lookup"><span data-stu-id="97188-301">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="97188-302">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="97188-302">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="97188-303">' Y '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-303">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="97188-304">' Y '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-304">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="97188-305">24 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="97188-305">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="97188-306">17</span><span class="sxs-lookup"><span data-stu-id="97188-306">17</span></span>                       |
| `%h` | <span data-ttu-id="97188-307">' B '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-307">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="97188-308">12 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="97188-308">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="97188-309">05</span><span class="sxs-lookup"><span data-stu-id="97188-309">05</span></span>                       |
| `%j` | <span data-ttu-id="97188-310">연간 일자</span><span class="sxs-lookup"><span data-stu-id="97188-310">Day of the year</span></span>                                                         | <span data-ttu-id="97188-311">1-366</span><span class="sxs-lookup"><span data-stu-id="97188-311">1-366</span></span>                    |
| `%k` | <span data-ttu-id="97188-312">' H '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-312">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="97188-313">' I '와 동일 (대문자 I)</span><span class="sxs-lookup"><span data-stu-id="97188-313">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="97188-314">05</span><span class="sxs-lookup"><span data-stu-id="97188-314">05</span></span>                       |
| `%M` | <span data-ttu-id="97188-315">분</span><span class="sxs-lookup"><span data-stu-id="97188-315">Minutes</span></span>                                                                 | <span data-ttu-id="97188-316">35</span><span class="sxs-lookup"><span data-stu-id="97188-316">35</span></span>                       |
| `%m` | <span data-ttu-id="97188-317">월 번호</span><span class="sxs-lookup"><span data-stu-id="97188-317">Month number</span></span>                                                            | <span data-ttu-id="97188-318">06</span><span class="sxs-lookup"><span data-stu-id="97188-318">06</span></span>                       |
| `%n` | <span data-ttu-id="97188-319">줄 바꿈 문자</span><span class="sxs-lookup"><span data-stu-id="97188-319">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="97188-320">AM 또는 PM</span><span class="sxs-lookup"><span data-stu-id="97188-320">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="97188-321">24 시간 형식의 시간-초 없음</span><span class="sxs-lookup"><span data-stu-id="97188-321">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="97188-322">17:45</span><span class="sxs-lookup"><span data-stu-id="97188-322">17:45</span></span>                    |
| `%r` | <span data-ttu-id="97188-323">12 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="97188-323">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="97188-324">오전 09:15:36</span><span class="sxs-lookup"><span data-stu-id="97188-324">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="97188-325">초</span><span class="sxs-lookup"><span data-stu-id="97188-325">Seconds</span></span>                                                                 | <span data-ttu-id="97188-326">05</span><span class="sxs-lookup"><span data-stu-id="97188-326">05</span></span>                       |
| `%s` | <span data-ttu-id="97188-327">1970 00:00:00 1 월 1 일 이후 경과 된 시간 (초)</span><span class="sxs-lookup"><span data-stu-id="97188-327">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="97188-328">1150451174</span><span class="sxs-lookup"><span data-stu-id="97188-328">1150451174</span></span>               |
| `%t` | <span data-ttu-id="97188-329">가로 탭 문자</span><span class="sxs-lookup"><span data-stu-id="97188-329">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="97188-330">24 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="97188-330">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="97188-331">17:45:52</span><span class="sxs-lookup"><span data-stu-id="97188-331">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="97188-332">' W '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-332">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="97188-333">요일-번호</span><span class="sxs-lookup"><span data-stu-id="97188-333">Day of the week - number</span></span>                                                | <span data-ttu-id="97188-334">일요일 = 0</span><span class="sxs-lookup"><span data-stu-id="97188-334">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="97188-335">연간 주</span><span class="sxs-lookup"><span data-stu-id="97188-335">Week of the year</span></span>                                                        | <span data-ttu-id="97188-336">01-53</span><span class="sxs-lookup"><span data-stu-id="97188-336">01-53</span></span>                    |
| `%w` | <span data-ttu-id="97188-337">' U '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-337">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="97188-338">연간 주</span><span class="sxs-lookup"><span data-stu-id="97188-338">Week of the year</span></span>                                                        | <span data-ttu-id="97188-339">00-52</span><span class="sxs-lookup"><span data-stu-id="97188-339">00-52</span></span>                    |
| `%X` | <span data-ttu-id="97188-340">' T '와 동일</span><span class="sxs-lookup"><span data-stu-id="97188-340">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="97188-341">로캘의 표준 형식 날짜</span><span class="sxs-lookup"><span data-stu-id="97188-341">Date in standard format for locale</span></span>                                      | <span data-ttu-id="97188-342">영어 (미국)의 경우 06/27/19</span><span class="sxs-lookup"><span data-stu-id="97188-342">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="97188-343">4 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="97188-343">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="97188-344">2019</span><span class="sxs-lookup"><span data-stu-id="97188-344">2019</span></span>                     |
| `%y` | <span data-ttu-id="97188-345">2 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="97188-345">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="97188-346">19</span><span class="sxs-lookup"><span data-stu-id="97188-346">19</span></span>                       |
| `%Z` | <span data-ttu-id="97188-347">UTC (Universal Time 좌표의)의 표준 시간대 오프셋</span><span class="sxs-lookup"><span data-stu-id="97188-347">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="97188-348">-07</span><span class="sxs-lookup"><span data-stu-id="97188-348">-07</span></span>                      |

## <span data-ttu-id="97188-349">관련 링크</span><span class="sxs-lookup"><span data-stu-id="97188-349">RELATED LINKS</span></span>

[<span data-ttu-id="97188-350">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="97188-350">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="97188-351">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="97188-351">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="97188-352">Get-Member</span><span class="sxs-lookup"><span data-stu-id="97188-352">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="97188-353">New-Item</span><span class="sxs-lookup"><span data-stu-id="97188-353">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="97188-354">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="97188-354">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="97188-355">Set-Date</span><span class="sxs-lookup"><span data-stu-id="97188-355">Set-Date</span></span>](Set-Date.md)
