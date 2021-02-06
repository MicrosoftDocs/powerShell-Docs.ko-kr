---
description: 함수, 스크립트 또는 스크립트 블록일 수 있는 현재 범위를 종료합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599611"
---
# <a name="about-return"></a><span data-ttu-id="b1562-103">반환 정보</span><span class="sxs-lookup"><span data-stu-id="b1562-103">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="b1562-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b1562-104">Short description</span></span>

<span data-ttu-id="b1562-105">함수, 스크립트 또는 스크립트 블록일 수 있는 현재 범위를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-105">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="b1562-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-106">Long description</span></span>

<span data-ttu-id="b1562-107">`return`키워드는 함수, 스크립트 또는 스크립트 블록을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-107">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="b1562-108">특정 지점에서 범위를 종료 하거나, 값을 반환 하거나, 범위의 끝에 도달 했음을 나타내는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-108">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="b1562-109">C 또는 C와 같은 언어에 익숙한 사용자는 \# 키워드를 사용 하 여 `return` 범위를 명시적으로 유지 하는 논리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-109">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="b1562-110">PowerShell에서 Return 키워드를 포함 하는 문이 없어도 각 문의 결과가 output으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-110">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="b1562-111">C 또는 C와 같은 언어는 \# 키워드에 지정 된 값 또는 값만 반환 `return` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-111">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="b1562-112">PowerShell 5.0부터 PowerShell은 정식 구문을 사용 하 여 클래스를 정의 하기 위한 언어를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-112">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="b1562-113">PowerShell 클래스의 컨텍스트에서는 문을 사용 하 여 지정 하는 것을 제외 하 고는 메서드에서 아무것도 출력 하지 않습니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="b1562-113">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="b1562-114">[About_Classes](about_Classes.md)에서 PowerShell 클래스에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-114">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="b1562-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1562-115">Syntax</span></span>

<span data-ttu-id="b1562-116">키워드의 구문은 다음과 같습니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="b1562-116">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="b1562-117">`return`키워드는 단독으로 표시 되거나 다음과 같이 값 또는 식 뒤에 올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-117">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="b1562-118">예</span><span class="sxs-lookup"><span data-stu-id="b1562-118">Examples</span></span>

<span data-ttu-id="b1562-119">다음 예제에서는 키워드를 사용 하 여 `return` 조건이 충족 되는 경우 특정 지점에서 함수를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-119">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="b1562-120">Return 문이 실행 되기 전에 return 문이 종료 되므로 홀수는 곱할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-120">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

<span data-ttu-id="b1562-121">PowerShell에서 `return` 키워드가 사용 되지 않은 경우에도 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-121">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="b1562-122">각 문의 결과가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-122">The results of each statement are returned.</span></span> <span data-ttu-id="b1562-123">예를 들어 다음 문은 변수 값을 반환 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="b1562-123">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="b1562-124">다음 문은의 값도 반환 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="b1562-124">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="b1562-125">다음 예에는 함수에서 계산을 수행 하 고 있음을 사용자에 게 알리기 위한 문이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-125">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="b1562-126">"잠시 기다려 주십시오.</span><span class="sxs-lookup"><span data-stu-id="b1562-126">The "Please wait.</span></span> <span data-ttu-id="b1562-127">계산 작업 중 ... " 문자열이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-127">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="b1562-128">대신, `$a` 다음 예제와 같이 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-128">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="b1562-129">정보 문자열과 계산 결과가 모두 함수에 의해 반환 되 고 변수에 할당 됩니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="b1562-129">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="b1562-130">PowerShell 5.0부터 함수 내에 메시지를 표시 하려는 경우 스트림을 사용할 수 있습니다 `Information` .</span><span class="sxs-lookup"><span data-stu-id="b1562-130">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="b1562-131">아래 코드에서는 Continue를 사용 하 여 cmdlet을 사용 하는 위의 예를 수정 `Write-Information` `InformationAction` 합니다. </span><span class="sxs-lookup"><span data-stu-id="b1562-131">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue**.</span></span>

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="b1562-132">반환 값 및 파이프라인</span><span class="sxs-lookup"><span data-stu-id="b1562-132">Return values and the Pipeline</span></span>

<span data-ttu-id="b1562-133">스크립트 블록이 나 함수에서 컬렉션을 반환 하면 PowerShell에서 자동으로 멤버를 롤링 하지 않으며 파이프라인을 통해 한 번에 하나씩 해당 멤버를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-133">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="b1562-134">이는 PowerShell의 일회성 처리로 인 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-134">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="b1562-135">자세한 내용은 [about_pipelines](about_pipelines.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1562-135">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="b1562-136">이 개념은 숫자의 배열을 반환 하는 다음 샘플 함수에서 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-136">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="b1562-137">함수의 출력은 파이프라인의 개체 수를 계산 하는 cmdlet으로 파이프 됩니다 `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="b1562-137">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="b1562-138">스크립트 블록이 나 함수에서 컬렉션을 단일 개체로 반환 하도록 강제 하려면 다음 두 가지 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-138">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="b1562-139">단항 배열 식</span><span class="sxs-lookup"><span data-stu-id="b1562-139">Unary array expression</span></span>

  <span data-ttu-id="b1562-140">단항 식을 활용 하 여 다음 예제에 나와 있는 것 처럼 반환 값을 파이프라인에서 단일 개체로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-140">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- <span data-ttu-id="b1562-141">`Write-Output`**Noenumerate** 매개 변수 사용.</span><span class="sxs-lookup"><span data-stu-id="b1562-141">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="b1562-142">`Write-Output` **Noenumerate** 매개 변수와 함께 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1562-142">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="b1562-143">아래 예제에서는 cmdlet을 사용 하 여 `Measure-Object` 키워드를 통해 샘플 함수에서 파이프라인으로 전송 된 개체 수를 계산 합니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="b1562-143">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a><span data-ttu-id="b1562-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1562-144">See also</span></span>

[<span data-ttu-id="b1562-145">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="b1562-145">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="b1562-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="b1562-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="b1562-147">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b1562-147">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="b1562-148">about_Classes</span><span class="sxs-lookup"><span data-stu-id="b1562-148">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="b1562-149">Write-Information</span><span class="sxs-lookup"><span data-stu-id="b1562-149">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="b1562-150">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="b1562-150">about_Script_Blocks</span></span>](about_Script_Blocks.md)

