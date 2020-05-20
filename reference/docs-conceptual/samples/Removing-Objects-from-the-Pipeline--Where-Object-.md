---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 파이프라인에서 개체 제거(Where Object)
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737188"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="fe20d-103">파이프라인에서 개체 제거(Where-Object)</span><span class="sxs-lookup"><span data-stu-id="fe20d-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="fe20d-104">일반적으로 PowerShell은 필요한 것보다 많은 개체를 만들어 파이프라인에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-104">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="fe20d-105">`Format-*` cmdlet을 사용하면 표시할 특정 개체의 속성을 지정할 수 있지만 전체 개체를 표시하지 않는 문제에는 도움이 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-105">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="fe20d-106">파이프라인 끝에 도달하기 전에 개체를 필터링하여 처음 만들어진 개체의 하위 집합에 대해서만 특정 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="fe20d-107">PowerShell에는 파이프라인에 있는 각 개체를 테스트하고 특정 테스트 조건을 만족하는 개체만 파이프라인을 통해 전달할 수 있는 `Where-Object` cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-107">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="fe20d-108">테스트를 통과하지 못한 개체는 파이프라인에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="fe20d-109">테스트 조건은 **FilterScript** 매개 변수의 값으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-109">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="fe20d-110">Where-Object를 사용하여 간단한 테스트 수행</span><span class="sxs-lookup"><span data-stu-id="fe20d-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="fe20d-111">**FilterScript**의 값은 true 또는 false로 계산되는 하나의 *스크립트 블록*(하나 이상의 PowerShell 명령이 중괄호(`{}`)로 묶여 있음)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-111">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="fe20d-112">이러한 스크립트 블록은 매우 간단할 수 있지만 비교 연산자와 같은 다른 PowerShell 개념을 알고 있어야 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-112">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="fe20d-113">비교 연산자는 자신을 중심으로 양쪽에 표시되는 두 항목을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="fe20d-114">비교 연산자의 이름은 하이픈 문자(`-`)로 시작되고 뒤에 이름이 옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-114">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="fe20d-115">기본 비교 연산자는 거의 모든 유형의 개체에서 작동하지만</span><span class="sxs-lookup"><span data-stu-id="fe20d-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="fe20d-116">고급 비교 연산자는 텍스트나 배열에서만 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="fe20d-117">기본적으로 PowerShell 비교 연산자는 텍스트를 비교할 때 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-117">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="fe20d-118">구문 오류가 발생할 수 있으므로 `<`,`>`, `=` 등의 기호는 비교 연산자로 사용할 수 없고</span><span class="sxs-lookup"><span data-stu-id="fe20d-118">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="fe20d-119">문자만 비교 연산자로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="fe20d-120">다음 표에는 기본 비교 연산자가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-120">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="fe20d-121">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="fe20d-121">Comparison Operator</span></span> |                  <span data-ttu-id="fe20d-122">의미</span><span class="sxs-lookup"><span data-stu-id="fe20d-122">Meaning</span></span>                   |    <span data-ttu-id="fe20d-123">예제(true 반환)</span><span class="sxs-lookup"><span data-stu-id="fe20d-123">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="fe20d-124">-eq</span><span class="sxs-lookup"><span data-stu-id="fe20d-124">-eq</span></span>                 | <span data-ttu-id="fe20d-125">같음</span><span class="sxs-lookup"><span data-stu-id="fe20d-125">is equal to</span></span>                                | <span data-ttu-id="fe20d-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="fe20d-126">1 -eq 1</span></span>                      |
| <span data-ttu-id="fe20d-127">-ne</span><span class="sxs-lookup"><span data-stu-id="fe20d-127">-ne</span></span>                 | <span data-ttu-id="fe20d-128">같지 않음</span><span class="sxs-lookup"><span data-stu-id="fe20d-128">Is not equal to</span></span>                            | <span data-ttu-id="fe20d-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="fe20d-129">1 -ne 2</span></span>                      |
| <span data-ttu-id="fe20d-130">-lt</span><span class="sxs-lookup"><span data-stu-id="fe20d-130">-lt</span></span>                 | <span data-ttu-id="fe20d-131">보다 작음</span><span class="sxs-lookup"><span data-stu-id="fe20d-131">Is less than</span></span>                               | <span data-ttu-id="fe20d-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="fe20d-132">1 -lt 2</span></span>                      |
| <span data-ttu-id="fe20d-133">-le</span><span class="sxs-lookup"><span data-stu-id="fe20d-133">-le</span></span>                 | <span data-ttu-id="fe20d-134">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="fe20d-134">Is less than or equal to</span></span>                   | <span data-ttu-id="fe20d-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="fe20d-135">1 -le 2</span></span>                      |
| <span data-ttu-id="fe20d-136">-gt</span><span class="sxs-lookup"><span data-stu-id="fe20d-136">-gt</span></span>                 | <span data-ttu-id="fe20d-137">보다 큼</span><span class="sxs-lookup"><span data-stu-id="fe20d-137">Is greater than</span></span>                            | <span data-ttu-id="fe20d-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="fe20d-138">2 -gt 1</span></span>                      |
| <span data-ttu-id="fe20d-139">-ge</span><span class="sxs-lookup"><span data-stu-id="fe20d-139">-ge</span></span>                 | <span data-ttu-id="fe20d-140">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="fe20d-140">Is greater than or equal to</span></span>                | <span data-ttu-id="fe20d-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="fe20d-141">2 -ge 1</span></span>                      |
| <span data-ttu-id="fe20d-142">-like</span><span class="sxs-lookup"><span data-stu-id="fe20d-142">-like</span></span>               | <span data-ttu-id="fe20d-143">비슷함(텍스트의 와일드카드 비교)</span><span class="sxs-lookup"><span data-stu-id="fe20d-143">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="fe20d-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="fe20d-144">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="fe20d-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="fe20d-145">-notlike</span></span>            | <span data-ttu-id="fe20d-146">비슷하지 않음(텍스트의 와일드카드 비교)</span><span class="sxs-lookup"><span data-stu-id="fe20d-146">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="fe20d-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="fe20d-147">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="fe20d-148">-contains</span><span class="sxs-lookup"><span data-stu-id="fe20d-148">-contains</span></span>           | <span data-ttu-id="fe20d-149">포함</span><span class="sxs-lookup"><span data-stu-id="fe20d-149">Contains</span></span>                                   | <span data-ttu-id="fe20d-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="fe20d-150">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="fe20d-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="fe20d-151">-notcontains</span></span>        | <span data-ttu-id="fe20d-152">포함하지 않음</span><span class="sxs-lookup"><span data-stu-id="fe20d-152">Does not contain</span></span>                           | <span data-ttu-id="fe20d-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="fe20d-153">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="fe20d-154">`Where-Object` 스크립트 블록은 특수 변수 `$_`를 사용하여 파이프라인에 있는 현재 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-154">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="fe20d-155">다음은 이러한 동작을 보여 주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-155">Here is an example of how it works.</span></span> <span data-ttu-id="fe20d-156">일련의 숫자 중에서 3보다 작은 숫자만 반환하려면 다음과 같이 `Where-Object`를 사용하여 숫자를 필터링하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="fe20d-157">개체 속성을 기반으로 필터링</span><span class="sxs-lookup"><span data-stu-id="fe20d-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="fe20d-158">`$_`가 현재 파이프라인 개체를 참조하므로 테스트를 위해 이 개체의 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="fe20d-159">예를 들어 WMI에서 **Win32_SystemDriver** 클래스를 살펴보면</span><span class="sxs-lookup"><span data-stu-id="fe20d-159">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="fe20d-160">특정 시스템에 수백 개의 시스템 드라이버가 있을 수 있지만 현재 실행 중인 드라이버와 같은 특정 시스템 드라이버 집합만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="fe20d-161">**Win32_SystemDriver** 클래스의 경우 관련 속성이 **State**입니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-161">For the **Win32_SystemDriver** class the relevant property is **State**.</span></span> <span data-ttu-id="fe20d-162">다음과 같이 입력하면 시스템 드라이버를 필터링하여 실행 중인 드라이버만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="fe20d-163">그러나 이 목록에는 아직도 필요한 것보다 많은 항목이 포함되어 있으므로</span><span class="sxs-lookup"><span data-stu-id="fe20d-163">This still produces a long list.</span></span> <span data-ttu-id="fe20d-164">다음과 같이 **StartMode** 값도 테스트하여 자동으로 시작되도록 설정된 드라이버만 선택하도록 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-164">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="fe20d-165">드라이버가 실행 중이라는 것을 앞에서 확인했기 때문에 이 목록에는 아직도 불필요한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="fe20d-166">사실 이 시점에서 필요한 정보는 이름과 표시 이름뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="fe20d-167">다음 명령은 목록에 이러한 두 속성만 포함하여 출력을 훨씬 더 간단하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="fe20d-168">위의 명령에는 두 개의 `Where-Object` 요소가 있지만 다음과 같이`-and` 논리 연산자를 사용하면 단일 `Where-Object` 요소로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-168">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="fe20d-169">다음 표에는 기본 논리 연산자가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe20d-169">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="fe20d-170">논리 연산자</span><span class="sxs-lookup"><span data-stu-id="fe20d-170">Logical Operator</span></span> |                 <span data-ttu-id="fe20d-171">의미</span><span class="sxs-lookup"><span data-stu-id="fe20d-171">Meaning</span></span>                  |  <span data-ttu-id="fe20d-172">예제(true 반환)</span><span class="sxs-lookup"><span data-stu-id="fe20d-172">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="fe20d-173">-and</span><span class="sxs-lookup"><span data-stu-id="fe20d-173">-and</span></span>             | <span data-ttu-id="fe20d-174">논리곱(둘 다 true일 경우 true임)</span><span class="sxs-lookup"><span data-stu-id="fe20d-174">Logical and; true if both sides are true</span></span> | <span data-ttu-id="fe20d-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fe20d-175">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="fe20d-176">-or</span><span class="sxs-lookup"><span data-stu-id="fe20d-176">-or</span></span>              | <span data-ttu-id="fe20d-177">논리합(둘 중 하나만 true여도 true임)</span><span class="sxs-lookup"><span data-stu-id="fe20d-177">Logical or; true if either side is true</span></span>  | <span data-ttu-id="fe20d-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fe20d-178">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="fe20d-179">-not</span><span class="sxs-lookup"><span data-stu-id="fe20d-179">-not</span></span>             | <span data-ttu-id="fe20d-180">논리 부정(true와 false를 반대로 바꿈)</span><span class="sxs-lookup"><span data-stu-id="fe20d-180">Logical not; reverses true and false</span></span>     | <span data-ttu-id="fe20d-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fe20d-181">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="fe20d-182">논리 부정(true와 false를 반대로 바꿈)</span><span class="sxs-lookup"><span data-stu-id="fe20d-182">Logical not; reverses true and false</span></span>     | <span data-ttu-id="fe20d-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fe20d-183">\!(1 -eq 2)</span></span>              |
