---
description: 참조 형식 변수를 만들고 사용 하는 방법을 설명 합니다. 참조 형식 변수를 사용 하 여 함수가 전달 되는 변수의 값을 변경할 수 있도록 허용할 수 있습니다.
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: 5b966816c8ac1ef91e03c78378f57fa20b5697de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600150"
---
# <a name="about-ref"></a><span data-ttu-id="58b26-104">Ref 정보</span><span class="sxs-lookup"><span data-stu-id="58b26-104">About Ref</span></span>

## <a name="short-description"></a><span data-ttu-id="58b26-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="58b26-105">Short description</span></span>
<span data-ttu-id="58b26-106">참조 형식 변수를 만들고 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-106">Describes how to create and use a reference type variable.</span></span> <span data-ttu-id="58b26-107">참조 형식 변수를 사용 하 여 함수가 전달 되는 변수의 값을 변경할 수 있도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-107">You can use reference type variables to permit a function to change the value of a variable that is passed to it.</span></span>

## <a name="long-description"></a><span data-ttu-id="58b26-108">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-108">Long description</span></span>

<span data-ttu-id="58b26-109">*참조* 또는 *값* 을 기준으로 함수에 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-109">You can pass variables to functions *by reference* or *by value*.</span></span>

<span data-ttu-id="58b26-110">*값으로* 변수를 전달 하는 경우 데이터의 복사본을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-110">When you pass a variable *by value*, you are passing a copy of the data.</span></span>

<span data-ttu-id="58b26-111">다음 예제에서 함수는 전달 되는 변수의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-111">In the following example, the function changes the value of the variable passed to it.</span></span> <span data-ttu-id="58b26-112">PowerShell에서 정수는 값 형식 이므로 값으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-112">In PowerShell, integers are value types so they are passed by value.</span></span>
<span data-ttu-id="58b26-113">따라서 값은 `$var` 함수 범위 밖으로 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-113">Therefore, the value of `$var` is unchanged outside the scope of the function.</span></span>

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

<span data-ttu-id="58b26-114">다음 예제에서는를 포함 하는 변수를 `Hashtable` 함수에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-114">In the following example, a variable containing a `Hashtable` is passed to a function.</span></span> <span data-ttu-id="58b26-115">`Hashtable` 는 개체 형식 이므로 기본적으로 함수에 *참조로* 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-115">`Hashtable` is an object type so by default it is passed to the function *by reference*.</span></span>

<span data-ttu-id="58b26-116">변수를 *참조로* 전달 하는 경우 함수는 데이터를 변경할 수 있으며 함수가 실행 된 후에도 변경 내용이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-116">When passing a variable *by reference*, the function can change the data and that change persists after the function executes.</span></span>

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

<span data-ttu-id="58b26-117">함수는 함수 범위 외부에 유지 되는 새 키-값 쌍을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-117">The function adds a new key-value pair that persists outside of the function's scope.</span></span>

### <a name="writing-functions-to-accept-reference-parameters"></a><span data-ttu-id="58b26-118">참조 매개 변수를 허용 하는 함수 작성</span><span class="sxs-lookup"><span data-stu-id="58b26-118">Writing functions to accept reference parameters</span></span>

<span data-ttu-id="58b26-119">전달 되는 데이터 형식에 관계 없이 매개 변수를 참조로 사용 하도록 함수를 코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-119">You can code your functions to take a parameter as a reference, regardless of the type of data passed.</span></span> <span data-ttu-id="58b26-120">이렇게 하려면 매개 변수 형식을, 또는로 지정 해야 합니다 `System.Management.Automation.PSReference` `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="58b26-120">This requires that you specify the parameters type as `System.Management.Automation.PSReference`, or `[ref]`.</span></span>

<span data-ttu-id="58b26-121">참조를 사용 하는 경우 `Value` 형식의 속성을 사용 `System.Management.Automation.PSReference` 하 여 데이터에 액세스 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-121">When using references, you must use the `Value` property of the `System.Management.Automation.PSReference` type to access your data.</span></span>

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

<span data-ttu-id="58b26-122">참조를 필요로 하는 매개 변수에 변수를 전달 하려면 변수를 참조로 캐스트를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-122">To pass a variable to a parameter that expects a reference, you must type cast your variable as a reference.</span></span>

> [!NOTE]
> <span data-ttu-id="58b26-123">대괄호와 괄호는 모두 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-123">The brackets and parenthesis are BOTH required.</span></span>

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a><span data-ttu-id="58b26-124">.NET 메서드에 참조 전달</span><span class="sxs-lookup"><span data-stu-id="58b26-124">Passing references to .NET methods</span></span>

<span data-ttu-id="58b26-125">일부 .NET 메서드는 변수를 참조로 전달 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-125">Some .NET methods may require you to pass a variable as a reference.</span></span> <span data-ttu-id="58b26-126">메서드의 정의에서 매개 변수에, 또는 키워드를 사용 하는 경우 `in` `out` `ref` 참조가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-126">When the method's definition uses the keywords `in`, `out`, or `ref` on a parameter, it expects a reference.</span></span>

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

<span data-ttu-id="58b26-127">`TryParse`메서드는 문자열을 정수로 구문 분석 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-127">The `TryParse` method attempts to parse a string as an integer.</span></span> <span data-ttu-id="58b26-128">메서드가 성공 하면 `$true` 가 반환 되 고 결과는 **참조로** 전달 된 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-128">If the method succeeds, it returns `$true`, and the result is stored in the variable you passed **by reference**.</span></span>

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a><span data-ttu-id="58b26-129">참조 및 범위</span><span class="sxs-lookup"><span data-stu-id="58b26-129">References and scopes</span></span>

<span data-ttu-id="58b26-130">참조를 사용 하면 부모 범위의 변수 값을 자식 범위 내에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-130">References allow the value of a variable in the parent scope to be changed within a child scope.</span></span>

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

<span data-ttu-id="58b26-131">참조 형식의 변수만 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b26-131">Only the reference type's variable was changed.</span></span>

## <a name="see-also"></a><span data-ttu-id="58b26-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58b26-132">See also</span></span>

[<span data-ttu-id="58b26-133">about_Variables</span><span class="sxs-lookup"><span data-stu-id="58b26-133">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="58b26-134">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="58b26-134">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="58b26-135">about_Functions</span><span class="sxs-lookup"><span data-stu-id="58b26-135">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="58b26-136">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="58b26-136">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="58b26-137">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="58b26-137">about_Scopes</span></span>](about_scopes.md)

