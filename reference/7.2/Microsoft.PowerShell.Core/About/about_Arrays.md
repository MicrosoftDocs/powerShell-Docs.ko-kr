---
description: 항목 컬렉션을 저장 하도록 디자인 된 데이터 구조인 배열에 대해 설명 합니다.
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_arrays
ms.openlocfilehash: 2e7cf9c8f7d4e6f1d5bc66310f56d3de9461e592
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601464"
---
# <a name="about-arrays"></a><span data-ttu-id="364ec-103">배열 정보</span><span class="sxs-lookup"><span data-stu-id="364ec-103">About Arrays</span></span>

## <a name="short-description"></a><span data-ttu-id="364ec-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="364ec-104">Short Description</span></span>
<span data-ttu-id="364ec-105">항목 컬렉션을 저장 하도록 디자인 된 데이터 구조인 배열에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-105">Describes arrays, which are data structures designed to store collections of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="364ec-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="364ec-106">Long Description</span></span>

<span data-ttu-id="364ec-107">배열은 항목 컬렉션을 저장 하도록 디자인 된 데이터 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-107">An array is a data structure that is designed to store a collection of items.</span></span>
<span data-ttu-id="364ec-108">항목은 형식이 나 형식이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-108">The items can be the same type or different types.</span></span>

<span data-ttu-id="364ec-109">Windows PowerShell 3.0부터 0 개 또는 한 개의 개체 컬렉션에 배열의 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-109">Beginning in Windows PowerShell 3.0, a collection of zero or one object has some properties of arrays.</span></span>

## <a name="creating-and-initializing-an-array"></a><span data-ttu-id="364ec-110">배열 만들기 및 초기화</span><span class="sxs-lookup"><span data-stu-id="364ec-110">Creating and initializing an array</span></span>

<span data-ttu-id="364ec-111">배열을 만들고 초기화 하려면 변수에 여러 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-111">To create and initialize an array, assign multiple values to a variable.</span></span> <span data-ttu-id="364ec-112">배열에 저장 된 값은 쉼표로 구분 되며 대입 연산자 ()로 변수 이름과 구분 됩니다 `=` .</span><span class="sxs-lookup"><span data-stu-id="364ec-112">The values stored in the array are delimited with a comma and separated from the variable name by the assignment operator (`=`).</span></span>

<span data-ttu-id="364ec-113">예를 `$A` 들어 7 개의 숫자 (int) 값 22, 5, 10, 8, 12, 9, 80를 포함 하는 라는 배열을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-113">For example, to create an array named `$A` that contains the seven numeric (int) values of 22, 5, 10, 8, 12, 9, and 80, type:</span></span>

```powershell
$A = 22,5,10,8,12,9,80
```

<span data-ttu-id="364ec-114">쉼표는 단일 항목 앞에 쉼표를 추가 하 여 단일 항목 배열을 초기화 하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-114">The comma can also be used to initialize a single item array by placing the comma before the single item.</span></span>

<span data-ttu-id="364ec-115">예를 `$B` 들어 단일 값 7을 포함 하는 라는 단일 항목 배열을 만들려면 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-115">For example, to create a single item array named `$B` containing the single value of 7, type:</span></span>

```powershell
$B = ,7
```

<span data-ttu-id="364ec-116">범위 연산자 ()를 사용 하 여 배열을 만들고 초기화할 수도 있습니다 `..` .</span><span class="sxs-lookup"><span data-stu-id="364ec-116">You can also create and initialize an array by using the range operator (`..`).</span></span>
<span data-ttu-id="364ec-117">다음 예에서는 값 5 ~ 8을 포함 하는 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-117">The following example creates an array containing the values 5 through 8.</span></span>

```powershell
$C = 5..8
```

<span data-ttu-id="364ec-118">따라서에는 `$C` 5, 6, 7 및 8의 네 가지 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-118">As a result, `$C` contains four values: 5, 6, 7, and 8.</span></span>

<span data-ttu-id="364ec-119">데이터 형식을 지정 하지 않으면 PowerShell에서 각 배열을 개체 배열 (**system.object []**)로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-119">When no data type is specified, PowerShell creates each array as an object array (**System.Object[]**).</span></span> <span data-ttu-id="364ec-120">배열의 데이터 형식을 확인 하려면 **GetType ()** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-120">To determine the data type of an array, use the **GetType()** method.</span></span> <span data-ttu-id="364ec-121">예를 들어 배열의 데이터 형식을 확인 하려면 다음을 `$A` 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-121">For example, to determine the data type of the `$A` array, type:</span></span>

```powershell
$A.GetType()
```

<span data-ttu-id="364ec-122">특정 형식의 값만 포함할 수 있는 강력한 형식의 배열을 만들려면 변수를 **문자열 []**, **long []** 또는 **int32 []** 와 같은 배열 형식으로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-122">To create a strongly typed array, that is, an array that can contain only values of a particular type, cast the variable as an array type, such as **string[]**, **long[]**, or **int32[]**.</span></span> <span data-ttu-id="364ec-123">배열을 캐스팅 하려면 변수 이름 앞에 대괄호로 묶은 배열 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-123">To cast an array, precede the variable name with an array type enclosed in brackets.</span></span> <span data-ttu-id="364ec-124">예를 `$ia` 들어 4 개의 정수 (1500, 2230, 3350 및 4000)가 포함 된 32 비트 정수 배열을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-124">For example, to create a 32-bit integer array named `$ia` containing four integers (1500, 2230, 3350, and 4000), type:</span></span>

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

<span data-ttu-id="364ec-125">따라서 `$ia` 배열에 정수만 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-125">As a result, the `$ia` array can contain only integers.</span></span>

<span data-ttu-id="364ec-126">Microsoft .NET 프레임 워크에서 지원 되는 형식으로 캐스팅 된 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-126">You can create arrays that are cast to any supported type in the Microsoft .NET Framework.</span></span> <span data-ttu-id="364ec-127">예를 들어 `Get-Process` 프로세스를 나타내기 위해 검색 하는 개체는 **System.web. 프로세스** 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-127">For example, the objects that `Get-Process` retrieves to represent processes are of the **System.Diagnostics.Process** type.</span></span> <span data-ttu-id="364ec-128">프로세스 개체의 강력한 형식의 배열을 만들려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-128">To create a strongly typed array of process objects, enter the following command:</span></span>

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a><span data-ttu-id="364ec-129">배열 하위 식 연산자</span><span class="sxs-lookup"><span data-stu-id="364ec-129">The array sub-expression operator</span></span>

<span data-ttu-id="364ec-130">배열 하위 식 연산자는 내부에 있는 문에서 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-130">The array sub-expression operator creates an array from the statements inside it.</span></span> <span data-ttu-id="364ec-131">연산자 내의 문이 생성 하는 것과 관계 없이 연산자는 배열에이를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-131">Whatever the statement inside the operator produces, the operator will place it in an array.</span></span> <span data-ttu-id="364ec-132">개체가 0 개 또는 1 개 있는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-132">Even if there is zero or one object.</span></span>

<span data-ttu-id="364ec-133">배열 연산자의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-133">The syntax of the array operator is as follows:</span></span>

```syntax
@( ... )
```

<span data-ttu-id="364ec-134">배열 연산자를 사용 하 여 0 개 또는 한 개의 개체로 이루어진 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-134">You can use the array operator to create an array of zero or one object.</span></span> <span data-ttu-id="364ec-135">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="364ec-135">For example:</span></span>

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

<span data-ttu-id="364ec-136">Array 연산자는 개체를 가져올 때 스크립트에 유용 하지만, 얻을 수 있는 개체의 수를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-136">The array operator is useful in scripts when you are getting objects, but do not know how many objects you get.</span></span> <span data-ttu-id="364ec-137">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="364ec-137">For example:</span></span>

```powershell
$p = @(Get-Process Notepad)
```

<span data-ttu-id="364ec-138">배열 하위 식 연산자에 대 한 자세한 내용은 [about_Operators](about_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="364ec-138">For more information about the array sub-expression operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="accessing-and-using-array-elements"></a><span data-ttu-id="364ec-139">배열 요소 액세스 및 사용</span><span class="sxs-lookup"><span data-stu-id="364ec-139">Accessing and using array elements</span></span>

### <a name="reading-an-array"></a><span data-ttu-id="364ec-140">배열 읽기</span><span class="sxs-lookup"><span data-stu-id="364ec-140">Reading an array</span></span>

<span data-ttu-id="364ec-141">변수 이름을 사용 하 여 배열을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-141">You can refer to an array by using its variable name.</span></span> <span data-ttu-id="364ec-142">배열의 모든 요소를 표시 하려면 배열 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-142">To display all the elements in the array, type the array name.</span></span> <span data-ttu-id="364ec-143">예를 들어, `$a` 가 9까지 정수 0, 1, 2를 포함 하는 배열인 경우 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-143">For example, assuming `$a` is an array containing integers 0, 1, 2, until 9; typing:</span></span>

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="364ec-144">0 위치에서 시작 하 여 인덱스를 사용 하 여 배열의 요소를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-144">You can refer to the elements in an array by using an index, beginning at position 0.</span></span> <span data-ttu-id="364ec-145">인덱스 번호를 대괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-145">Enclose the index number in brackets.</span></span> <span data-ttu-id="364ec-146">예를 들어 배열의 첫 번째 요소를 표시 하려면 `$a` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-146">For example, to display the first element in the `$a` array, type:</span></span>

```powershell
$a[0]
```

```Output
0
```

<span data-ttu-id="364ec-147">배열의 세 번째 요소를 표시 하려면 `$a` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-147">To display the third element in the `$a` array, type:</span></span>

```powershell
$a[2]
```

```Output
2
```

<span data-ttu-id="364ec-148">인덱스에 대해 범위 연산자를 사용 하 여 배열의 일부를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-148">You can retrieve part of the array using a range operator for the index.</span></span> <span data-ttu-id="364ec-149">예를 들어 배열의 두 번째 요소와 다섯 번째 요소를 검색 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-149">For example, to retrieve the second to fifth elements of the array, you would type:</span></span>

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

<span data-ttu-id="364ec-150">배열의 끝부터 음수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-150">Negative numbers count from the end of the array.</span></span> <span data-ttu-id="364ec-151">예를 들어 "-1"은 배열의 마지막 요소를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-151">For example, "-1" refers to the last element of the array.</span></span> <span data-ttu-id="364ec-152">배열의 마지막 세 요소를 표시 하려면 인덱스 오름차순에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-152">To display the last three elements of the array, in index ascending order, type:</span></span>

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

<span data-ttu-id="364ec-153">음수 인덱스를 내림차순으로 입력 하면 출력이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-153">If you type negative indexes in descending order, your output changes.</span></span>

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

<span data-ttu-id="364ec-154">그러나이 표기법을 사용할 때는 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-154">However, be cautious when using this notation.</span></span> <span data-ttu-id="364ec-155">표기법은 끝 경계에서 배열의 시작 부분으로 순환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-155">The notation cycles from the end boundary to the beginning of the array.</span></span>

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

<span data-ttu-id="364ec-156">또한 일반적인 실수 중 하나는 `$a[0..-2]` 마지막 요소를 제외 하 고 배열의 모든 요소를 참조 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-156">Also, one common mistake is to assume `$a[0..-2]` refers to all the elements of the array, except for the last one.</span></span> <span data-ttu-id="364ec-157">배열의 첫 번째, 마지막 및 초에서 마지막 요소를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-157">It refers to the first, last, and second-to-last elements in the array.</span></span>

<span data-ttu-id="364ec-158">더하기 연산자 ()를 사용 `+` 하 여 범위를 배열의 요소 목록과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-158">You can use the plus operator (`+`) to combine a ranges with a list of elements in an array.</span></span> <span data-ttu-id="364ec-159">예를 들어 인덱스 위치 0, 2 및 4-6에 요소를 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-159">For example, to display the elements at index positions 0, 2, and 4 through 6, type:</span></span>

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

<span data-ttu-id="364ec-160">또한 여러 범위 및 개별 요소를 나열 하려면 더하기 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-160">Also, to list multiple ranges and individual elements you can use the plus operator.</span></span> <span data-ttu-id="364ec-161">예를 들어 0 ~ 2, 4 ~ 6 개의 요소를 나열 하 고 여덟 번째 위치에 요소를 나열 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-161">For example, to list elements zero to two, four to six, and the element at eighth positional type:</span></span>

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a><span data-ttu-id="364ec-162">배열 요소 반복</span><span class="sxs-lookup"><span data-stu-id="364ec-162">Iterations over array elements</span></span>

<span data-ttu-id="364ec-163">ForEach, For, While 루프와 같은 루프 구문을 사용 하 여 배열의 요소를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-163">You can also use looping constructs, such as ForEach, For, and While loops, to refer to the elements in an array.</span></span> <span data-ttu-id="364ec-164">예를 들어 ForEach 루프를 사용 하 여 배열의 요소를 표시 하려면 `$a` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-164">For example, to use a ForEach loop to display the elements in the `$a` array, type:</span></span>

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="364ec-165">Foreach 루프는 배열을 반복 하 고 배열의 끝에 도달할 때까지 배열의 각 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-165">The Foreach loop iterates through the array and returns each value in the array until reaching the end of the array.</span></span>

<span data-ttu-id="364ec-166">For 루프는 배열의 요소를 검사 하는 동안 카운터를 증가 시키는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-166">The For loop is useful when you are incrementing counters while examining the elements in an array.</span></span> <span data-ttu-id="364ec-167">예를 들어 For 루프를 사용 하 여 배열의 다른 모든 값을 반환 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-167">For example, to use a For loop to return every other value in an array, type:</span></span>

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

<span data-ttu-id="364ec-168">While 루프를 사용 하 여 정의 된 조건이 더 이상 true가 될 때까지 배열의 요소를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-168">You can use a While loop to display the elements in an array until a defined condition is no longer true.</span></span> <span data-ttu-id="364ec-169">예를 들어 배열 `$a` 인덱스가 4 보다 작은 동안 배열의 요소를 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-169">For example, to display the elements in the `$a` array while the array index is less than 4, type:</span></span>

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a><span data-ttu-id="364ec-170">배열의 속성</span><span class="sxs-lookup"><span data-stu-id="364ec-170">Properties of arrays</span></span>

### <a name="count-or-length-or-longlength"></a><span data-ttu-id="364ec-171">개수 또는 길이 또는 고 길이</span><span class="sxs-lookup"><span data-stu-id="364ec-171">Count or Length or LongLength</span></span>

<span data-ttu-id="364ec-172">배열에 있는 항목 수를 확인 하려면 `Length` 속성 또는 해당 별칭을 사용 `Count` 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-172">To determine how many items are in an array, use the `Length` property or its `Count` alias.</span></span> <span data-ttu-id="364ec-173">`Longlength` 배열에 2147483647 개 이상의 요소가 포함 된 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-173">`Longlength` is useful if the array contains more than 2,147,483,647 elements.</span></span>

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a><span data-ttu-id="364ec-174">순위</span><span class="sxs-lookup"><span data-stu-id="364ec-174">Rank</span></span>

<span data-ttu-id="364ec-175">배열의 차원 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-175">Returns the number of dimensions in the array.</span></span> <span data-ttu-id="364ec-176">PowerShell의 대부분 배열에는 하나의 차원만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-176">Most arrays in PowerShell have one dimension, only.</span></span> <span data-ttu-id="364ec-177">다차원 배열을 작성 한다고 생각 하는 경우에도 다음 예제와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-177">Even when you think you are building a multidimensional array; like the following example:</span></span>

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

<span data-ttu-id="364ec-178">다음 예제에서는 .Net Framework를 사용 하 여 진정한 다차원 배열을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-178">The following example shows how to create a truly multidimensional array using the .Net Framework.</span></span>

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a><span data-ttu-id="364ec-179">배열의 메서드</span><span class="sxs-lookup"><span data-stu-id="364ec-179">Methods of arrays</span></span>

### <a name="clear"></a><span data-ttu-id="364ec-180">지우기</span><span class="sxs-lookup"><span data-stu-id="364ec-180">Clear</span></span>

<span data-ttu-id="364ec-181">모든 요소 값을 배열의 요소 형식 _기본값으로_ 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-181">Sets all element values to the _default value_ of the array's element type.</span></span>
<span data-ttu-id="364ec-182">Clear () 메서드는 배열의 크기를 다시 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-182">The Clear() method does not reset the size of the array.</span></span>

<span data-ttu-id="364ec-183">다음 예제에서는 `$a` 개체의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-183">In the following example `$a` is an array of objects.</span></span>

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

<span data-ttu-id="364ec-184">이 예제에서 `$intA` 는 정수를 포함 하도록 명시적으로 형식화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-184">In this example, `$intA` is explicitly typed to contain integers.</span></span>

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a><span data-ttu-id="364ec-185">ForEach</span><span class="sxs-lookup"><span data-stu-id="364ec-185">ForEach</span></span>

<span data-ttu-id="364ec-186">를 사용 하 여 배열의 모든 요소를 반복 하 고 배열의 각 요소에 대해 지정 된 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-186">Allows to iterate over all elements in the array and perform a given operation for each element of the array.</span></span>

<span data-ttu-id="364ec-187">ForEach 메서드에는 서로 다른 작업을 수행 하는 여러 오버 로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-187">The ForEach method has several overloads that perform different operations.</span></span>

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a><span data-ttu-id="364ec-188">ForEach (scriptblock 식)</span><span class="sxs-lookup"><span data-stu-id="364ec-188">ForEach(scriptblock expression)</span></span>

#### <a name="foreachscriptblock-expression-object-arguments"></a><span data-ttu-id="364ec-189">ForEach (scriptblock 식, object [] arguments)</span><span class="sxs-lookup"><span data-stu-id="364ec-189">ForEach(scriptblock expression, object[] arguments)</span></span>

<span data-ttu-id="364ec-190">이 메서드는 PowerShell v4에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-190">This method was added in PowerShell v4.</span></span>

> [!NOTE]
> <span data-ttu-id="364ec-191">구문에서는 스크립트 블록을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-191">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="364ec-192">Scriptblock이 유일한 매개 변수인 경우 괄호는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-192">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="364ec-193">또한 메서드와 여는 괄호 또는 중괄호 사이에 공백이 있어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-193">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="364ec-194">다음 예제에서는 foreach 메서드를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-194">The following example shows how use the foreach method.</span></span> <span data-ttu-id="364ec-195">이 경우 배열의 요소에 대 한 제곱 값을 생성 하는 것이 의도입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-195">In this case the intent is to generate the square value of the elements in the array.</span></span>

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

<span data-ttu-id="364ec-196">`-ArgumentList`의 매개 변수와 마찬가지로 `ForEach-Object` `arguments` 매개 변수를 사용 하면 인수 배열을 허용 하도록 구성 된 스크립트 블록에 인수 배열을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-196">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

<span data-ttu-id="364ec-197">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="364ec-197">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

#### <a name="foreachtype-converttotype"></a><span data-ttu-id="364ec-198">ForEach (convertToType 형식)</span><span class="sxs-lookup"><span data-stu-id="364ec-198">ForEach(type convertToType)</span></span>

<span data-ttu-id="364ec-199">`ForEach`메서드를 사용 하 여 요소를 다른 형식으로 빠르게 캐스팅할 수 있습니다. 다음 예제에서는 문자열 날짜 목록을 형식으로 변환 하는 방법을 보여 줍니다 `[DateTime]` .</span><span class="sxs-lookup"><span data-stu-id="364ec-199">The `ForEach` method can be used to swiftly cast the elements to a different type; the following example shows how to convert a list of string dates to `[DateTime]` type.</span></span>

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a><span data-ttu-id="364ec-200">ForEach (문자열 propertyName)</span><span class="sxs-lookup"><span data-stu-id="364ec-200">ForEach(string propertyName)</span></span>

#### <a name="foreachstring-propertyname-object-newvalue"></a><span data-ttu-id="364ec-201">ForEach (string propertyName, object [] newValue)</span><span class="sxs-lookup"><span data-stu-id="364ec-201">ForEach(string propertyName, object[] newValue)</span></span>

<span data-ttu-id="364ec-202">`ForEach`메서드를 사용 하 여 컬렉션의 모든 항목에 대 한 속성 값을 신속 하 게 검색 하거나 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-202">The `ForEach` method can also be used to quickly retrieve, or set property values for every item in the collection.</span></span>

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a><span data-ttu-id="364ec-203">ForEach (string methodName)</span><span class="sxs-lookup"><span data-stu-id="364ec-203">ForEach(string methodName)</span></span>

#### <a name="foreachstring-methodname-object-arguments"></a><span data-ttu-id="364ec-204">ForEach (string methodName, object [] arguments)</span><span class="sxs-lookup"><span data-stu-id="364ec-204">ForEach(string methodName, object[] arguments)</span></span>

<span data-ttu-id="364ec-205">마지막으로 `ForEach` 메서드를 사용 하 여 컬렉션의 모든 항목에 대해 메서드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-205">Lastly, `ForEach` methods can be used to execute a method on every item in the collection.</span></span>

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

<span data-ttu-id="364ec-206">`-ArgumentList`의 매개 변수와 마찬가지로 `ForEach-Object` `arguments` 매개 변수를 사용 하면 인수 배열을 허용 하도록 구성 된 스크립트 블록에 인수 배열을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-206">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

> [!NOTE]
> <span data-ttu-id="364ec-207">Windows PowerShell 3.0에서 시작 하 여 컬렉션의 각 항목에 대 한 속성 검색 및 메서드 실행은 "스칼라 개체 및 컬렉션의 메서드"를 사용 하 여 수행할 수도 있습니다. 여기 [about_methods](about_methods.md)여기에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-207">Starting in Windows PowerShell 3.0 retrieving properties and executing methods for each item in a collection can also be accomplished using "Methods of scalar objects and collections" You can read more about that here [about_methods](about_methods.md).</span></span>

### <a name="where"></a><span data-ttu-id="364ec-208">Where</span><span class="sxs-lookup"><span data-stu-id="364ec-208">Where</span></span>

<span data-ttu-id="364ec-209">배열의 요소를 필터링 하거나 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-209">Allows to filter or select the elements of the array.</span></span> <span data-ttu-id="364ec-210">스크립트는 0 (0), 빈 문자열 `$false` 또는 `$null` 다음에 표시 되는 요소에 대해 다음과 다른 것으로 계산 되어야 합니다. `Where`</span><span class="sxs-lookup"><span data-stu-id="364ec-210">The script must evaluate to anything different than: zero (0), empty string, `$false` or `$null` for the element to show after the `Where`</span></span>

<span data-ttu-id="364ec-211">메서드에 대 한 정의가 하나 있습니다 `Where` .</span><span class="sxs-lookup"><span data-stu-id="364ec-211">There is one definition for the `Where` method.</span></span>

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> <span data-ttu-id="364ec-212">구문에서는 스크립트 블록을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-212">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="364ec-213">Scriptblock이 유일한 매개 변수인 경우 괄호는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-213">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="364ec-214">또한 메서드와 여는 괄호 또는 중괄호 사이에 공백이 있어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-214">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="364ec-215">는 `Expression` 필터링에 필요한 scriptblock 이며 `mode` 선택적 인수는 추가 선택 기능을 허용 하 고 `numberToReturn` 선택적 인수는 필터에서 반환 되는 항목 수를 제한 하는 기능을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-215">The `Expression` is scriptblock that is required for filtering, the `mode` optional argument allows additional selection capabilities, and the `numberToReturn` optional argument allows the ability to limit how many items are returned from the filter.</span></span>

<span data-ttu-id="364ec-216">에 허용 되는 값은 `mode` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-216">The acceptable values for `mode` are:</span></span>

- <span data-ttu-id="364ec-217">Default (0)-모든 항목 반환</span><span class="sxs-lookup"><span data-stu-id="364ec-217">Default (0) - Return all items</span></span>
- <span data-ttu-id="364ec-218">First (1)-첫 번째 항목 반환</span><span class="sxs-lookup"><span data-stu-id="364ec-218">First (1) - Return the first item</span></span>
- <span data-ttu-id="364ec-219">Last (2)-마지막 항목 반환</span><span class="sxs-lookup"><span data-stu-id="364ec-219">Last (2) - Return the last item</span></span>
- <span data-ttu-id="364ec-220">다음까지 건너뛰기 (3)-조건이 true가 될 때까지 항목을 건너뛰고 나머지 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-220">SkipUntil (3) - Skip items until condition is true, the return the remaining items</span></span>
- <span data-ttu-id="364ec-221">Until (4)-조건이 true가 될 때까지 모든 항목 반환</span><span class="sxs-lookup"><span data-stu-id="364ec-221">Until (4) - Return all items until condition is true</span></span>
- <span data-ttu-id="364ec-222">Split (5)-두 요소의 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-222">Split (5) - Return an array of two elements</span></span>
  - <span data-ttu-id="364ec-223">첫 번째 요소는 일치 하는 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-223">The first element contains matching items</span></span>
  - <span data-ttu-id="364ec-224">두 번째 요소는 나머지 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-224">The second element contains the remaining items</span></span>

<span data-ttu-id="364ec-225">다음 예제에서는 배열에서 홀수인 모든 숫자를 선택 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-225">The following example shows how to select all odd numbers from the array.</span></span>

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

<span data-ttu-id="364ec-226">이 예에서는 비어 있지 않은 문자열을 선택 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-226">This example show how to select the strings that are not empty.</span></span>

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a><span data-ttu-id="364ec-227">기본값</span><span class="sxs-lookup"><span data-stu-id="364ec-227">Default</span></span>

<span data-ttu-id="364ec-228">이 `Default` 모드는 scriptblock을 사용 하 여 항목을 필터링 `Expression` 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-228">The `Default` mode filters items using the `Expression` scriptblock.</span></span>

<span data-ttu-id="364ec-229">`numberToReturn`가 제공 되는 경우 반환할 최대 항목 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-229">If a `numberToReturn` is provided, it specifies the maximum number of items to return.</span></span>

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> <span data-ttu-id="364ec-230">`Default`모드와 모드는 모두 `First` 첫 번째 ( `numberToReturn` ) 항목을 반환 하며, 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-230">Both the `Default` mode and `First` mode return the first (`numberToReturn`) items, and can be used interchangeably.</span></span>

#### <a name="last"></a><span data-ttu-id="364ec-231">마지막</span><span class="sxs-lookup"><span data-stu-id="364ec-231">Last</span></span>

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a><span data-ttu-id="364ec-232">다음까지 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="364ec-232">SkipUntil</span></span>

<span data-ttu-id="364ec-233">`SkipUntil`모드는 개체가 스크립트 블록 식 필터를 전달할 때까지 컬렉션의 모든 개체를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-233">The `SkipUntil` mode skips all objects in a collection until an object passes the script block expression filter.</span></span> <span data-ttu-id="364ec-234">그런 다음 나머지 컬렉션 항목을 테스트 하지 않고 **모두** 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-234">It then returns **ALL** remaining collection items without testing them.</span></span> <span data-ttu-id="364ec-235">_하나의 전달 항목만 테스트 됩니다_.</span><span class="sxs-lookup"><span data-stu-id="364ec-235">_Only one passing item is tested_.</span></span>

<span data-ttu-id="364ec-236">즉, 반환 된 컬렉션에는 테스트 되지 않은 _전달_ 및 _전달_ 되지 않는 항목이 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-236">This means the returned collection contains both _passing_ and _non-passing_ items that have NOT been tested.</span></span>

<span data-ttu-id="364ec-237">값을 인수로 전달 하 여 반환 되는 항목 수를 제한할 수 있습니다 `numberToReturn` .</span><span class="sxs-lookup"><span data-stu-id="364ec-237">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a><span data-ttu-id="364ec-238">발생할</span><span class="sxs-lookup"><span data-stu-id="364ec-238">Until</span></span>

<span data-ttu-id="364ec-239">모드는 `Until` 모드를 반전 `SkipUntil` 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-239">The `Until` mode inverts the `SkipUntil` mode.</span></span>  <span data-ttu-id="364ec-240">항목이 스크립트 블록 식을 전달할 때까지 컬렉션의 **모든** 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-240">It returns **ALL** items in a collection until an item passes the script block expression.</span></span> <span data-ttu-id="364ec-241">항목이 scriptblock 식을 _전달_ 하면 `Where` 메서드가 항목 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-241">Once an item _passes_ the scriptblock expression, the `Where` method stops processing items.</span></span>

<span data-ttu-id="364ec-242">즉, 메서드에서 _전달 되지 않는_ 첫 번째 항목 집합을 받습니다 `Where` .</span><span class="sxs-lookup"><span data-stu-id="364ec-242">This means that you receive the first set of _non-passing_ items from the `Where` method.</span></span> <span data-ttu-id="364ec-243">한 항목이 전달 된 _후_ 나머지는 테스트 되거나 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-243">_After_ one item passes, the rest are NOT tested or returned.</span></span>

<span data-ttu-id="364ec-244">값을 인수로 전달 하 여 반환 되는 항목 수를 제한할 수 있습니다 `numberToReturn` .</span><span class="sxs-lookup"><span data-stu-id="364ec-244">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> <span data-ttu-id="364ec-245">및는 모두 `Until` `SkipUntil` 항목의 일괄 처리를 테스트 하지 않고 온-프레미스로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-245">Both `Until` and `SkipUntil` operate under the premise of NOT testing a batch of items.</span></span>
>
> <span data-ttu-id="364ec-246">`Until`첫 번째 패스 **앞** 에 있는 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-246">`Until` returns the items **BEFORE** the first _pass_.</span></span>
>
> <span data-ttu-id="364ec-247">`SkipUntil`첫 번째 전달 항목을 포함 하 여 첫 번째 _패스_ **이후의** 모든 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-247">`SkipUntil` returns all the items **AFTER** the first _pass_, including the first passing item.</span></span>

#### <a name="split"></a><span data-ttu-id="364ec-248">분할</span><span class="sxs-lookup"><span data-stu-id="364ec-248">Split</span></span>

<span data-ttu-id="364ec-249">`Split`모드는 컬렉션 항목을 두 개의 개별 컬렉션으로 분할 하거나 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-249">The `Split` mode splits, or groups collection items into two separate collections.</span></span> <span data-ttu-id="364ec-250">Scriptblock 식을 전달 하는 것과 그렇지 않은 식입니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-250">Those that pass the scriptblock expression, and those that do not.</span></span>

<span data-ttu-id="364ec-251">을 지정 하는 경우 `numberToReturn` 첫 번째 컬렉션에는 지정 된 값을 초과 하지 않고 _전달_ 하는 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-251">If a `numberToReturn` is specified, the first collection, contains the _passing_ items, not to exceed the value specified.</span></span>

<span data-ttu-id="364ec-252">식 필터를 **전달** 하는 개체를 포함 하 여 나머지 개체는 두 번째 컬렉션에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-252">The remaining objects, even those that **PASS** the expression filter, are returned in the second collection.</span></span>

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a><span data-ttu-id="364ec-253">배열의 멤버 가져오기</span><span class="sxs-lookup"><span data-stu-id="364ec-253">Get the members of an array</span></span>

<span data-ttu-id="364ec-254">Length 속성 및 **SetValue** 메서드와 같이 배열의 속성 및 메서드를 가져오려면 Cmdlet의 **InputObject** 매개 변수를 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="364ec-254">To get the properties and methods of an array, such as the Length property and the **SetValue** method, use the **InputObject** parameter of the `Get-Member` cmdlet.</span></span>

<span data-ttu-id="364ec-255">배열을로 파이프 하면 `Get-Member` PowerShell에서 한 번에 하나씩 항목을 보내고, `Get-Member` 배열의 각 항목에 대 한 형식을 반환 합니다 (중복 요소 무시).</span><span class="sxs-lookup"><span data-stu-id="364ec-255">When you pipe an array to `Get-Member`, PowerShell sends the items one at a time and `Get-Member` returns the type of each item in the array (ignoring duplicates).</span></span>

<span data-ttu-id="364ec-256">**InputObject** 매개 변수를 사용 하는 경우는 `Get-Member` 배열의 멤버를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-256">When you use the **InputObject** parameter, `Get-Member` returns the members of the array.</span></span>

<span data-ttu-id="364ec-257">예를 들어 다음 명령은 배열 변수의 멤버를 가져옵니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="364ec-257">For example, the following command gets the members of the `$a` array variable.</span></span>

```powershell
Get-Member -InputObject $a
```

<span data-ttu-id="364ec-258">Cmdlet으로 파이프 되는 값 앞에 쉼표 (,)를 입력 하 여 배열의 멤버를 가져올 수도 있습니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="364ec-258">You can also get the members of an array by typing a comma (,) before the value that is piped to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="364ec-259">쉼표를 사용 하면 배열이 배열 배열의 두 번째 항목으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-259">The comma makes the array the second item in an array of arrays.</span></span> <span data-ttu-id="364ec-260">PowerShell은 한 번에 하나씩 배열을 파이프 하 고 `Get-Member` 배열의 멤버를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-260">PowerShell pipes the arrays one at a time and `Get-Member` returns the members of the array.</span></span> <span data-ttu-id="364ec-261">다음 두 예제와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-261">Like the next two examples.</span></span>

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a><span data-ttu-id="364ec-262">배열 조작</span><span class="sxs-lookup"><span data-stu-id="364ec-262">Manipulating an array</span></span>

<span data-ttu-id="364ec-263">배열의 요소를 변경 하 고, 배열에 요소를 추가 하 고, 두 배열의 값을 세 번째 배열로 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-263">You can change the elements in an array, add an element to an array, and combine the values from two arrays into a third array.</span></span>

<span data-ttu-id="364ec-264">배열의 특정 요소에 대 한 값을 변경 하려면 변경할 요소의 배열 이름과 인덱스를 지정한 다음 할당 연산자 ()를 사용 `=` 하 여 요소에 대 한 새 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-264">To change the value of a particular element in an array, specify the array name and the index of the element that you want to change, and then use the assignment operator (`=`) to specify a new value for the element.</span></span> <span data-ttu-id="364ec-265">예를 들어 배열의 두 번째 항목 `$a` (인덱스 위치 1) 값을 10으로 변경 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-265">For example, to change the value of the second item in the `$a` array (index position 1) to 10, type:</span></span>

```powershell
$a[1] = 10
```

<span data-ttu-id="364ec-266">배열의 **SetValue** 메서드를 사용 하 여 값을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-266">You can also use the **SetValue** method of an array to change a value.</span></span> <span data-ttu-id="364ec-267">다음 예에서는 배열의 두 번째 값 (인덱스 위치 1) `$a` 을 500로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-267">The following example changes the second value (index position 1) of the `$a` array to 500:</span></span>

```powershell
$a.SetValue(500,1)
```

<span data-ttu-id="364ec-268">연산자를 사용 `+=` 하 여 요소를 배열에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-268">You can use the `+=` operator to add an element to an array.</span></span> <span data-ttu-id="364ec-269">다음 예제에서는 배열에 요소를 추가 하는 방법을 보여 줍니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="364ec-269">The following example shows how to add an element to the `$a` array.</span></span>

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> <span data-ttu-id="364ec-270">연산자를 사용 하는 경우 `+=` PowerShell은 실제로 원래 배열의 값과 추가 된 값을 사용 하 여 새 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-270">When you use the `+=` operator, PowerShell actually creates a new array with the values of the original array and the added value.</span></span> <span data-ttu-id="364ec-271">이로 인해 작업이 여러 번 반복 되거나 배열의 크기가 너무 큰 경우 성능 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-271">This might cause performance issues if the operation is repeated several times or the size of the array is too big.</span></span>

<span data-ttu-id="364ec-272">배열에서 요소를 삭제 하는 것은 쉽지 않지만 기존 배열의 선택한 요소만 포함 하는 새 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-272">It is not easy to delete elements from an array, but you can create a new array that contains only selected elements of an existing array.</span></span> <span data-ttu-id="364ec-273">예를 들어 `$t` 인덱스 위치 2의 값을 제외 하 고 배열의 모든 요소가 포함 된 배열을 만들려면 `$a` 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-273">For example, to create the `$t` array with all the elements in the `$a` array except for the value at index position 2, type:</span></span>

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

<span data-ttu-id="364ec-274">두 배열을 단일 배열로 결합 하려면 더하기 연산자 ()를 사용 `+` 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-274">To combine two arrays into a single array, use the plus operator (`+`).</span></span> <span data-ttu-id="364ec-275">다음 예제에서는 두 개의 배열을 만들고이를 결합 한 다음 결과 결합 된 배열을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-275">The following example creates two arrays, combines them, and then displays the resulting combined array.</span></span>

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

<span data-ttu-id="364ec-276">결과적으로 배열에는 `$z` 1, 3, 5, 9가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-276">As a result, the `$z` array contains 1, 3, 5, and 9.</span></span>

<span data-ttu-id="364ec-277">배열을 삭제 하려면 값을 `$null` 배열에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-277">To delete an array, assign a value of `$null` to the array.</span></span> <span data-ttu-id="364ec-278">다음 명령은 변수에서 배열을 삭제 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="364ec-278">The following command deletes the array in the `$a` variable.</span></span>

`$a = $null`

<span data-ttu-id="364ec-279">`Remove-Item`Cmdlet을 사용할 수도 있지만, 값을 할당 하는 `$null` 것은 특히 많은 배열의 경우 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-279">You can also use the `Remove-Item` cmdlet, but assigning a value of `$null` is faster, especially for large arrays.</span></span>

## <a name="arrays-of-zero-or-one"></a><span data-ttu-id="364ec-280">0 또는 1의 배열</span><span class="sxs-lookup"><span data-stu-id="364ec-280">Arrays of zero or one</span></span>

<span data-ttu-id="364ec-281">Windows PowerShell 3.0부터 0 개 또는 한 개의 개체 컬렉션에 Count 및 Length 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-281">Beginning in Windows PowerShell 3.0, a collection of zero or one object has the Count and Length property.</span></span> <span data-ttu-id="364ec-282">또한 한 개체의 배열에 대 한 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-282">Also, you can index into an array of one object.</span></span> <span data-ttu-id="364ec-283">이 기능을 사용 하면 컬렉션을 필요로 하는 명령이 두 개 미만의 항목 보다 작은 경우 발생 하는 스크립팅 오류를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-283">This feature helps you to avoid scripting errors that occur when a command that expects a collection gets fewer than two items.</span></span>

<span data-ttu-id="364ec-284">다음 예에서는이 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-284">The following examples demonstrate this feature.</span></span>

### <a name="zero-objects"></a><span data-ttu-id="364ec-285">0 개 개체</span><span class="sxs-lookup"><span data-stu-id="364ec-285">Zero objects</span></span>

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a><span data-ttu-id="364ec-286">개체 하나</span><span class="sxs-lookup"><span data-stu-id="364ec-286">One object</span></span>

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a><span data-ttu-id="364ec-287">System.string 개체에 대 한 인덱싱 지원</span><span class="sxs-lookup"><span data-stu-id="364ec-287">Indexing support for System.Tuple objects</span></span>

<span data-ttu-id="364ec-288">PowerShell 6.1에는 배열과 유사한 **튜플** 개체의 인덱싱된 액세스에 대 한 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-288">PowerShell 6.1 added the support for indexed access of **Tuple** objects, similar to arrays.</span></span>
<span data-ttu-id="364ec-289">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="364ec-289">For example:</span></span>

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

<span data-ttu-id="364ec-290">배열 및 다른 컬렉션 개체와 달리 **튜플** 개체는 파이프라인을 통해 전달 될 때 또는 개체의 배열을 지 원하는 매개 변수를 통해 전달 될 때 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="364ec-290">Unlike arrays and other collection objects, **Tuple** objects are treated as a single object when passed through the pipeline or by parameters that support arrays of objects.</span></span>

<span data-ttu-id="364ec-291">자세한 내용은 [system.object](/dotnet/api/system.tuple)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="364ec-291">For more information, see [System.Tuple](/dotnet/api/system.tuple).</span></span>

## <a name="see-also"></a><span data-ttu-id="364ec-292">참고 항목</span><span class="sxs-lookup"><span data-stu-id="364ec-292">See also</span></span>

- [<span data-ttu-id="364ec-293">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="364ec-293">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="364ec-294">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="364ec-294">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="364ec-295">about_Operators</span><span class="sxs-lookup"><span data-stu-id="364ec-295">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="364ec-296">about_For</span><span class="sxs-lookup"><span data-stu-id="364ec-296">about_For</span></span>](about_For.md)
- [<span data-ttu-id="364ec-297">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="364ec-297">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="364ec-298">about_While</span><span class="sxs-lookup"><span data-stu-id="364ec-298">about_While</span></span>](about_While.md)

