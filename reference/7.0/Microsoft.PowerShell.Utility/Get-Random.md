---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 007f8f2e377af0620d439f5a35be51aace032dc1
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99496055"
---
# <span data-ttu-id="aae45-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="aae45-102">Get-Random</span></span>

## <span data-ttu-id="aae45-103">개요</span><span class="sxs-lookup"><span data-stu-id="aae45-103">SYNOPSIS</span></span>
<span data-ttu-id="aae45-104">난수를 가져오거나 컬렉션에서 개체를 임의로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="aae45-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aae45-105">SYNTAX</span></span>

### <span data-ttu-id="aae45-106">RandomNumberParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="aae45-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="aae45-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="aae45-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="aae45-108">설명</span><span class="sxs-lookup"><span data-stu-id="aae45-108">DESCRIPTION</span></span>

<span data-ttu-id="aae45-109">`Get-Random`Cmdlet은 임의로 선택 된 숫자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-109">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="aae45-110">개체의 컬렉션을에 제출 하면 `Get-Random` 컬렉션에서 임의로 선택 된 개체를 하나 이상 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-110">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="aae45-111">매개 변수 또는 입력을 사용 하지 않으면 `Get-Random` 명령에서 0 (영)과 **int32.maxvalue** (,) 사이의 임의로 선택 된 32 비트의 부호 없는 정수를 반환 `0x7FFFFFFF` `2,147,483,647` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-111">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="aae45-112">기본적으로는 `Get-Random` [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) 클래스를 사용 하 여 암호화 보안 임의성을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-112">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="aae45-113">의 매개 변수를 사용 `Get-Random` 하 여 최소값과 최대값, 컬렉션에서 반환 되는 개체 수 또는 초기값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-113">You can use the parameters of `Get-Random` to specify the minimum and maximum values, the number of objects returned from a collection, or a seed number.</span></span>

> [!CAUTION]
> <span data-ttu-id="aae45-114">초기값을 의도적으로 설정 하면 무작위로 반복 되는 동작이 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-114">Setting the seed deliberately results in non-random, repeatable behavior.</span></span> <span data-ttu-id="aae45-115">명령을 포함 하는 스크립트를 디버깅 하거나 분석 하는 경우와 같이 동작을 재현 하려는 경우에만 사용 해야 합니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="aae45-115">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="aae45-116">이 초기값은 `Get-Random` **setseed** 를 다시 사용 하거나 세션을 닫을 때까지 현재 명령 및 현재 세션의 모든 후속 명령에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-116">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="aae45-117">초기값을 기본값으로 다시 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-117">You can't reset the seed to its default value.</span></span>

## <span data-ttu-id="aae45-118">예제</span><span class="sxs-lookup"><span data-stu-id="aae45-118">EXAMPLES</span></span>

### <span data-ttu-id="aae45-119">예제 1: 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-119">Example 1: Get a random integer</span></span>

<span data-ttu-id="aae45-120">이 명령은 0에서 **int32.maxvalue** 사이의 임의의 정수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-120">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="aae45-121">예제 2:0에서 99 사이의 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-121">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="aae45-122">예 3:-100과 99 사이의 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-122">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="aae45-123">예제 4: 임의의 부동 소수점 숫자 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-123">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="aae45-124">이 명령은 10.7 이상 20.92 미만인 임의의 부동 소수점 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-124">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="aae45-125">예 5: 배열에서 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-125">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="aae45-126">이 명령은 지정된 배열에서 임의로 선택된 숫자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-126">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="aae45-127">예제 6: 배열에서 임의의 정수 몇 개 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-127">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="aae45-128">이 명령은 임의로 선택 된 세 개의 숫자를 배열에서 임의의 순서로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-128">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="aae45-129">예제 7: 전체 컬렉션 임의화</span><span class="sxs-lookup"><span data-stu-id="aae45-129">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="aae45-130">이 명령은 임의의 순서로 전체 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-130">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="aae45-131">**Count** 매개 변수 값은 정수의 **int32.maxvalue** 정적 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-131">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="aae45-132">전체 컬렉션을 임의의 순서로 반환하려면 컬렉션의 개체 수보다 크거나 같은 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-132">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="aae45-133">예 8: 숫자가 아닌 임의의 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-133">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="aae45-134">이 명령은 숫자가 아닌 컬렉션에서 임의의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-134">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="aae45-135">예 9: SetSeed 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="aae45-135">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="aae45-136">이 예제에서는 **SetSeed** 매개 변수를 사용할 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-136">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="aae45-137">**Setseed** 는 무작위 동작을 생성 하므로 일반적으로 스크립트를 디버깅 하거나 분석 하는 경우와 같이 결과를 재현 하는 데만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-137">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### <span data-ttu-id="aae45-138">예 10: 임의 파일 가져오기</span><span class="sxs-lookup"><span data-stu-id="aae45-138">Example 10: Get random files</span></span>

<span data-ttu-id="aae45-139">이 명령은 `C:` 로컬 컴퓨터의 드라이브에서 무작위로 선택 된 50 파일 샘플을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-139">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="aae45-140">예 11: 롤 박람회</span><span class="sxs-lookup"><span data-stu-id="aae45-140">Example 11: Roll fair dice</span></span>

<span data-ttu-id="aae45-141">이 예제는 공평 하 게 1200 시간을 롤백하고 결과를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-141">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="aae45-142">첫 번째 명령은 `ForEach-Object` `Get-Random` 파이프 된 (1-6)에서에 대 한 호출을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-142">The first command, `ForEach-Object` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="aae45-143">결과는를 사용 하 여 값으로 그룹화 되 `Group-Object` 고가 있는 테이블로 형식이 지정 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="aae45-143">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### <span data-ttu-id="aae45-144">예 12: Count 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="aae45-144">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="aae45-145">이제 개체를로 파이프 하지 않고 **Count** 매개 변수를 사용할 수 있습니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="aae45-145">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="aae45-146">다음 예제에서는 10 보다 작은 세 개의 난수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-146">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="aae45-147">예제 13: 빈 문자열이 나 $null를 사용 하 여 InputObject 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="aae45-147">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="aae45-148">이 예제에서 **InputObject** 매개 변수는 빈 문자열 () 및를 포함 하는 배열을 지정 합니다 `''` `$null` .</span><span class="sxs-lookup"><span data-stu-id="aae45-148">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="aae45-149">`Get-Random` 는 `a` , 빈 문자열 또는을 반환 `$null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-149">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="aae45-150">빈 문자열는 빈 줄로 표시 되 고 `$null` PowerShell 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-150">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="aae45-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aae45-151">PARAMETERS</span></span>

### <span data-ttu-id="aae45-152">-개수</span><span class="sxs-lookup"><span data-stu-id="aae45-152">-Count</span></span>

<span data-ttu-id="aae45-153">반환할 임의 개체 또는 숫자의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-153">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="aae45-154">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-154">The default is 1.</span></span>

<span data-ttu-id="aae45-155">에서 사용 하는 경우 `InputObject` **Count** 값이 컬렉션의 개체 수를 초과 하면는 `Get-Random` 임의의 순서로 개체를 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-155">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

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

### <span data-ttu-id="aae45-156">-InputObject</span><span class="sxs-lookup"><span data-stu-id="aae45-156">-InputObject</span></span>

<span data-ttu-id="aae45-157">개체 컬렉션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-157">Specifies a collection of objects.</span></span> <span data-ttu-id="aae45-158">`Get-Random` 컬렉션에서 **Count** 로 지정 된 수까지 임의로 선택 된 개체를 임의의 순서로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-158">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="aae45-159">개체, 개체가 포함된 변수, 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="aae45-159">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="aae45-160">개체의 컬렉션을로 파이프 할 수도 있습니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="aae45-160">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="aae45-161">PowerShell 7부터 **InputObject** 매개 변수는 빈 문자열 또는을 포함할 수 있는 배열을 허용 합니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="aae45-161">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="aae45-162">배열은 파이프라인 또는 **InputObject** 매개 변수 값으로 전송 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-162">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aae45-163">-최대</span><span class="sxs-lookup"><span data-stu-id="aae45-163">-Maximum</span></span>

<span data-ttu-id="aae45-164">난수의 최대값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-164">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="aae45-165">`Get-Random` 는 최대값 (같지 않음) 보다 작은 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-165">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="aae45-166">정수, 배정밀도 부동 소수점 수 또는 정수 또는 double로 변환할 수 있는 개체 (예: 숫자 문자열 ("100"))를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-166">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="aae45-167">**Maximum** 값은 **Minimum** 값보다 커야 하며 같으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-167">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="aae45-168">**Maximum** 또는 **Minimum** 값이 부동 소수점 숫자인 경우은 `Get-Random` 임의로 선택 된 부동 소수점 숫자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-168">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="aae45-169">64 비트 컴퓨터에서 **Minimum** 값이 32 비트 정수인 경우 **Maximum** 의 기본값은 **int32.maxvalue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-169">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="aae45-170">**Minimum** 값이 double (부동 소수점 숫자) 이면 **Maximum** 의 기본값은 **int32.maxvalue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-170">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="aae45-171">그렇지 않으면 기본값은 **int32.maxvalue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-171">Otherwise, the default value is **Int32.MaxValue**.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aae45-172">-최소</span><span class="sxs-lookup"><span data-stu-id="aae45-172">-Minimum</span></span>

<span data-ttu-id="aae45-173">난수의 최소값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-173">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="aae45-174">정수, 배정밀도 부동 소수점 수 또는 정수 또는 double로 변환할 수 있는 개체 (예: 숫자 문자열 ("100"))를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-174">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="aae45-175">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-175">The default value is 0 (zero).</span></span>

<span data-ttu-id="aae45-176">**Minimum** 값은 **Maximum** 값보다 작아야 하며 같으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-176">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="aae45-177">**Maximum** 또는 **Minimum** 값이 부동 소수점 숫자인 경우은 `Get-Random` 임의로 선택 된 부동 소수점 숫자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-177">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aae45-178">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="aae45-178">-SetSeed</span></span>

<span data-ttu-id="aae45-179">난수 생성기의 시드 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-179">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="aae45-180">**Setseed** 를 사용 하는 경우 [cmdlet은 system.string 메서드를](/dotnet/api/system.random) 사용 하 여 암호화 되지 않은 의사 난수를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-180">When you use **SetSeed**, the cmdlet uses the [System.Random](/dotnet/api/system.random) method to generate pseudorandom numbers, which is not cryptographically secure.</span></span>

> [!CAUTION]
> <span data-ttu-id="aae45-181">초기값을 설정 하면 불규칙 하지 않은 동작이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-181">Setting the seed results in non-random behavior.</span></span> <span data-ttu-id="aae45-182">명령을 포함 하는 스크립트를 디버깅 하거나 분석 하는 경우와 같이 동작을 재현 하려는 경우에만 사용 해야 합니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="aae45-182">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="aae45-183">이 초기값은 `Get-Random` **setseed** 를 다시 사용 하거나 세션을 닫을 때까지 현재 명령 및 현재 세션의 모든 후속 명령에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-183">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="aae45-184">초기값을 기본값으로 다시 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-184">You can't reset the seed to its default value.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aae45-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aae45-185">CommonParameters</span></span>

<span data-ttu-id="aae45-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aae45-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aae45-187">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aae45-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aae45-188">입력</span><span class="sxs-lookup"><span data-stu-id="aae45-188">INPUTS</span></span>

### <span data-ttu-id="aae45-189">System.Object</span><span class="sxs-lookup"><span data-stu-id="aae45-189">System.Object</span></span>

<span data-ttu-id="aae45-190">하나 이상의 개체를 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-190">You can pipe one or more objects.</span></span> <span data-ttu-id="aae45-191">`Get-Random` 파이프 된 개체에서 임의로 값을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-191">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="aae45-192">출력</span><span class="sxs-lookup"><span data-stu-id="aae45-192">OUTPUTS</span></span>

### <span data-ttu-id="aae45-193">System.object, system.object, system.string</span><span class="sxs-lookup"><span data-stu-id="aae45-193">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="aae45-194">`Get-Random` 정수 또는 부동 소수점 숫자를 반환 하거나, 전송 된 컬렉션에서 임의로 선택 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-194">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="aae45-195">참고</span><span class="sxs-lookup"><span data-stu-id="aae45-195">NOTES</span></span>

<span data-ttu-id="aae45-196">기본적으로는 `Get-Random` [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) 클래스를 사용 하 여 암호화 보안 임의성을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-196">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="aae45-197">`Get-Random` 는 항상 입력 값과 동일한 데이터 형식을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-197">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="aae45-198">다음 표에서는 각 숫자 입력 형식에 대 한 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-198">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="aae45-199">입력 형식</span><span class="sxs-lookup"><span data-stu-id="aae45-199">Input Type</span></span> | <span data-ttu-id="aae45-200">출력 형식</span><span class="sxs-lookup"><span data-stu-id="aae45-200">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="aae45-201">SByte</span><span class="sxs-lookup"><span data-stu-id="aae45-201">SByte</span></span>    |   <span data-ttu-id="aae45-202">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-202">Double</span></span>    |
|    <span data-ttu-id="aae45-203">Byte</span><span class="sxs-lookup"><span data-stu-id="aae45-203">Byte</span></span>    |   <span data-ttu-id="aae45-204">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-204">Double</span></span>    |
|   <span data-ttu-id="aae45-205">Int16</span><span class="sxs-lookup"><span data-stu-id="aae45-205">Int16</span></span>    |   <span data-ttu-id="aae45-206">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-206">Double</span></span>    |
|   <span data-ttu-id="aae45-207">UInt16</span><span class="sxs-lookup"><span data-stu-id="aae45-207">UInt16</span></span>   |   <span data-ttu-id="aae45-208">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-208">Double</span></span>    |
|   <span data-ttu-id="aae45-209">Int32</span><span class="sxs-lookup"><span data-stu-id="aae45-209">Int32</span></span>    |    <span data-ttu-id="aae45-210">Int32</span><span class="sxs-lookup"><span data-stu-id="aae45-210">Int32</span></span>    |
|   <span data-ttu-id="aae45-211">UInt32</span><span class="sxs-lookup"><span data-stu-id="aae45-211">UInt32</span></span>   |   <span data-ttu-id="aae45-212">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-212">Double</span></span>    |
|   <span data-ttu-id="aae45-213">Int64</span><span class="sxs-lookup"><span data-stu-id="aae45-213">Int64</span></span>    |    <span data-ttu-id="aae45-214">Int64</span><span class="sxs-lookup"><span data-stu-id="aae45-214">Int64</span></span>    |
|   <span data-ttu-id="aae45-215">UInt64</span><span class="sxs-lookup"><span data-stu-id="aae45-215">UInt64</span></span>   |   <span data-ttu-id="aae45-216">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-216">Double</span></span>    |
|   <span data-ttu-id="aae45-217">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-217">Double</span></span>   |   <span data-ttu-id="aae45-218">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-218">Double</span></span>    |
|   <span data-ttu-id="aae45-219">Single</span><span class="sxs-lookup"><span data-stu-id="aae45-219">Single</span></span>   |   <span data-ttu-id="aae45-220">Double</span><span class="sxs-lookup"><span data-stu-id="aae45-220">Double</span></span>    |

<span data-ttu-id="aae45-221">Windows PowerShell 3.0부터는 `Get-Random` 64 비트 정수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-221">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="aae45-222">Windows PowerShell 2.0에서는 모든 값이 **system.object** 로 캐스팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-222">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="aae45-223">PowerShell 7부터 **RandomListItemParameterSet** 매개 변수 집합의 **InputObject** 매개 변수는 빈 문자열이 나를 포함 하는 배열을 허용 합니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="aae45-223">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="aae45-224">이전 PowerShell 버전에서는 **RandomNumberParameterSet** 매개 변수 집합의 **Maximum** 매개 변수만 빈 문자열 또는을 수락 `$null` 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aae45-224">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="aae45-225">관련 링크</span><span class="sxs-lookup"><span data-stu-id="aae45-225">RELATED LINKS</span></span>

[<span data-ttu-id="aae45-226">RandomNumberGenerator ()</span><span class="sxs-lookup"><span data-stu-id="aae45-226">System.Security.Cryptography.RandomNumberGenerator()</span></span>](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[<span data-ttu-id="aae45-227">. 무작위</span><span class="sxs-lookup"><span data-stu-id="aae45-227">Sytem.Random</span></span>](/dotnet/api/system.random)
