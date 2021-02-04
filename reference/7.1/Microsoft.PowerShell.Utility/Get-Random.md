---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 842d4ea92f60a92fddcddea11bb8155c708ac192
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99495962"
---
# <span data-ttu-id="d351d-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="d351d-102">Get-Random</span></span>

## <span data-ttu-id="d351d-103">개요</span><span class="sxs-lookup"><span data-stu-id="d351d-103">SYNOPSIS</span></span>
<span data-ttu-id="d351d-104">난수를 가져오거나 컬렉션에서 개체를 임의로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="d351d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d351d-105">SYNTAX</span></span>

### <span data-ttu-id="d351d-106">RandomNumberParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="d351d-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="d351d-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="d351d-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="d351d-108">ShuffleParameterSet</span><span class="sxs-lookup"><span data-stu-id="d351d-108">ShuffleParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## <span data-ttu-id="d351d-109">설명</span><span class="sxs-lookup"><span data-stu-id="d351d-109">DESCRIPTION</span></span>

<span data-ttu-id="d351d-110">`Get-Random`Cmdlet은 임의로 선택 된 숫자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="d351d-111">개체의 컬렉션을에 제출 하면 `Get-Random` 컬렉션에서 임의로 선택 된 개체를 하나 이상 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="d351d-112">매개 변수 또는 입력을 사용 하지 않으면 `Get-Random` 명령에서 0 (영)과 **int32.maxvalue** (,) 사이의 임의로 선택 된 32 비트의 부호 없는 정수를 반환 `0x7FFFFFFF` `2,147,483,647` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="d351d-113">기본적으로는 `Get-Random` [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) 클래스를 사용 하 여 암호화 보안 임의성을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-113">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="d351d-114">의 매개 변수를 사용 `Get-Random` 하 여 최소값과 최대값, 컬렉션에서 반환 되는 개체 수 또는 초기값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-114">You can use the parameters of `Get-Random` to specify the minimum and maximum values, the number of objects returned from a collection, or a seed number.</span></span>

> [!CAUTION]
> <span data-ttu-id="d351d-115">초기값을 의도적으로 설정 하면 무작위로 반복 되는 동작이 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-115">Setting the seed deliberately results in non-random, repeatable behavior.</span></span> <span data-ttu-id="d351d-116">명령을 포함 하는 스크립트를 디버깅 하거나 분석 하는 경우와 같이 동작을 재현 하려는 경우에만 사용 해야 합니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="d351d-116">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="d351d-117">이 초기값은 `Get-Random` **setseed** 를 다시 사용 하거나 세션을 닫을 때까지 현재 명령 및 현재 세션의 모든 후속 명령에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-117">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="d351d-118">초기값을 기본값으로 다시 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-118">You can't reset the seed to its default value.</span></span>

## <span data-ttu-id="d351d-119">예제</span><span class="sxs-lookup"><span data-stu-id="d351d-119">EXAMPLES</span></span>

### <span data-ttu-id="d351d-120">예제 1: 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-120">Example 1: Get a random integer</span></span>

<span data-ttu-id="d351d-121">이 명령은 0에서 **int32.maxvalue** 사이의 임의의 정수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-121">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="d351d-122">예제 2:0에서 99 사이의 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-122">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="d351d-123">예 3:-100과 99 사이의 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-123">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="d351d-124">예제 4: 임의의 부동 소수점 숫자 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-124">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="d351d-125">이 명령은 10.7 이상 20.92 미만인 임의의 부동 소수점 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-125">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="d351d-126">예 5: 배열에서 임의의 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-126">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="d351d-127">이 명령은 지정된 배열에서 임의로 선택된 숫자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-127">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="d351d-128">예제 6: 배열에서 임의의 정수 몇 개 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-128">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="d351d-129">이 명령은 임의로 선택 된 세 개의 숫자를 배열에서 임의의 순서로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-129">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="d351d-130">예제 7: 전체 컬렉션 임의화</span><span class="sxs-lookup"><span data-stu-id="d351d-130">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="d351d-131">PowerShell 7.1부터 **무작위 매개 변수를 사용** 하 여 전체 컬렉션을 임의의 순서로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-131">Starting in PowerShell 7.1, you can use the **Shuffle** parameter to return the entire collection in a random order.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="d351d-132">예 8: 숫자가 아닌 임의의 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-132">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="d351d-133">이 명령은 숫자가 아닌 컬렉션에서 임의의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-133">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="d351d-134">예 9: SetSeed 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="d351d-134">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="d351d-135">이 예제에서는 **SetSeed** 매개 변수를 사용할 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-135">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="d351d-136">**Setseed** 는 무작위 동작을 생성 하므로 일반적으로 스크립트를 디버깅 하거나 분석 하는 경우와 같이 결과를 재현 하는 데만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-136">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="d351d-137">예 10: 임의 파일 가져오기</span><span class="sxs-lookup"><span data-stu-id="d351d-137">Example 10: Get random files</span></span>

<span data-ttu-id="d351d-138">이 명령은 `C:` 로컬 컴퓨터의 드라이브에서 무작위로 선택 된 50 파일 샘플을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-138">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="d351d-139">예 11: 롤 박람회</span><span class="sxs-lookup"><span data-stu-id="d351d-139">Example 11: Roll fair dice</span></span>

<span data-ttu-id="d351d-140">이 예제는 공평 하 게 1200 시간을 롤백하고 결과를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-140">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="d351d-141">첫 번째 명령은 `ForEach-Object` `Get-Random` 파이프 된 (1-6)에서에 대 한 호출을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-141">The first command, `ForEach-Object` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="d351d-142">결과는를 사용 하 여 값으로 그룹화 되 `Group-Object` 고가 있는 테이블로 형식이 지정 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="d351d-142">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="d351d-143">예 12: Count 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="d351d-143">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="d351d-144">이제 개체를로 파이프 하지 않고 **Count** 매개 변수를 사용할 수 있습니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="d351d-144">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="d351d-145">다음 예제에서는 10 보다 작은 세 개의 난수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-145">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="d351d-146">예제 13: 빈 문자열이 나 $null를 사용 하 여 InputObject 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="d351d-146">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="d351d-147">이 예제에서 **InputObject** 매개 변수는 빈 문자열 () 및를 포함 하는 배열을 지정 합니다 `''` `$null` .</span><span class="sxs-lookup"><span data-stu-id="d351d-147">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="d351d-148">`Get-Random` 는 `a` , 빈 문자열 또는을 반환 `$null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-148">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="d351d-149">빈 문자열는 빈 줄로 표시 되 고 `$null` PowerShell 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-149">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="d351d-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d351d-150">PARAMETERS</span></span>

### <span data-ttu-id="d351d-151">-개수</span><span class="sxs-lookup"><span data-stu-id="d351d-151">-Count</span></span>

<span data-ttu-id="d351d-152">반환할 임의 개체 또는 숫자의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-152">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="d351d-153">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-153">The default is 1.</span></span>

<span data-ttu-id="d351d-154">에서 사용 하는 경우 `InputObject` **Count** 값이 컬렉션의 개체 수를 초과 하면는 `Get-Random` 임의의 순서로 개체를 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-154">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d351d-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d351d-155">-InputObject</span></span>

<span data-ttu-id="d351d-156">개체 컬렉션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-156">Specifies a collection of objects.</span></span> <span data-ttu-id="d351d-157">`Get-Random` 컬렉션에서 **Count** 로 지정 된 수까지 임의로 선택 된 개체를 임의의 순서로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-157">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="d351d-158">개체, 개체가 포함된 변수, 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="d351d-158">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="d351d-159">개체의 컬렉션을로 파이프 할 수도 있습니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="d351d-159">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="d351d-160">PowerShell 7부터 **InputObject** 매개 변수는 빈 문자열 또는을 포함할 수 있는 배열을 허용 합니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="d351d-160">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="d351d-161">배열은 파이프라인 또는 **InputObject** 매개 변수 값으로 전송 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-161">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d351d-162">-최대</span><span class="sxs-lookup"><span data-stu-id="d351d-162">-Maximum</span></span>

<span data-ttu-id="d351d-163">난수의 최대값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-163">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="d351d-164">`Get-Random` 는 최대값 (같지 않음) 보다 작은 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-164">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="d351d-165">정수, 배정밀도 부동 소수점 수 또는 정수 또는 double로 변환할 수 있는 개체 (예: 숫자 문자열 ("100"))를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-165">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="d351d-166">**Maximum** 값은 **Minimum** 값보다 커야 하며 같으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-166">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="d351d-167">**Maximum** 또는 **Minimum** 값이 부동 소수점 숫자인 경우은 `Get-Random` 임의로 선택 된 부동 소수점 숫자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-167">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="d351d-168">64 비트 컴퓨터에서 **Minimum** 값이 32 비트 정수인 경우 **Maximum** 의 기본값은 **int32.maxvalue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-168">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="d351d-169">**Minimum** 값이 double (부동 소수점 숫자) 이면 **Maximum** 의 기본값은 **int32.maxvalue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-169">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="d351d-170">그렇지 않으면 기본값은 **int32.maxvalue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-170">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="d351d-171">-최소</span><span class="sxs-lookup"><span data-stu-id="d351d-171">-Minimum</span></span>

<span data-ttu-id="d351d-172">난수의 최소값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-172">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="d351d-173">정수, 배정밀도 부동 소수점 수 또는 정수 또는 double로 변환할 수 있는 개체 (예: 숫자 문자열 ("100"))를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-173">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="d351d-174">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-174">The default value is 0 (zero).</span></span>

<span data-ttu-id="d351d-175">**Minimum** 값은 **Maximum** 값보다 작아야 하며 같으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-175">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="d351d-176">**Maximum** 또는 **Minimum** 값이 부동 소수점 숫자인 경우은 `Get-Random` 임의로 선택 된 부동 소수점 숫자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-176">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="d351d-177">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="d351d-177">-SetSeed</span></span>

<span data-ttu-id="d351d-178">난수 생성기의 시드 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-178">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="d351d-179">**Setseed** 를 사용 하는 경우 [cmdlet은 system.string 메서드를](/dotnet/api/system.random) 사용 하 여 암호화 되지 않은 의사 난수를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-179">When you use **SetSeed**, the cmdlet uses the [System.Random](/dotnet/api/system.random) method to generate pseudorandom numbers, which is not cryptographically secure.</span></span>

> [!CAUTION]
> <span data-ttu-id="d351d-180">초기값을 설정 하면 불규칙 하지 않은 동작이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-180">Setting the seed results in non-random behavior.</span></span> <span data-ttu-id="d351d-181">명령을 포함 하는 스크립트를 디버깅 하거나 분석 하는 경우와 같이 동작을 재현 하려는 경우에만 사용 해야 합니다 `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="d351d-181">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="d351d-182">이 초기값은 `Get-Random` **setseed** 를 다시 사용 하거나 세션을 닫을 때까지 현재 명령 및 현재 세션의 모든 후속 명령에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-182">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="d351d-183">초기값을 기본값으로 다시 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-183">You can't reset the seed to its default value.</span></span>

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

### <span data-ttu-id="d351d-184">-순서 섞기</span><span class="sxs-lookup"><span data-stu-id="d351d-184">-Shuffle</span></span>

<span data-ttu-id="d351d-185">전체 컬렉션을 임의의 순서로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-185">Returns the entire collection in a randomized order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d351d-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d351d-186">CommonParameters</span></span>

<span data-ttu-id="d351d-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d351d-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d351d-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d351d-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d351d-189">입력</span><span class="sxs-lookup"><span data-stu-id="d351d-189">INPUTS</span></span>

### <span data-ttu-id="d351d-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="d351d-190">System.Object</span></span>

<span data-ttu-id="d351d-191">하나 이상의 개체를 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-191">You can pipe one or more objects.</span></span> <span data-ttu-id="d351d-192">`Get-Random` 파이프 된 개체에서 임의로 값을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-192">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="d351d-193">출력</span><span class="sxs-lookup"><span data-stu-id="d351d-193">OUTPUTS</span></span>

### <span data-ttu-id="d351d-194">System.object, system.object, system.string</span><span class="sxs-lookup"><span data-stu-id="d351d-194">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="d351d-195">`Get-Random` 정수 또는 부동 소수점 숫자를 반환 하거나, 전송 된 컬렉션에서 임의로 선택 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-195">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="d351d-196">참고</span><span class="sxs-lookup"><span data-stu-id="d351d-196">NOTES</span></span>

<span data-ttu-id="d351d-197">기본적으로는 `Get-Random` [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) 클래스를 사용 하 여 암호화 보안 임의성을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-197">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="d351d-198">`Get-Random` 는 항상 입력 값과 동일한 데이터 형식을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-198">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="d351d-199">다음 표에서는 각 숫자 입력 형식에 대 한 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-199">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="d351d-200">입력 형식</span><span class="sxs-lookup"><span data-stu-id="d351d-200">Input Type</span></span> | <span data-ttu-id="d351d-201">출력 형식</span><span class="sxs-lookup"><span data-stu-id="d351d-201">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="d351d-202">SByte</span><span class="sxs-lookup"><span data-stu-id="d351d-202">SByte</span></span>    |   <span data-ttu-id="d351d-203">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-203">Double</span></span>    |
|    <span data-ttu-id="d351d-204">Byte</span><span class="sxs-lookup"><span data-stu-id="d351d-204">Byte</span></span>    |   <span data-ttu-id="d351d-205">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-205">Double</span></span>    |
|   <span data-ttu-id="d351d-206">Int16</span><span class="sxs-lookup"><span data-stu-id="d351d-206">Int16</span></span>    |   <span data-ttu-id="d351d-207">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-207">Double</span></span>    |
|   <span data-ttu-id="d351d-208">UInt16</span><span class="sxs-lookup"><span data-stu-id="d351d-208">UInt16</span></span>   |   <span data-ttu-id="d351d-209">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-209">Double</span></span>    |
|   <span data-ttu-id="d351d-210">Int32</span><span class="sxs-lookup"><span data-stu-id="d351d-210">Int32</span></span>    |    <span data-ttu-id="d351d-211">Int32</span><span class="sxs-lookup"><span data-stu-id="d351d-211">Int32</span></span>    |
|   <span data-ttu-id="d351d-212">UInt32</span><span class="sxs-lookup"><span data-stu-id="d351d-212">UInt32</span></span>   |   <span data-ttu-id="d351d-213">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-213">Double</span></span>    |
|   <span data-ttu-id="d351d-214">Int64</span><span class="sxs-lookup"><span data-stu-id="d351d-214">Int64</span></span>    |    <span data-ttu-id="d351d-215">Int64</span><span class="sxs-lookup"><span data-stu-id="d351d-215">Int64</span></span>    |
|   <span data-ttu-id="d351d-216">UInt64</span><span class="sxs-lookup"><span data-stu-id="d351d-216">UInt64</span></span>   |   <span data-ttu-id="d351d-217">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-217">Double</span></span>    |
|   <span data-ttu-id="d351d-218">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-218">Double</span></span>   |   <span data-ttu-id="d351d-219">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-219">Double</span></span>    |
|   <span data-ttu-id="d351d-220">Single</span><span class="sxs-lookup"><span data-stu-id="d351d-220">Single</span></span>   |   <span data-ttu-id="d351d-221">Double</span><span class="sxs-lookup"><span data-stu-id="d351d-221">Double</span></span>    |

<span data-ttu-id="d351d-222">Windows PowerShell 3.0부터는 `Get-Random` 64 비트 정수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-222">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="d351d-223">Windows PowerShell 2.0에서는 모든 값이 **system.object** 로 캐스팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-223">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="d351d-224">PowerShell 7부터 **RandomListItemParameterSet** 매개 변수 집합의 **InputObject** 매개 변수는 빈 문자열이 나를 포함 하는 배열을 허용 합니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="d351d-224">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="d351d-225">이전 PowerShell 버전에서는 **RandomNumberParameterSet** 매개 변수 집합의 **Maximum** 매개 변수만 빈 문자열 또는을 수락 `$null` 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d351d-225">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="d351d-226">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d351d-226">RELATED LINKS</span></span>

[<span data-ttu-id="d351d-227">RandomNumberGenerator ()</span><span class="sxs-lookup"><span data-stu-id="d351d-227">System.Security.Cryptography.RandomNumberGenerator()</span></span>](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[<span data-ttu-id="d351d-228">. 무작위</span><span class="sxs-lookup"><span data-stu-id="d351d-228">Sytem.Random</span></span>](/dotnet/api/system.random)
