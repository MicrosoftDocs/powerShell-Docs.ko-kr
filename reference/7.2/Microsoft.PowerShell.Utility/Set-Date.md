---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 0f35eea0dfca76b535aad3bdb663d55c224a11d2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600125"
---
# <span data-ttu-id="8ed51-102">Set-Date</span><span class="sxs-lookup"><span data-stu-id="8ed51-102">Set-Date</span></span>

## <span data-ttu-id="8ed51-103">개요</span><span class="sxs-lookup"><span data-stu-id="8ed51-103">SYNOPSIS</span></span>
<span data-ttu-id="8ed51-104">컴퓨터의 시스템 시간을 지정한 시간으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-104">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="8ed51-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ed51-105">SYNTAX</span></span>

### <span data-ttu-id="8ed51-106">날짜 (기본값)</span><span class="sxs-lookup"><span data-stu-id="8ed51-106">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ed51-107">Adjust</span><span class="sxs-lookup"><span data-stu-id="8ed51-107">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8ed51-108">설명</span><span class="sxs-lookup"><span data-stu-id="8ed51-108">DESCRIPTION</span></span>

<span data-ttu-id="8ed51-109">`Set-Date`Cmdlet은 컴퓨터의 시스템 날짜 및 시간을 지정한 날짜 및 시간으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-109">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="8ed51-110">문자열을 입력 하거나 **DateTime** 또는 **TimeSpan** 개체를에 전달 하 여 새 날짜 및/또는 시간을 지정할 수 있습니다 `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-110">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="8ed51-111">새 날짜 또는 시간을 지정 하려면 **date** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-111">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="8ed51-112">변경 간격을 지정 하려면 **조정** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-112">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="8ed51-113">예제</span><span class="sxs-lookup"><span data-stu-id="8ed51-113">EXAMPLES</span></span>

### <span data-ttu-id="8ed51-114">예 1: 시스템 날짜에 3 일 추가</span><span class="sxs-lookup"><span data-stu-id="8ed51-114">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="8ed51-115">이 명령은 현재 시스템 날짜에 3일을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-115">This command adds three days to the current system date.</span></span>
<span data-ttu-id="8ed51-116">시간에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-116">It does not affect the time.</span></span>
<span data-ttu-id="8ed51-117">이 명령은 **date** 매개 변수를 사용 하 여 날짜를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-117">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="8ed51-118">이 `Get-Date` cmdlet은 현재 날짜를 **DateTime** 개체로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-118">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="8ed51-119">**Datetime** 개체의 **AddDays** 메서드는 지정 된 일 수 (3)를 현재 **DateTime** 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-119">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="8ed51-120">예 2: 시스템 클록을 10 분 뒤로 설정</span><span class="sxs-lookup"><span data-stu-id="8ed51-120">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="8ed51-121">이 예에서는 현재 시스템 시간을 10 분 뒤로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-121">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="8ed51-122">**조정** 매개 변수를 사용 하 여 로캘의 표준 시간 형식에서 변경 간격 (10 분을 뺀 값)을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-122">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="8ed51-123">**Displayhint** 매개 변수는 PowerShell에 시간만 표시 하도록 지시 하지만을 반환 하는 **DateTime** 개체에는 영향을 주지 않습니다 `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-123">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="8ed51-124">예제 3: 날짜 및 시간을 변수 값으로 설정</span><span class="sxs-lookup"><span data-stu-id="8ed51-124">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="8ed51-125">이 명령은 로컬 컴퓨터의 시스템 날짜 및 시간을 변수에 저장 된 날짜 및 시간으로 변경 합니다 `$T` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-125">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="8ed51-126">첫 번째 명령은 날짜를 가져와에 저장 `$T` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-126">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="8ed51-127">두 번째 명령은 **Date** 매개 변수를 사용 하 여의 **DateTime** 개체를 cmdlet에 전달 합니다 `$T` `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-127">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="8ed51-128">예제 4: 시스템 클록에 90 분 추가</span><span class="sxs-lookup"><span data-stu-id="8ed51-128">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="8ed51-129">이 명령은 로컬 컴퓨터의 시스템 시간을 90분 후로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-129">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="8ed51-130">첫 번째 명령은 cmdlet을 사용 하 여 `New-TimeSpan` 90 분 간격의 **TimeSpan** 개체를 만든 다음 변수에 저장 합니다 `$90mins` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-130">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="8ed51-131">두 번째 명령은의 **조정** 매개 변수를 사용 하 여 `Set-Date` 변수에서 **TimeSpan** 개체의 값으로 날짜를 조정 합니다 `$90mins` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-131">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="8ed51-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ed51-132">PARAMETERS</span></span>

### <span data-ttu-id="8ed51-133">-조정</span><span class="sxs-lookup"><span data-stu-id="8ed51-133">-Adjust</span></span>

<span data-ttu-id="8ed51-134">이 cmdlet이 현재 날짜 및 시간에서 추가 하거나 빼는 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-134">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="8ed51-135">로캘에 대 한 표준 날짜 및 시간 형식 조정을 입력 하거나, **조정** 매개 변수를 사용 하 여에서로 **TimeSpan** 개체를 전달할 수 있습니다 `New-TimeSpan` `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-135">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ed51-136">-날짜</span><span class="sxs-lookup"><span data-stu-id="8ed51-136">-Date</span></span>

<span data-ttu-id="8ed51-137">날짜 및 시간을 지정한 값으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-137">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="8ed51-138">새 날짜를 간단한 날짜 형식으로 입력하고 시간을 해당 로캘의 표준 시간 형식으로 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-138">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="8ed51-139">또는에서 **DateTime** 개체를 전달할 수 있습니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-139">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="8ed51-140">날짜를 지정 하 고 시간을 지정 하지 않으면 `Set-Date` 지정 된 날짜의 자정으로 시간을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-140">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="8ed51-141">시간만 지정할 경우 날짜는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-141">If you specify only a time, it does not change the date.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8ed51-142">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="8ed51-142">-DisplayHint</span></span>

<span data-ttu-id="8ed51-143">표시 되는 날짜 및 시간 요소를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-143">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8ed51-144">**날짜** -날짜만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-144">**Date** - displays only the date.</span></span>
- <span data-ttu-id="8ed51-145">**시간** -시간만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-145">**Time** - displays only the time.</span></span>
- <span data-ttu-id="8ed51-146">날짜 **/시간-날짜** 및 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-146">**DateTime** - displays the date and time.</span></span>

<span data-ttu-id="8ed51-147">이 매개 변수는 표시에만 영향을 주고</span><span class="sxs-lookup"><span data-stu-id="8ed51-147">This parameter affects only the display.</span></span>
<span data-ttu-id="8ed51-148">을 검색 하는 **DateTime** 개체에는 영향을 주지 않습니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-148">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

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

### <span data-ttu-id="8ed51-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8ed51-149">-Confirm</span></span>

<span data-ttu-id="8ed51-150">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8ed51-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8ed51-151">-WhatIf</span></span>

<span data-ttu-id="8ed51-152">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8ed51-153">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8ed51-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ed51-154">CommonParameters</span></span>

<span data-ttu-id="8ed51-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8ed51-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ed51-156">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed51-156">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8ed51-157">입력</span><span class="sxs-lookup"><span data-stu-id="8ed51-157">INPUTS</span></span>

### <span data-ttu-id="8ed51-158">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="8ed51-158">System.DateTime</span></span>

<span data-ttu-id="8ed51-159">날짜를로 파이프 할 수 있습니다 `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="8ed51-159">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="8ed51-160">출력</span><span class="sxs-lookup"><span data-stu-id="8ed51-160">OUTPUTS</span></span>

### <span data-ttu-id="8ed51-161">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="8ed51-161">System.DateTime</span></span>

<span data-ttu-id="8ed51-162">`Set-Date` 설정 된 날짜를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-162">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="8ed51-163">참고</span><span class="sxs-lookup"><span data-stu-id="8ed51-163">NOTES</span></span>

- <span data-ttu-id="8ed51-164">컴퓨터의 날짜 및 시간을 변경할 때이 cmdlet을 사용 하면 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-164">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="8ed51-165">이 변경 내용으로 인해 컴퓨터가 날짜 또는 시간에 의해 트리거되는 시스템 전체 이벤트 및 업데이트를 받지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-165">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="8ed51-166">오류를 방지 하려면 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-166">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="8ed51-167">  `Set-Date` **AddDays**, **addmonths** 및 **fromfiletime** 과 같이와 함께 사용 되는 DateTime 및 TimeSpan 개체에 표준 .net 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed51-167">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays**, **AddMonths**, and **FromFileTime**.</span></span> <span data-ttu-id="8ed51-168">자세한 내용은 [DateTime 메서드](/dotnet/api/system.datetime) 및를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed51-168">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="8ed51-169">.NET SDK의 [TimeSpan 메서드](/dotnet/api/system.timespan) .</span><span class="sxs-lookup"><span data-stu-id="8ed51-169">[TimeSpan Methods](/dotnet/api/system.timespan) in the .NET SDK.</span></span>

## <span data-ttu-id="8ed51-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8ed51-170">RELATED LINKS</span></span>

[<span data-ttu-id="8ed51-171">가져오기-날짜</span><span class="sxs-lookup"><span data-stu-id="8ed51-171">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="8ed51-172">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8ed51-172">New-TimeSpan</span></span>](New-TimeSpan.md)
