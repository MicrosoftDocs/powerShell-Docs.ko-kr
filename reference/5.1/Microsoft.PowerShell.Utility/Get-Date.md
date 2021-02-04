---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: bb7f169e0c01c73bb4e834375f341bf795e37ce7
ms.sourcegitcommit: f5986121386c81acddcf324eb0526d7d092bcc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584667"
---
# <span data-ttu-id="5eff2-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="5eff2-103">Get-Date</span></span>

## <span data-ttu-id="5eff2-104">개요</span><span class="sxs-lookup"><span data-stu-id="5eff2-104">SYNOPSIS</span></span>
<span data-ttu-id="5eff2-105">현재 날짜 및 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-105">Gets the current date and time.</span></span>

## <span data-ttu-id="5eff2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5eff2-106">SYNTAX</span></span>

### <span data-ttu-id="5eff2-107">net (기본값)</span><span class="sxs-lookup"><span data-stu-id="5eff2-107">net (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [<CommonParameters>]
```

### <span data-ttu-id="5eff2-108">UFormat</span><span class="sxs-lookup"><span data-stu-id="5eff2-108">UFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-UFormat <String>] [<CommonParameters>]
```

## <span data-ttu-id="5eff2-109">설명</span><span class="sxs-lookup"><span data-stu-id="5eff2-109">DESCRIPTION</span></span>

<span data-ttu-id="5eff2-110">`Get-Date`Cmdlet은 현재 날짜 또는 지정한 날짜를 나타내는 **DateTime** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-110">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="5eff2-111">`Get-Date` 에서는 날짜 및 시간을 여러 .NET 및 UNIX 형식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-111">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="5eff2-112">`Get-Date`를 사용 하 여 날짜 또는 시간 문자열을 생성 한 다음 다른 cmdlet 또는 프로그램으로 문자열을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-112">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="5eff2-113">`Get-Date` 컴퓨터의 문화권 설정을 사용 하 여 출력의 형식 지정 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-113">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="5eff2-114">컴퓨터의 설정을 보려면를 사용 `(Get-Culture).DateTimeFormat` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-114">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="5eff2-115">예제</span><span class="sxs-lookup"><span data-stu-id="5eff2-115">EXAMPLES</span></span>

### <span data-ttu-id="5eff2-116">예 1: 현재 날짜 및 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="5eff2-116">Example 1: Get the current date and time</span></span>

<span data-ttu-id="5eff2-117">이 예에서는 `Get-Date` 현재 시스템 날짜 및 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-117">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="5eff2-118">출력은 자세한 날짜 및 자세한 시간 형식으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-118">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="5eff2-119">예제 2: 현재 날짜 및 시간의 요소 가져오기</span><span class="sxs-lookup"><span data-stu-id="5eff2-119">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="5eff2-120">이 예제에서는를 사용 하 여 `Get-Date` 날짜 또는 시간 요소를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-120">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="5eff2-121">매개 변수는 **Date**, **Time** 또는 **DateTime** 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-121">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="5eff2-122">`Get-Date`**date 인수와 함께** **displayhint** 매개 변수를 사용 하 여 날짜만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-122">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="5eff2-123">예제 3: .NET 서식 지정자를 사용 하 여 날짜 및 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="5eff2-123">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="5eff2-124">이 예제에서는 .NET 형식 지정자를 사용 하 여 출력 형식을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-124">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="5eff2-125">출력은 **문자열** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-125">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="5eff2-126">`Get-Date`**format** 매개 변수를 사용 하 여 여러 형식 지정자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-126">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="5eff2-127">이 예제에서 사용 되는 .NET 형식 지정자는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-127">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="5eff2-128">지정자</span><span class="sxs-lookup"><span data-stu-id="5eff2-128">Specifier</span></span> | <span data-ttu-id="5eff2-129">정의</span><span class="sxs-lookup"><span data-stu-id="5eff2-129">Definition</span></span> |
| --- | --- |
| `dddd` | <span data-ttu-id="5eff2-130">요일-전체 이름</span><span class="sxs-lookup"><span data-stu-id="5eff2-130">Day of the week - full name</span></span> |
| `MM` | <span data-ttu-id="5eff2-131">월 번호</span><span class="sxs-lookup"><span data-stu-id="5eff2-131">Month number</span></span> |
| `dd` | <span data-ttu-id="5eff2-132">월의 날짜-2 자리</span><span class="sxs-lookup"><span data-stu-id="5eff2-132">Day of the month - 2 digits</span></span> |
| `yyyy` | <span data-ttu-id="5eff2-133">4 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="5eff2-133">Year in 4-digit format</span></span> |
| `HH:mm` | <span data-ttu-id="5eff2-134">24 시간 형식의 시간-초 없음</span><span class="sxs-lookup"><span data-stu-id="5eff2-134">Time in 24-hour format -no seconds</span></span> |
| `K` | <span data-ttu-id="5eff2-135">UTC (Universal Time 좌표의)의 표준 시간대 오프셋</span><span class="sxs-lookup"><span data-stu-id="5eff2-135">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="5eff2-136">.NET 형식 지정자에 대 한 자세한 내용은 [사용자 지정 날짜 및 시간 형식 문자열](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5eff2-136">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="5eff2-137">예제 4: UFormat 지정자를 사용 하 여 날짜 및 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="5eff2-137">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="5eff2-138">이 예제에서는 출력 형식을 사용자 지정 하는 데 몇 가지 **uformat** 형식 지정자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-138">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="5eff2-139">출력은 **문자열** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-139">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="5eff2-140">`Get-Date`**uformat** 매개 변수를 사용 하 여 여러 형식 지정자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-140">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="5eff2-141">이 예제에 사용 된 **Uformat** 서식 지정자는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-141">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="5eff2-142">지정자</span><span class="sxs-lookup"><span data-stu-id="5eff2-142">Specifier</span></span> | <span data-ttu-id="5eff2-143">정의</span><span class="sxs-lookup"><span data-stu-id="5eff2-143">Definition</span></span> |
| --- | --- |
| `%A` | <span data-ttu-id="5eff2-144">요일-전체 이름</span><span class="sxs-lookup"><span data-stu-id="5eff2-144">Day of the week - full name</span></span> |
| `%m` | <span data-ttu-id="5eff2-145">월 번호</span><span class="sxs-lookup"><span data-stu-id="5eff2-145">Month number</span></span> |
| `%d` | <span data-ttu-id="5eff2-146">월의 날짜-2 자리</span><span class="sxs-lookup"><span data-stu-id="5eff2-146">Day of the month - 2 digits</span></span> |
| `%Y` | <span data-ttu-id="5eff2-147">4 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="5eff2-147">Year in 4-digit format</span></span> |
| `%R` | <span data-ttu-id="5eff2-148">24 시간 형식의 시간-초 없음</span><span class="sxs-lookup"><span data-stu-id="5eff2-148">Time in 24-hour format -no seconds</span></span> |
| `%Z` | <span data-ttu-id="5eff2-149">UTC (Universal Time 좌표의)의 표준 시간대 오프셋</span><span class="sxs-lookup"><span data-stu-id="5eff2-149">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="5eff2-150">유효한 **uformat** 형식 지정자 목록은 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5eff2-150">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="5eff2-151">예 5: 날짜의 날짜 가져오기</span><span class="sxs-lookup"><span data-stu-id="5eff2-151">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="5eff2-152">이 예에서는 속성을 사용 하 여 연간 일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-152">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="5eff2-153">회교식 달력에는 366 일이 있는 윤년을 제외 하 고 365 일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-153">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="5eff2-154">예를 들어, 2020 년 12 월 31 일은 366입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-154">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="5eff2-155">`Get-Date` 는 세 개의 매개 변수를 사용 하 여 **년**, **월**, **일** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-155">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="5eff2-156">명령은 **DayofYear** 속성을 통해 결과가 계산 되도록 괄호를 사용 하 여 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-156">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="5eff2-157">예 6: 일광 절약 시간제에 따라 날짜가 조정 되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="5eff2-157">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="5eff2-158">이 예제에서는 부울 메서드를 사용 하 여 날짜가 일광 절약 시간제에 따라 조정 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-158">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="5eff2-159">변수는 `$DST` 의 결과를 저장 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-159">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="5eff2-160">`$DST`**IsDaylightSavingTime** 메서드를 사용 하 여 일광 절약 시간제에 따라 날짜가 조정 되었는지 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-160">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="5eff2-161">예 7: 현재 시간을 UTC 시간으로 변환</span><span class="sxs-lookup"><span data-stu-id="5eff2-161">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="5eff2-162">이 예제에서 현재 시간은 UTC 시간으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-162">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="5eff2-163">시스템 로캘의 UTC 오프셋은 시간을 변환 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-163">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="5eff2-164">[메모](#notes) 섹션의 테이블에는 유효한 **uformat** 형식 지정 자가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-164">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="5eff2-165">`Get-Date` 형식 지정자와 함께 **Uformat** 매개 변수를 사용 하 여 현재 시스템 날짜 및 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-165">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="5eff2-166">형식 지정자 **% Z** 은 **(는)-07** 의 UTC 오프셋을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-166">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="5eff2-167">`$Time`변수는 현재 시스템 날짜 및 시간을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-167">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="5eff2-168">`$Time`**ToUniversalTime ()** 메서드를 사용 하 여 컴퓨터의 UTC 오프셋을 기반으로 시간을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-168">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="5eff2-169">예 8: 타임 스탬프 만들기</span><span class="sxs-lookup"><span data-stu-id="5eff2-169">Example 8: Create a timestamp</span></span>

<span data-ttu-id="5eff2-170">이 예제에서 서식 지정자는 디렉터리 이름에 대 한 타임 스탬프 **문자열** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-170">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="5eff2-171">타임 스탬프에는 날짜, 시간 및 UTC 오프셋이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-171">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="5eff2-172">`$timestamp`변수는 명령 결과를 저장 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-172">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="5eff2-173">`Get-Date`**format 매개 변수** 를 소문자의 형식 지정자와 함께 사용 하 여 `o` 타임 스탬프 **문자열** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-173">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="5eff2-174">개체는 파이프라인에서로 전송 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="5eff2-174">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="5eff2-175">**ScriptBlock** 에는 `$_` 현재 파이프라인 개체를 나타내는 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-175">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="5eff2-176">타임 스탬프 문자열은 마침표로 대체 된 콜론으로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-176">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="5eff2-177">`New-Item`**Path** 매개 변수를 사용 하 여 새 디렉터리의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-177">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="5eff2-178">경로는 변수를 `$timestamp` 디렉터리 이름으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-178">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="5eff2-179">**형식** 매개 변수는 디렉터리를 만들도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-179">The **Type** parameter specifies that a directory is created.</span></span>

## <span data-ttu-id="5eff2-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5eff2-180">PARAMETERS</span></span>

### <span data-ttu-id="5eff2-181">-날짜</span><span class="sxs-lookup"><span data-stu-id="5eff2-181">-Date</span></span>

<span data-ttu-id="5eff2-182">날짜 및 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-182">Specifies a date and time.</span></span> <span data-ttu-id="5eff2-183">Time은 선택 사항이 며 지정 되지 않은 경우 00:00:00을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-183">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="5eff2-184">시스템 로캘의 표준 형식으로 날짜 및 시간을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-184">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="5eff2-185">예를 들어 미국 영어:</span><span class="sxs-lookup"><span data-stu-id="5eff2-185">For example, in US English:</span></span>

<span data-ttu-id="5eff2-186">`Get-Date -Date "6/25/2019 12:30:22"` 화요일, June 25, 2019 12:30:22 반환</span><span class="sxs-lookup"><span data-stu-id="5eff2-186">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5eff2-187">-일</span><span class="sxs-lookup"><span data-stu-id="5eff2-187">-Day</span></span>

<span data-ttu-id="5eff2-188">표시되는 월의 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-188">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="5eff2-189">1에서 31 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-189">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="5eff2-190">지정 된 값이 한 달의 일 수보다 크면 PowerShell에서 해당 월에 일 수를 더 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-190">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="5eff2-191">예를 들어,는 `Get-Date -Month 2 -Day 31` **2 월 31 일** 이 아닌 **3 월 3** 일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-191">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="5eff2-192">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="5eff2-192">-DisplayHint</span></span>

<span data-ttu-id="5eff2-193">표시되는 날짜 및 시간 요소를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-193">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="5eff2-194">허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-194">The accepted values are as follows:</span></span>

- <span data-ttu-id="5eff2-195">**날짜**: 날짜만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-195">**Date**: displays only the date</span></span>
- <span data-ttu-id="5eff2-196">**Time**: 시간만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-196">**Time**: displays only the time</span></span>
- <span data-ttu-id="5eff2-197">**DateTime**: 날짜와 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-197">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="5eff2-198">-형식</span><span class="sxs-lookup"><span data-stu-id="5eff2-198">-Format</span></span>

<span data-ttu-id="5eff2-199">형식 지정자가 나타내는 Microsoft .NET Framework 형식의 날짜 및 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-199">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="5eff2-200">**Format** 매개 변수는 **문자열** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-200">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="5eff2-201">사용 가능한 .NET 형식 지정자 목록은 [사용자 지정 날짜 및 시간 형식 문자열](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5eff2-201">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="5eff2-202">**Format** 매개 변수를 사용 하는 경우 `Get-Date` 날짜를 표시 하는 데 필요한 **DateTime** 개체의 속성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-202">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="5eff2-203">따라서 **DateTime** 개체의 일부 속성 및 메서드를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-203">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="5eff2-204">PowerShell 5.0부터 다음 추가 형식을 **Format** 매개 변수에 대 한 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-204">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="5eff2-205">**Filedate**.</span><span class="sxs-lookup"><span data-stu-id="5eff2-205">**FileDate**.</span></span> <span data-ttu-id="5eff2-206">현재 날짜를 현지 시간으로 표현 하는 파일 또는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-206">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="5eff2-207">형식은 `yyyyMMdd` (4 자리 연도, 2 자리 월 및 2 자리 일을 사용 하는 대/소문자 구분)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-207">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="5eff2-208">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-208">For example:</span></span>
  20190627.

- <span data-ttu-id="5eff2-209">**Filedateuniversal**.</span><span class="sxs-lookup"><span data-stu-id="5eff2-209">**FileDateUniversal**.</span></span> <span data-ttu-id="5eff2-210">현재 날짜를 UTC (universal time)로 표현 하는 파일 또는 경로에 대 한 친숙 한 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-210">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="5eff2-211">형식은입니다 `yyyyMMddZ` . 여기에는 4 자리 연도, 2 자리 월, 2 자리 날짜 및 문자를 UTC 표시기로 사용 하 여 대/소문자를 구분 합니다 `Z` .</span><span class="sxs-lookup"><span data-stu-id="5eff2-211">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="5eff2-212">예: 20190627Z</span><span class="sxs-lookup"><span data-stu-id="5eff2-212">For example: 20190627Z.</span></span>

- <span data-ttu-id="5eff2-213">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="5eff2-213">**FileDateTime**.</span></span> <span data-ttu-id="5eff2-214">현재 날짜와 시간을 24 시간 형식으로 표시 하는 파일 또는 경로에 대 한 친숙 한 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-214">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="5eff2-215">형식은 `yyyyMMddTHHmmssffff` (대/소문자 구분, 4 자리 연도, 2 자리 월, 2 자리 날짜, `T` 시간 구분 기호, 2 자리 시간, 2 자리 분, 2 자리 초 및 4 자리 밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-215">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="5eff2-216">예: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="5eff2-216">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="5eff2-217">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="5eff2-217">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="5eff2-218">현재 날짜와 시간을 24 시간 형식으로 표시 하는 파일 또는 경로 (UTC)를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-218">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="5eff2-219">형식은 `yyyyMMddTHHmmssffffZ` (대/소문자 구분, 4 자리 연도, 2 자리 월, 2 자리 날짜, `T` 시간 구분 기호, 2 자리 시간, 2 자리 분, 2 자리 초, 4 자리 밀리초 및 `Z` UTC 표시기로 문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-219">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="5eff2-220">예: 20190627T1540500718Z</span><span class="sxs-lookup"><span data-stu-id="5eff2-220">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: net
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5eff2-221">-시간</span><span class="sxs-lookup"><span data-stu-id="5eff2-221">-Hour</span></span>

<span data-ttu-id="5eff2-222">표시되는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-222">Specifies the hour that is displayed.</span></span> <span data-ttu-id="5eff2-223">0에서 23 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-223">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="5eff2-224">-밀리초</span><span class="sxs-lookup"><span data-stu-id="5eff2-224">-Millisecond</span></span>

<span data-ttu-id="5eff2-225">날짜에서 밀리초를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-225">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="5eff2-226">0에서 999 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-226">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="5eff2-227">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5eff2-228">-분</span><span class="sxs-lookup"><span data-stu-id="5eff2-228">-Minute</span></span>

<span data-ttu-id="5eff2-229">표시되는 분을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-229">Specifies the minute that is displayed.</span></span> <span data-ttu-id="5eff2-230">0에서 59 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-230">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="5eff2-231">-월</span><span class="sxs-lookup"><span data-stu-id="5eff2-231">-Month</span></span>

<span data-ttu-id="5eff2-232">표시되는 월을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-232">Specifies the month that is displayed.</span></span> <span data-ttu-id="5eff2-233">1에서 12 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-233">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="5eff2-234">-초</span><span class="sxs-lookup"><span data-stu-id="5eff2-234">-Second</span></span>

<span data-ttu-id="5eff2-235">표시되는 초를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-235">Specifies the second that is displayed.</span></span> <span data-ttu-id="5eff2-236">0에서 59 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-236">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="5eff2-237">-UFormat</span><span class="sxs-lookup"><span data-stu-id="5eff2-237">-UFormat</span></span>

<span data-ttu-id="5eff2-238">날짜 및 시간을 UNIX 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-238">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="5eff2-239">**Uformat** 매개 변수는 문자열 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-239">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="5eff2-240">**Uformat** 지정자 앞에는 백분율 기호 ()가 있습니다 ( `%` 예: `%m` , `%d` 및) `%Y` .</span><span class="sxs-lookup"><span data-stu-id="5eff2-240">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="5eff2-241">[참고](#notes) 섹션에는 유효한 **uformat 지정자** 의 테이블이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-241">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="5eff2-242">**Uformat** 매개 변수를 사용 하는 경우 `Get-Date` 날짜를 표시 하는 데 필요한 **DateTime** 개체의 속성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-242">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="5eff2-243">따라서 **DateTime** 개체의 일부 속성 및 메서드를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-243">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: UFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5eff2-244">-연도</span><span class="sxs-lookup"><span data-stu-id="5eff2-244">-Year</span></span>

<span data-ttu-id="5eff2-245">표시되는 연도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-245">Specifies the year that is displayed.</span></span> <span data-ttu-id="5eff2-246">1에서 9999 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-246">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="5eff2-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5eff2-247">CommonParameters</span></span>

<span data-ttu-id="5eff2-248">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5eff2-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5eff2-249">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5eff2-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5eff2-250">입력</span><span class="sxs-lookup"><span data-stu-id="5eff2-250">INPUTS</span></span>

### <span data-ttu-id="5eff2-251">파이프라인 입력</span><span class="sxs-lookup"><span data-stu-id="5eff2-251">Pipeline input</span></span>

<span data-ttu-id="5eff2-252">`Get-Date` 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-252">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="5eff2-253">예: `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="5eff2-253">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="5eff2-254">출력</span><span class="sxs-lookup"><span data-stu-id="5eff2-254">OUTPUTS</span></span>

### <span data-ttu-id="5eff2-255">System.string 또는 System.string</span><span class="sxs-lookup"><span data-stu-id="5eff2-255">System.DateTime or System.String</span></span>

<span data-ttu-id="5eff2-256">`Get-Date`**format** 및 **uformat** 매개 변수를 사용 하는 경우를 제외 하 고는 **DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-256">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="5eff2-257">**Format** 또는 **uformat** 매개 변수는 **문자열** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-257">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="5eff2-258">**DateTime** 개체가 문자열 입력을 필요로 하는 것과 같은 cmdlet으로 파이프라인으로 전송 되는 경우 `Add-Content` PowerShell은 개체를 **문자열** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-258">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="5eff2-259">메서드는 `(Get-Date).ToString()` **DateTime** 개체를 **문자열** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-259">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="5eff2-260">개체의 속성 및 메서드를 표시 하려면 개체를 파이프라인에서로 보냅니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="5eff2-260">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="5eff2-261">예: `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="5eff2-261">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="5eff2-262">참고</span><span class="sxs-lookup"><span data-stu-id="5eff2-262">NOTES</span></span>

<span data-ttu-id="5eff2-263">**DateTime** 개체는 시스템 로캘의 자세한 날짜 및 자세한 시간 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-263">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="5eff2-264">유효한 **Uformat 지정 자가** 다음 표에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-264">The valid **UFormat specifiers** are displayed in the following table:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5eff2-265">새 버전의 PowerShell에 추가 **Uformat 지정** 자가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-265">Additional **UFormat** specifiers are added in newer versions of PowerShell.</span></span> <span data-ttu-id="5eff2-266">예를 들어 `%F` 은 powershell 6.2에 추가 되었으므로 Windows powershell 5.1 또는 이전 버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-266">For example, `%F` was added in PowerShell 6.2, so it isn't available in Windows PowerShell 5.1 or older.</span></span> <span data-ttu-id="5eff2-267">여러 버전의 PowerShell에서 실행 되도록 설계 된 스크립트에서 **Uformat** 지정자를 사용 하는 경우이 점을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-267">Keep this in mind when using **UFormat** specifiers in scripts designed to be run on multiple versions of PowerShell.</span></span>

| <span data-ttu-id="5eff2-268">형식 지정자</span><span class="sxs-lookup"><span data-stu-id="5eff2-268">Format specifier</span></span> |                                 <span data-ttu-id="5eff2-269">의미</span><span class="sxs-lookup"><span data-stu-id="5eff2-269">Meaning</span></span>                     |         <span data-ttu-id="5eff2-270">예제</span><span class="sxs-lookup"><span data-stu-id="5eff2-270">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="5eff2-271">요일-전체 이름</span><span class="sxs-lookup"><span data-stu-id="5eff2-271">Day of the week - full name</span></span>                                             | <span data-ttu-id="5eff2-272">월요일</span><span class="sxs-lookup"><span data-stu-id="5eff2-272">Monday</span></span>                   |
| `%a` | <span data-ttu-id="5eff2-273">요일-약식 이름</span><span class="sxs-lookup"><span data-stu-id="5eff2-273">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="5eff2-274">Mon</span><span class="sxs-lookup"><span data-stu-id="5eff2-274">Mon</span></span>                      |
| `%B` | <span data-ttu-id="5eff2-275">월 이름-전체</span><span class="sxs-lookup"><span data-stu-id="5eff2-275">Month name - full</span></span>                                                       | <span data-ttu-id="5eff2-276">January</span><span class="sxs-lookup"><span data-stu-id="5eff2-276">January</span></span>                  |
| `%b` | <span data-ttu-id="5eff2-277">월 이름-약식</span><span class="sxs-lookup"><span data-stu-id="5eff2-277">Month name - abbreviated</span></span>                                                | <span data-ttu-id="5eff2-278">1월</span><span class="sxs-lookup"><span data-stu-id="5eff2-278">Jan</span></span>                      |
| `%C` | <span data-ttu-id="5eff2-279">궁서</span><span class="sxs-lookup"><span data-stu-id="5eff2-279">Century</span></span>                                                                 | <span data-ttu-id="5eff2-280">2019의 경우 20</span><span class="sxs-lookup"><span data-stu-id="5eff2-280">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="5eff2-281">날짜 및 시간-약식</span><span class="sxs-lookup"><span data-stu-id="5eff2-281">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="5eff2-282">6 월 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="5eff2-282">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="5eff2-283">Mm/dd/yy 형식의 날짜</span><span class="sxs-lookup"><span data-stu-id="5eff2-283">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="5eff2-284">06/27/19</span><span class="sxs-lookup"><span data-stu-id="5eff2-284">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="5eff2-285">월의 날짜-2 자리</span><span class="sxs-lookup"><span data-stu-id="5eff2-285">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="5eff2-286">05</span><span class="sxs-lookup"><span data-stu-id="5eff2-286">05</span></span>                       |
| `%e` | <span data-ttu-id="5eff2-287">월의 날짜-한 자리로 된 경우 공백을 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="5eff2-287">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="5eff2-288">\<space\>5</span><span class="sxs-lookup"><span data-stu-id="5eff2-288">\<space\>5</span></span>               |
| `%G` | <span data-ttu-id="5eff2-289">' Y '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-289">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="5eff2-290">' Y '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-290">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="5eff2-291">24 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="5eff2-291">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="5eff2-292">17</span><span class="sxs-lookup"><span data-stu-id="5eff2-292">17</span></span>                       |
| `%h` | <span data-ttu-id="5eff2-293">' B '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-293">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="5eff2-294">12 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="5eff2-294">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="5eff2-295">05</span><span class="sxs-lookup"><span data-stu-id="5eff2-295">05</span></span>                       |
| `%j` | <span data-ttu-id="5eff2-296">연간 일자 ( `0` PowerShell 6 이상에서 선행 수정이 포함 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="5eff2-296">Day of the year (does not include leading `0` - Fixed in PowerShell 6+)</span></span> | <span data-ttu-id="5eff2-297">1-366</span><span class="sxs-lookup"><span data-stu-id="5eff2-297">1-366</span></span>                    |
| `%k` | <span data-ttu-id="5eff2-298">' H '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-298">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="5eff2-299">' I '와 동일 (대문자 I)</span><span class="sxs-lookup"><span data-stu-id="5eff2-299">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="5eff2-300">05</span><span class="sxs-lookup"><span data-stu-id="5eff2-300">05</span></span>                       |
| `%M` | <span data-ttu-id="5eff2-301">분</span><span class="sxs-lookup"><span data-stu-id="5eff2-301">Minutes</span></span>                                                                 | <span data-ttu-id="5eff2-302">35</span><span class="sxs-lookup"><span data-stu-id="5eff2-302">35</span></span>                       |
| `%m` | <span data-ttu-id="5eff2-303">월 번호</span><span class="sxs-lookup"><span data-stu-id="5eff2-303">Month number</span></span>                                                            | <span data-ttu-id="5eff2-304">06</span><span class="sxs-lookup"><span data-stu-id="5eff2-304">06</span></span>                       |
| `%n` | <span data-ttu-id="5eff2-305">줄 바꿈 문자</span><span class="sxs-lookup"><span data-stu-id="5eff2-305">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="5eff2-306">AM 또는 PM</span><span class="sxs-lookup"><span data-stu-id="5eff2-306">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="5eff2-307">24 시간 형식의 시간-초 없음</span><span class="sxs-lookup"><span data-stu-id="5eff2-307">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="5eff2-308">17:45</span><span class="sxs-lookup"><span data-stu-id="5eff2-308">17:45</span></span>                    |
| `%r` | <span data-ttu-id="5eff2-309">12 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="5eff2-309">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="5eff2-310">오전 09:15:36</span><span class="sxs-lookup"><span data-stu-id="5eff2-310">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="5eff2-311">초</span><span class="sxs-lookup"><span data-stu-id="5eff2-311">Seconds</span></span>                                                                 | <span data-ttu-id="5eff2-312">05</span><span class="sxs-lookup"><span data-stu-id="5eff2-312">05</span></span>                       |
| `%s` | <span data-ttu-id="5eff2-313">1970 00:00:00 1 월 1 일 이후 경과 된 시간 (초)</span><span class="sxs-lookup"><span data-stu-id="5eff2-313">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="5eff2-314">1150451174.95705</span><span class="sxs-lookup"><span data-stu-id="5eff2-314">1150451174.95705</span></span>         |
| `%t` | <span data-ttu-id="5eff2-315">가로 탭 문자</span><span class="sxs-lookup"><span data-stu-id="5eff2-315">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="5eff2-316">24 시간 형식의 시간</span><span class="sxs-lookup"><span data-stu-id="5eff2-316">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="5eff2-317">17:45:52</span><span class="sxs-lookup"><span data-stu-id="5eff2-317">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="5eff2-318">' W '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-318">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="5eff2-319">요일-번호</span><span class="sxs-lookup"><span data-stu-id="5eff2-319">Day of the week - number</span></span>                                                | <span data-ttu-id="5eff2-320">일요일 = 0</span><span class="sxs-lookup"><span data-stu-id="5eff2-320">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="5eff2-321">연간 주</span><span class="sxs-lookup"><span data-stu-id="5eff2-321">Week of the year</span></span>                                                        | <span data-ttu-id="5eff2-322">01-53</span><span class="sxs-lookup"><span data-stu-id="5eff2-322">01-53</span></span>                    |
| `%w` | <span data-ttu-id="5eff2-323">' U '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-323">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="5eff2-324">연간 주</span><span class="sxs-lookup"><span data-stu-id="5eff2-324">Week of the year</span></span>                                                        | <span data-ttu-id="5eff2-325">00-52</span><span class="sxs-lookup"><span data-stu-id="5eff2-325">00-52</span></span>                    |
| `%X` | <span data-ttu-id="5eff2-326">' T '와 동일</span><span class="sxs-lookup"><span data-stu-id="5eff2-326">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="5eff2-327">로캘의 표준 형식 날짜</span><span class="sxs-lookup"><span data-stu-id="5eff2-327">Date in standard format for locale</span></span>                                      | <span data-ttu-id="5eff2-328">영어 (미국)의 경우 06/27/19</span><span class="sxs-lookup"><span data-stu-id="5eff2-328">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="5eff2-329">4 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="5eff2-329">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="5eff2-330">2019</span><span class="sxs-lookup"><span data-stu-id="5eff2-330">2019</span></span>                     |
| `%y` | <span data-ttu-id="5eff2-331">2 자리 형식의 연도</span><span class="sxs-lookup"><span data-stu-id="5eff2-331">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="5eff2-332">19</span><span class="sxs-lookup"><span data-stu-id="5eff2-332">19</span></span>                       |
| `%Z` | <span data-ttu-id="5eff2-333">UTC (Universal Time 좌표의)의 표준 시간대 오프셋</span><span class="sxs-lookup"><span data-stu-id="5eff2-333">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="5eff2-334">-07</span><span class="sxs-lookup"><span data-stu-id="5eff2-334">-07</span></span>                      |

## <span data-ttu-id="5eff2-335">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5eff2-335">RELATED LINKS</span></span>

[<span data-ttu-id="5eff2-336">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="5eff2-336">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="5eff2-337">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="5eff2-337">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="5eff2-338">Get-Member</span><span class="sxs-lookup"><span data-stu-id="5eff2-338">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="5eff2-339">New-Item</span><span class="sxs-lookup"><span data-stu-id="5eff2-339">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="5eff2-340">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="5eff2-340">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="5eff2-341">Set-Date</span><span class="sxs-lookup"><span data-stu-id="5eff2-341">Set-Date</span></span>](Set-Date.md)
