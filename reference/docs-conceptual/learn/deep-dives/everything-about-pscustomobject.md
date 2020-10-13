---
title: PSCustomObject에 대해 알고 싶은 모든 것
description: PSCustomObject는 구조화된 데이터를 만드는 단순한 방법입니다.
ms.date: 10/05/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ccbdcdae5ad38f555233dffbed7e8a6ec2b0726b
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91772323"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="cb078-103">PSCustomObject에 대해 알고 싶은 모든 것</span><span class="sxs-lookup"><span data-stu-id="cb078-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="cb078-104">`PSCustomObject`는 PowerShell 도구 벨트에 추가하는 작업을 처리하는 탁월한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="cb078-105">기본 사항부터 시작한 다음 고급 기능을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="cb078-106">`PSCustomObject` 사용의 기본 목적은 구조화된 데이터를 간단하게 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="cb078-107">첫 번째 예제를 살펴보면 무슨 말인지 잘 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="cb078-108">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="cb078-109">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="cb078-110">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="cb078-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="cb078-111">PSCustomObject 만들기</span><span class="sxs-lookup"><span data-stu-id="cb078-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="cb078-112">저는 PowerShell에서 `[PSCustomObject]`를 즐겨 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="cb078-113">사용 가능한 개체를 만들기가 그 어느 때보다도 쉬워졌습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="cb078-114">따라서 개체를 만드는 다른 방법은 설명하지 않겠습니다. 여기에 있는 예제 대부분은 PowerShell v3.0 이상을 기준으로 한다는 점만 말씀드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="cb078-115">거의 모든 요소에 해시 테이블을 사용하기 때문에 이 방법이 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="cb078-116">하지만 PowerShell에서 해시 테이블을 개체처럼 처리할 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="cb078-117">가장 큰 차이점은 `Format-Table`이나 `Export-CSV`를 사용할 때는 해시 테이블은 단순한 키/값 쌍 컬렉션에 불과하다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="cb078-118">그런 다음 일반 개체처럼 값에 액세스하고 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="cb078-119">해시 테이블 변환</span><span class="sxs-lookup"><span data-stu-id="cb078-119">Converting a hashtable</span></span>

<span data-ttu-id="cb078-120">지금은 이 주제를 다루고 있지만, 여러분은 다음과 같은 작업도 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="cb078-121">개체를 완전히 새로 만드는 방법을 선호하지만 간혹 해시 테이블을 먼저 작업해야 할 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="cb078-122">이 예제는 생성자가 개체 속성에 해시 테이블을 사용하기 때문에 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="cb078-123">한 가지 중요한 점은 이 메서드가 작동하는 동안에는 정확하게 동등하지 않다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="cb078-124">가장 큰 차이점은 속성의 순서가 유지되지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="cb078-125">기존의 접근 방식</span><span class="sxs-lookup"><span data-stu-id="cb078-125">Legacy approach</span></span>

<span data-ttu-id="cb078-126">사람들이 `New-Object`를 이용해 사용자 지정 개체를 만다는 모습을 보셨을 겁니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="cb078-127">이 방법은 속도는 조금 느리지만 PowerShell 초기 버전에서는 가장 적합한 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="cb078-128">폴더에 저장</span><span class="sxs-lookup"><span data-stu-id="cb078-128">Saving to a file</span></span>

<span data-ttu-id="cb078-129">해시 테이블을 파일에 저장하는 가장 좋은 방법은 JSON으로 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="cb078-130">`[PSCustomObject]`로 다시 가져오면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-130">You can import it back into a `[PSCustomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="cb078-131">제 게시물인 [파일 읽기 및 쓰기를 수행하는 다양한 방법][]에서 파일에 개체를 저장하는 다른 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="cb078-132">속성 작업</span><span class="sxs-lookup"><span data-stu-id="cb078-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="cb078-133">속성 추가</span><span class="sxs-lookup"><span data-stu-id="cb078-133">Adding properties</span></span>

<span data-ttu-id="cb078-134">`Add-Member`를 사용하여 `PSCustomObject`에 새 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="cb078-135">속성 제거</span><span class="sxs-lookup"><span data-stu-id="cb078-135">Remove properties</span></span>

<span data-ttu-id="cb078-136">개체에서 속성을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="cb078-137">`psobject`는 기본 개체 메타데이터에 대 한 액세스를 제공하는 숨겨진 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="cb078-138">속성 이름 열거</span><span class="sxs-lookup"><span data-stu-id="cb078-138">Enumerating property names</span></span>

<span data-ttu-id="cb078-139">개체에 모든 속성 이름 목록이 필요할 때가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="cb078-140">`psobject` 속성에서도 동일한 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="cb078-141">속성에 동적으로 액세스</span><span class="sxs-lookup"><span data-stu-id="cb078-141">Dynamically accessing properties</span></span>

<span data-ttu-id="cb078-142">속성 값에 직접 액세스할 수 있다는 사실은 이미 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="cb078-143">속성 이름에는 문자열을 사용할 수 있으며, 작동에는 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="cb078-144">이 추가 단계를 수행하고 속성 이름에 변수를 사용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="cb078-145">이상하게 보이겠지만 작동에는 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomobject-into-a-hashtable"></a><span data-ttu-id="cb078-146">PSCustomObject를 해시 테이블로 변환</span><span class="sxs-lookup"><span data-stu-id="cb078-146">Convert PSCustomObject into a hashtable</span></span>

<span data-ttu-id="cb078-147">마지막 섹션에서 계속 진행하려면 속성을 동적으로 탐색하고 해당 속성에서 해시 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="cb078-148">속성 테스트</span><span class="sxs-lookup"><span data-stu-id="cb078-148">Testing for properties</span></span>

<span data-ttu-id="cb078-149">속성 존재 여부를 확인해야 한다면 속성에 값이 있는지 확인하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="cb078-150">그러나 값이 `$null`일 수 있는 경우 해당 `psobject.properties`를 확인하여 속성이 존재하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-150">But if the value could be `$null` you can check to see if it exists by checking the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID').Count )
```

## <a name="adding-object-methods"></a><span data-ttu-id="cb078-151">개체 메서드 추가</span><span class="sxs-lookup"><span data-stu-id="cb078-151">Adding object methods</span></span>

<span data-ttu-id="cb078-152">개체에 스크립트 메서드를 추가해야 한다면 `Add-Member` 및 `ScriptBlock`을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="cb078-153">`this` 자동 변수를 사용하여 현재 개체를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="cb078-154">다음은 개체를 해시 테이블로 변환하는 `scriptblock`입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="cb078-155">(마지막 예제와 동일한 코드 형식)</span><span class="sxs-lookup"><span data-stu-id="cb078-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="cb078-156">그런 다음 이를 스크립트 속성으로 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="cb078-157">그러면 다음과 같이 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="cb078-158">개체 및 값 형식</span><span class="sxs-lookup"><span data-stu-id="cb078-158">Objects vs Value types</span></span>

<span data-ttu-id="cb078-159">개체 형식과 값 형식은 서로 다른 방식으로 변수 할당을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="cb078-160">값 형식을 서로 할당하면 값만 새 변수에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="cb078-161">이 경우 `$first`는 1이고 `$second`는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="cb078-162">개체 변수는 실제 개체에 대한 참조를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="cb078-163">한 개체를 새 변수에 추가해도 여전히 같은 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="cb078-164">`$third`와 `$fourth`는 개체의 같은 인스턴스를 참조하므로 `$third.key`와 `$fourth.Key`는 모두 4입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="cb078-165">psobject.copy()</span><span class="sxs-lookup"><span data-stu-id="cb078-165">psobject.copy()</span></span>

<span data-ttu-id="cb078-166">개체의 실제 복사본이 필요하다면 개체를 복제하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="cb078-167">복제는 개체의 단순 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="cb078-168">이제 서로 다른 인스턴스가 존재하며 이 예제에서 `$third.key`는 3이고 `$fourth.Key`는 4입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="cb078-169">중첩된 개체가 있으므로 저는 이것을 단순 복사본이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="cb078-170">(속성에 다른 개체가 포함된 경우).</span><span class="sxs-lookup"><span data-stu-id="cb078-170">(where the properties contain other objects).</span></span> <span data-ttu-id="cb078-171">최상위 값만 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-171">Only the top-level values are copied.</span></span> <span data-ttu-id="cb078-172">자식 개체는 서로를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="cb078-173">사용자 지정 개체 형식에 대한 PSTypeName</span><span class="sxs-lookup"><span data-stu-id="cb078-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="cb078-174">이제 개체가 있으므로 개체를 이용해 모호할 수 있는 몇 가지 추가 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="cb078-175">제일 먼저 할 일은 `PSTypeName`을 부여하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="cb078-176">이것은 사람들이 가장 많이 선택하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="cb078-177">얼마 전 [/u/markekraus의 게시물][]에서 다른 수행 방법을 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="cb078-178">그리고 다른 게시물을 살펴보면서 [Adam Bertram][]과 [Mike Shepard][]가 말하는 인라인으로 정의하는 방법을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="cb078-179">언어에도 아주 잘 어울리는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="cb078-180">이제 적절한 형식 이름을 가진 개체가 있으니 더 많은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

> [!NOTE]
> <span data-ttu-id="cb078-181">PowerShell 클래스를 사용하여 사용자 지정 PowerShell 형식을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-181">You can also create custom PowerShell types using PowerShell classes.</span></span> <span data-ttu-id="cb078-182">자세한 내용은 [PowerShell 클래스 개요](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb078-182">For more information, see [PowerShell Class Overview](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="cb078-183">DefaultPropertySet 사용(긴 방식)</span><span class="sxs-lookup"><span data-stu-id="cb078-183">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="cb078-184">PowerShell은 사용자를 대신하여 기본적으로 표시할 속성을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-184">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="cb078-185">많은 네이티브 명령에는 어려운 일을 모두 처리하는 `.ps1xml` [서식 지정 파일][]이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-185">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="cb078-186">이 [Boe Prox가 게시][]에서는 PowerShell만 이용해 사용자 지정 개체에서 이 작업을 하는 다른 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-186">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="cb078-187">PowerShell에서 사용할 `MemberSet`를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-187">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet('DefaultDisplayPropertySet',[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="cb078-188">개체가 셸에 들어가면 기본적으로 이러한 속성만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-188">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="cb078-189">DefaultPropertySet가 있는 Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="cb078-189">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="cb078-190">좋은 방법이긴 하지만 얼마 전에 [Jeffrey Snover 및 Don Jones외의 PowerShell 언플러그드 2016][psunplugged]을 시청하면서 더 좋은 방법을 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-190">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="cb078-191">Jeffrey는 [Update-TypeData][]를 이용해 기본 속성을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-191">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="cb078-192">너무나 간단해서 이 게시물을 참조하지 않고도 모든 내용을 기억할 정도입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-192">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="cb078-193">이제 많은 속성을 사용하여 개체를 쉽게 만들 수 있으며 셸에서 해당 개체를 살펴볼 때도 여전히 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-193">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="cb078-194">다른 속성에 액세스하거나 속성을 확인해야 한다면 여기서 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-194">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="cb078-195">ScriptProperty가 있는 Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="cb078-195">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="cb078-196">이 동영상에서 알게 된 또 다른 내용은 개체에 대한 스크립트 속성 생성이었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-196">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="cb078-197">기존 개체에도 적용된다는 사실을 말씀드려야 할 것 같네요.</span><span class="sxs-lookup"><span data-stu-id="cb078-197">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="cb078-198">이 작업은 개체 작성 전후 언제든 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-198">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="cb078-199">바로 이점 때문에 이 방법은 스크립트 속성이 있는 `Add-Member` 사용과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-199">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="cb078-200">앞에서 설명한 방식으로 `Add-Member`를 사용하면 개체의 특정 인스턴스에만 존재하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-200">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="cb078-201">이것은 이 `TypeName`이 있는 모든 개체에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-201">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="cb078-202">함수 매개 변수</span><span class="sxs-lookup"><span data-stu-id="cb078-202">Function parameters</span></span>

<span data-ttu-id="cb078-203">이제 함수 및 스크립트의 매개 변수에도 이러한 사용자 지점 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-203">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="cb078-204">특정 함수로 이러한 사용자 지정 개체를 만든 다음 다른 함수로 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-204">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="cb078-205">PowerShell을 이용할 때는 개체가 사용자가 지정한 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-205">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="cb078-206">형식이 자동으로 일치하지 않는다면 유효성 검사 오류가 발생하여 코드에서 이를 테스트하는 단계를 건너뛰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-206">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="cb078-207">PowerShell이 가장 적합한 작업을 수행하게 하는 대표적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-207">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="cb078-208">함수 OutputType</span><span class="sxs-lookup"><span data-stu-id="cb078-208">Function OutputType</span></span>

<span data-ttu-id="cb078-209">고급 기능에 대해 `OutputType`를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-209">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="cb078-210">**OutputType** 특성 값은 문서 참고일뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-210">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="cb078-211">함수 코드에서 파생되거나 실제 함수 출력과 비교되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-211">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="cb078-212">출력 유형을 사용하는 주된 이유는 함수의 메타데이터 정보 사용자의 의도를 반영한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-212">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="cb078-213">개발 환경에서 `Get-Command`와 `Get-Help` 같은 요소를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-213">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="cb078-214">추가 정보가 필요하다면 도움말인 [about_Functions_OutputTypeAttribute][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb078-214">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="cb078-215">말이 나온 김에 설명하자면, Pester를 사용하여 함수를 단위 테스트하는 경우에는 **OutputType**과 일치하는 출력 개체의 유효성을 검사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-215">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="cb078-216">이렇게 하면 잘못된 변수가 파이프에 속하는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-216">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="cb078-217">맺음말</span><span class="sxs-lookup"><span data-stu-id="cb078-217">Closing thoughts</span></span>

<span data-ttu-id="cb078-218">이 문서에서 다룬 내용은 모두 `[PSCustomObject]`를 기준으로 하지만, 여기에 나온 정보 상당수는 개체에도 대체로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-218">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="cb078-219">진행 과정에서 기능을 언급하는 모습은 보았지만 `PSCustomObject` 관련 정보 모음으로 제공되는 모습은 보지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-219">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="cb078-220">지난주 우연히 이를 접했는데 생전 처음 본다는 사실에 놀라고 말았습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-220">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="cb078-221">여러분이 큰 그림을 보고 이러한 정보를 활용할 기회를 놓치지 않도록 모든 정보를 한곳에 모으고 싶었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-221">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="cb078-222">유용한 내용을 배우고 스크립트에서 활용하는 방법을 확인하시길 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="cb078-222">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Boe Prox가 게시]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[서식 지정 파일]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[파일 읽기 및 쓰기를 수행하는 다양한 방법]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[/u/markekraus의 게시물]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
