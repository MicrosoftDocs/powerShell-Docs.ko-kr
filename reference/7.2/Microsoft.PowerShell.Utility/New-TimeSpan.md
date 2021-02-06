---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 5808685a5560d1cbf91c6705b90643c35702b28a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602679"
---
# <span data-ttu-id="3e449-102">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3e449-102">New-TimeSpan</span></span>

## <span data-ttu-id="3e449-103">개요</span><span class="sxs-lookup"><span data-stu-id="3e449-103">SYNOPSIS</span></span>
<span data-ttu-id="3e449-104">TimeSpan 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-104">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="3e449-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e449-105">SYNTAX</span></span>

### <span data-ttu-id="3e449-106">날짜 (기본값)</span><span class="sxs-lookup"><span data-stu-id="3e449-106">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="3e449-107">시간</span><span class="sxs-lookup"><span data-stu-id="3e449-107">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="3e449-108">설명</span><span class="sxs-lookup"><span data-stu-id="3e449-108">DESCRIPTION</span></span>

<span data-ttu-id="3e449-109">`New-TimeSpan`Cmdlet은 시간 간격을 나타내는 **TimeSpan** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-109">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="3e449-110">**TimeSpan** 개체를 사용 하 여 **DateTime** 개체에서 시간을 더하거나 뺄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-110">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="3e449-111">매개 변수를 사용 하지 않으면 `New-TimeSpan` 명령에서 시간 간격을 0으로 나타내는 **TimeSpan** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-111">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="3e449-112">예제</span><span class="sxs-lookup"><span data-stu-id="3e449-112">EXAMPLES</span></span>

### <span data-ttu-id="3e449-113">예제 1: 지정 된 기간 동안 TimeSpan 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3e449-113">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="3e449-114">이 명령은 기간이 1 시간에서 25 분인 **TimeSpan** 개체를 만들어 라는 변수에 저장 `$TimeSpan` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-114">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="3e449-115">**TimeSpan** 개체의 표현을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-115">It displays a representation of the **TimeSpan** object.</span></span>

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### <span data-ttu-id="3e449-116">예제 2: 시간 간격에 대 한 TimeSpan 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3e449-116">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="3e449-117">이 예제에서는 명령이 실행 된 시간과 1 월 2010 1 일 사이의 간격을 나타내는 새 **TimeSpan** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-117">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="3e449-118">**Start** 매개 변수의 기본값이 현재 날짜 및 시간 이므로이 명령에는 **start** 매개 변수가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-118">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="3e449-119">예 3: 현재 날짜 로부터 90 일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-119">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="3e449-120">이 명령은 현재 날짜부터 90일 후의 날짜를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-120">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="3e449-121">예제 4: 파일이 업데이트 된 후 TimeSpan 검색</span><span class="sxs-lookup"><span data-stu-id="3e449-121">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="3e449-122">이 명령은 [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) 도움말 파일이 마지막으로 업데이트 된 이후 경과 된 시간을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-122">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="3e449-123">모든 파일 또는 **LastWriteTime** 속성이 있는 다른 모든 개체에서이 명령 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-123">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="3e449-124">이 명령은의 **Start** 매개 변수가 `New-TimeSpan` **LastWriteTime** 의 별칭을 포함 하기 때문에 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-124">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime**.</span></span> <span data-ttu-id="3e449-125">**LastWriteTime** 속성이 있는 개체를로 파이프 하면 `New-TimeSpan` PowerShell에서 **LastWriteTime** 속성 값을 **Start** 매개 변수 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-125">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## <span data-ttu-id="3e449-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e449-126">PARAMETERS</span></span>

### <span data-ttu-id="3e449-127">-Days</span><span class="sxs-lookup"><span data-stu-id="3e449-127">-Days</span></span>

<span data-ttu-id="3e449-128">시간 범위의 날짜를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-128">Specifies the days in the time span.</span></span>
<span data-ttu-id="3e449-129">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-129">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e449-130">-끝</span><span class="sxs-lookup"><span data-stu-id="3e449-130">-End</span></span>

<span data-ttu-id="3e449-131">시간 범위의 끝을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-131">Specifies the end of a time span.</span></span>
<span data-ttu-id="3e449-132">기본값이 현재 날짜와 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-132">The default value is the current date and time.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e449-133">-시간</span><span class="sxs-lookup"><span data-stu-id="3e449-133">-Hours</span></span>

<span data-ttu-id="3e449-134">시간 범위의 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-134">Specifies the hours in the time span.</span></span>
<span data-ttu-id="3e449-135">기본값은 영입니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-135">The default value is zero.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e449-136">-분</span><span class="sxs-lookup"><span data-stu-id="3e449-136">-Minutes</span></span>

<span data-ttu-id="3e449-137">시간 범위의 분을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-137">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="3e449-138">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-138">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e449-139">-초</span><span class="sxs-lookup"><span data-stu-id="3e449-139">-Seconds</span></span>

<span data-ttu-id="3e449-140">시간 범위의 길이 (초)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-140">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="3e449-141">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-141">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e449-142">-시작</span><span class="sxs-lookup"><span data-stu-id="3e449-142">-Start</span></span>

<span data-ttu-id="3e449-143">시간 범위의 시작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-143">Specifies the start of a time span.</span></span>
<span data-ttu-id="3e449-144">날짜 및 시간을 나타내는 문자열 (예: "3/15/09") 또는 **DateTime** 개체 (예: 명령)를 입력 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-144">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="3e449-145">기본값이 현재 날짜와 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-145">The default value is the current date and time.</span></span>

<span data-ttu-id="3e449-146">**Start** 또는 해당 별칭인 **LastWriteTime** 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-146">You can use **Start** or its alias, **LastWriteTime**.</span></span>
<span data-ttu-id="3e449-147">**LastWriteTime** 별칭을 사용 하면 파일 시스템의 파일과 같이 **LastWriteTime** 속성이 있는 개체 `[System.Io.FileIO]` 를의 **시작** 매개 변수로 파이프 할 수 있습니다 `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="3e449-147">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e449-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e449-148">CommonParameters</span></span>

<span data-ttu-id="3e449-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e449-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e449-150">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e449-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3e449-151">입력</span><span class="sxs-lookup"><span data-stu-id="3e449-151">INPUTS</span></span>

### <span data-ttu-id="3e449-152">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="3e449-152">System.DateTime</span></span>

<span data-ttu-id="3e449-153">시작 시간을 나타내는 **DateTime** 개체를로 파이프 할 수 있습니다 `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="3e449-153">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="3e449-154">출력</span><span class="sxs-lookup"><span data-stu-id="3e449-154">OUTPUTS</span></span>

### <span data-ttu-id="3e449-155">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3e449-155">System.TimeSpan</span></span>

<span data-ttu-id="3e449-156">`New-TimeSpan` 시간 범위를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e449-156">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="3e449-157">참고</span><span class="sxs-lookup"><span data-stu-id="3e449-157">NOTES</span></span>

## <span data-ttu-id="3e449-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3e449-158">RELATED LINKS</span></span>

[<span data-ttu-id="3e449-159">가져오기-날짜</span><span class="sxs-lookup"><span data-stu-id="3e449-159">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="3e449-160">Set-Date</span><span class="sxs-lookup"><span data-stu-id="3e449-160">Set-Date</span></span>](Set-Date.md)

