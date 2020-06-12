---
title: 흐름 제어
description: PowerShell은 스크립트에서 루프를 만들고, 결정을 내리고, 코드 흐름을 논리적으로 제어하는 방법을 제공합니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437994"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="54237-103">6장 - 흐름 제어</span><span class="sxs-lookup"><span data-stu-id="54237-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="54237-104">스크립팅</span><span class="sxs-lookup"><span data-stu-id="54237-104">Scripting</span></span>

<span data-ttu-id="54237-105">PowerShell 원라이너 작성에서 스크립트 작성으로 전환하는 경우 실제로 그런 것보다 훨씬 복잡하게 들립니다.</span><span class="sxs-lookup"><span data-stu-id="54237-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="54237-106">스크립트는 `.PS1` 파일로 저장된다는 점을 제외하면 PowerShell 콘솔에서 대화형으로 실행하는 동일한 또는 비슷한 명령일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="54237-107">`foreach` 루프와 같이 `ForEach-Object` cmdlet 대신 사용할 수 있는 몇 가지 스크립팅 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="54237-108">`foreach`가 스크립팅 구문이기도 하고 `ForEach-Object` cmdlet의 별칭이기도 하다는 점을 고려하면 초보자에게는 이러한 차이가 혼동스러울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="54237-109">반복</span><span class="sxs-lookup"><span data-stu-id="54237-109">Looping</span></span>

<span data-ttu-id="54237-110">PowerShell의 편리한 점 한 가지는 하나의 항목에 대해 작업을 수행하는 방법을 이해하면 수백 개의 항목에 대해 동일한 작업을 쉽게 수행할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="54237-111">PowerShell에서 다양한 유형의 루프 중 하나를 사용하여 항목을 반복하면 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="54237-112">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="54237-112">ForEach-Object</span></span>

<span data-ttu-id="54237-113">`ForEach-Object`는 PowerShell 원라이너와 같은 파이프라인에서 항목을 반복하기 위한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="54237-114">`ForEach-Object`는 파이프라인을 통해 개체를 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="54237-115">`Get-Command`의 **Module** 매개 변수는 여러 개의 문자열 값을 허용하지만 파이프라인 입력을 통해 속성 이름 기준으로 또는 파라미터 입력을 통해서만 값을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="54237-116">다음 시나리오에서는 **Module** 매개 변수와 함께 사용하기 위해 값 기준으로 두 문자열을 `Get-Command`로 파이프하려면 `ForEach-Object` cmdlet을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="54237-117">이전 예제에서 `$_`는 현재 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="54237-118">PowerShell 버전 3.0부터 `$_` 대신 `$PSItem`을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="54237-119">하지만 대부분의 숙련된 PowerShell 사용자는 여전히 `$_`를 사용합니다. 이전 버전과 호환되고 타이핑할 필요가 적기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="54237-120">`foreach` 키워드를 사용하는 경우 항목을 반복하기 전에 메모리에 모든 항목을 저장해야 합니다. 작업하는 항목의 수를 모르는 경우에는 어려움이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="54237-121">많은 경우에 `foreach` 또는 `ForEach-Object`와 같은 루프가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="54237-122">그렇지 않으면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="54237-123">다른 경우에는 루프를 완전히 배제하면서 동일한 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="54237-124">어떤 옵션이 있는지 알아보려면 cmdlet 도움말을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54237-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="54237-125">이전 예제에서 볼 수 있듯이 `Get-ADComputer`의 **Identity** 매개 변수는 매개 변수 입력을 통해 제공되는 경우 단일 값만 허용하지만 입력이 파이프라인 입력을 통해 제공되는 경우 여러 항목을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="54237-126">For</span><span class="sxs-lookup"><span data-stu-id="54237-126">For</span></span>

<span data-ttu-id="54237-127">지정된 조건이 true인 동안 `for` 루프가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="54237-128">`for` 루프는 자주 사용되지는 않지만 나름대로의 용도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="54237-129">이전 예제에서 루프는 숫자 1부터 시작하여 카운터 변수 `$i`가 5보다 작은 동안 계속되어 총 4번 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="54237-130">총 10초 동안 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="54237-131">해야 할 일</span><span class="sxs-lookup"><span data-stu-id="54237-131">Do</span></span>

<span data-ttu-id="54237-132">PowerShell에는 두 가지 `do` 루프가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="54237-133">`Do Until`은 지정된 조건이 false인 동안 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="54237-134">이전 예제는 추측하는 값이 `Get-Random` cmdlet에서 생성한 것과 동일한 숫자가 될 때까지 계속되는 숫자 게임입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="54237-135">`Do While`은 반대입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="54237-136">지정된 조건이 true로 평가되는 동안 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="54237-137">테스트 조건을 같지 않음으로 뒤집어 `Do While` 루프를 사용하면 동일한 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="54237-138">`Do` 루프는 항상 한 번 이상 실행됩니다. 루프의 끝에서 조건이 평가되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="54237-139">While</span><span class="sxs-lookup"><span data-stu-id="54237-139">While</span></span>

<span data-ttu-id="54237-140">`While` 루프는 `Do While` 루프와 마찬가지로 지정된 조건이 true인 동안 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="54237-141">그러나 `While` 루프는 코드가 실행되기 전에 루프 맨 위에 있는 조건을 평가한다는 것이 차이점입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="54237-142">따라서 조건이 false로 평가되는 경우 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="54237-143">이전 예제에서는 미국에서 추수감사절 날짜를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="54237-144">추수감사절은 항상 11월의 네 번째 목요일입니다.</span><span class="sxs-lookup"><span data-stu-id="54237-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="54237-145">따라서 루프가 11월의 22번째 날부터 시작하고 요일이 목요일이 아닌 동안 하루를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="54237-146">22번째가 목요일이면 루프가 전혀 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="54237-147">중단, 계속 및 반환</span><span class="sxs-lookup"><span data-stu-id="54237-147">Break, Continue, and Return</span></span>

<span data-ttu-id="54237-148">`Break`는 루프를 중단하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="54237-149">일반적으로 `switch` 문과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="54237-150">이전 예제에 표시된 `break` 문을 실행하면 첫 번째 반복에서 루프가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="54237-151">Continue는 루프의 다음 반복으로 건너뛰도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="54237-152">이전 예제는 숫자 1, 2, 4, 5를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="54237-153">숫자 3을 건너뛰고 루프의 다음 반복을 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="54237-154">`continue`는 현재 반복에 대해서라는 점만 제외하고 `break`와 마찬가지로 루프를 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="54237-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="54237-155">Execution은 루프를 중단하고 중지하는 대신 다음 반복에서 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="54237-156">Return은 기존 범위에서 종료되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="54237-157">이전 예제에서 return은 첫 번째 결과를 출력한 다음 루프에서 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="54237-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="54237-158">결과 문에 대한 자세한 설명은 다음 블로그 게시물 중 하나에서 찾을 수 있습니다. ["PowerShell return 카워드"][].</span><span class="sxs-lookup"><span data-stu-id="54237-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="54237-159">요약</span><span class="sxs-lookup"><span data-stu-id="54237-159">Summary</span></span>

<span data-ttu-id="54237-160">이 장에서는 PowerShell에 존재하는 다양한 유형의 루프에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="54237-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="54237-161">검토</span><span class="sxs-lookup"><span data-stu-id="54237-161">Review</span></span>

1. <span data-ttu-id="54237-162">`ForEach-Object` cmdlet과 foreach 스크립팅 구문의 차이점은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="54237-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="54237-163">Do While 또는 Do Until 루프를 사용하는 대신 While 루프를 사용할 때의 주요 이점은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="54237-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="54237-164">break 문과 continue 문은 어떻게 다른가요?</span><span class="sxs-lookup"><span data-stu-id="54237-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="54237-165">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="54237-165">Recommended Reading</span></span>

- <span data-ttu-id="54237-166">[ForEach-Object][]</span><span class="sxs-lookup"><span data-stu-id="54237-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="54237-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="54237-167">[about_ForEach][]</span></span>
- <span data-ttu-id="54237-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="54237-168">[about_For][]</span></span>
- <span data-ttu-id="54237-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="54237-169">[about_Do][]</span></span>
- <span data-ttu-id="54237-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="54237-170">[about_While][]</span></span>
- <span data-ttu-id="54237-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="54237-171">[about_Break][]</span></span>
- <span data-ttu-id="54237-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="54237-172">[about_Continue][]</span></span>
- <span data-ttu-id="54237-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="54237-173">[about_Return][]</span></span>

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
["PowerShell return 카워드"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
