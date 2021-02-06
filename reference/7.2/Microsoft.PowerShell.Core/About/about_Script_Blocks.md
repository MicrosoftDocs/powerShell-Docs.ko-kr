---
description: 스크립트 블록이 무엇 인지 정의 하 고 PowerShell 프로그래밍 언어에서 스크립트 블록을 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1ba5e92bedc03a2d61d528715ab13c5d96eb3075
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602690"
---
# <a name="about-script-blocks"></a><span data-ttu-id="69615-103">스크립트 블록 정보</span><span class="sxs-lookup"><span data-stu-id="69615-103">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="69615-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="69615-104">Short description</span></span>

<span data-ttu-id="69615-105">스크립트 블록이 무엇 인지 정의 하 고 PowerShell 프로그래밍 언어에서 스크립트 블록을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-105">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="69615-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="69615-106">Long description</span></span>

<span data-ttu-id="69615-107">PowerShell 프로그래밍 언어에서 스크립트 블록은 단일 단위로 사용할 수 있는 문 또는 식의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="69615-107">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="69615-108">스크립트 블록은 인수를 받아서 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-108">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="69615-109">구문적으로 스크립트 블록은 다음 구문에 표시 된 것 처럼 중괄호의 문 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="69615-109">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="69615-110">스크립트 블록은 스크립트 블록의 모든 명령에 대 한 출력을 단일 개체 또는 배열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-110">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="69615-111">키워드를 사용 하 여 반환 값을 지정할 수도 있습니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="69615-111">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="69615-112">`return`키워드는 스크립트 블록에서 반환 된 다른 출력에 영향을 주거나 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-112">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="69615-113">그러나 키워드는 `return` 해당 줄에서 스크립트 블록을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-113">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="69615-114">자세한 내용은 [about_Return](about_Return.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69615-114">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="69615-115">함수와 마찬가지로 스크립트 블록에는 매개 변수가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-115">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="69615-116">다음 구문과 같이 Param 키워드를 사용 하 여 명명 된 매개 변수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-116">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="69615-117">스크립트 블록에서 함수와 달리 중괄호 외부에 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-117">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="69615-118">함수와 마찬가지로 스크립트 블록에는,, `DynamicParam` `Begin` `Process` 및 키워드가 포함 될 수 있습니다 `End` .</span><span class="sxs-lookup"><span data-stu-id="69615-118">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="69615-119">자세한 내용은 [about_Functions](about_Functions.md) 및 [about_Functions_Advanced](about_Functions_Advanced.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69615-119">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="69615-120">스크립트 블록 사용</span><span class="sxs-lookup"><span data-stu-id="69615-120">Using Script Blocks</span></span>

<span data-ttu-id="69615-121">스크립트 블록은 Microsoft .NET Framework 형식의 인스턴스입니다 `System.Management.Automation.ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="69615-121">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="69615-122">명령에는 스크립트 블록 매개 변수 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-122">Commands can have script block parameter values.</span></span> <span data-ttu-id="69615-123">예를 들어 cmdlet에는 `Invoke-Command` `ScriptBlock` 다음 예제와 같이 스크립트 블록 값을 사용 하는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-123">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

<span data-ttu-id="69615-124">`Invoke-Command` 는 매개 변수 블록을 포함 하는 스크립트 블록을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-124">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="69615-125">매개 변수는 **Argumentlist** 매개 변수를 사용 하 여 위치에 의해 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69615-125">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

<span data-ttu-id="69615-126">이전 예제의 스크립트 블록은 키워드를 사용 하 여 `param` 및 매개 변수를 `$p1` 만듭니다 `$p2` .</span><span class="sxs-lookup"><span data-stu-id="69615-126">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="69615-127">"First" 문자열은 첫 번째 매개 변수 ()에 바인딩되고 `$p1` "Second"는 ()에 바인딩됩니다 `$p2` .</span><span class="sxs-lookup"><span data-stu-id="69615-127">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="69615-128">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69615-128">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="69615-129">변수를 사용 하 여 스크립트 블록을 저장 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-129">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="69615-130">아래 예제에서는 스크립트 블록을 변수에 저장 하 고에 전달 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-130">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="69615-131">Call 연산자는 변수에 저장 된 스크립트 블록을 실행 하는 또 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="69615-131">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="69615-132">Like `Invoke-Command` 연산자는 자식 범위에서 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-132">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="69615-133">Call 연산자를 사용 하면 스크립트 블록에서 매개 변수를 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-133">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

<span data-ttu-id="69615-134">할당을 사용 하 여 스크립트 블록의 출력을 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-134">You can store the output from your script blocks in a variable using assignment.</span></span>

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

<span data-ttu-id="69615-135">호출 연산자에 대 한 자세한 내용은 [about_Operators](about_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69615-135">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="69615-136">매개 변수가 포함 된 지연 바인딩 스크립트 블록 사용</span><span class="sxs-lookup"><span data-stu-id="69615-136">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="69615-137">파이프라인 입력 () 또는 ()를 허용 하는 형식화 된 매개 변수는 `by Value` `by PropertyName` 매개 변수에 대해 **지연 바인딩** 스크립트 블록을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-137">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="69615-138">**지연 바인딩** 스크립트 블록 내에서 파이프라인 변수를 사용 하 여 파이프에서 파이프 된를 참조할 수 있습니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="69615-138">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="69615-139">더 복잡 한 cmdlet에서는 지연 바인딩 스크립트 블록을 사용 하 여 개체에서 파이프 된를 다시 사용 하 여 다른 매개 변수를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69615-139">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="69615-140">**지연-** 스크립트 블록을 매개 변수로 바인딩하는 방법에 대 한 참고 사항:</span><span class="sxs-lookup"><span data-stu-id="69615-140">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="69615-141">**지연 바인드** 스크립트 블록에서 사용 하는 매개 변수 이름을 명시적으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69615-141">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="69615-142">매개 변수는 형식화 되지 않아야 하 고 매개 변수의 형식은 또는 일 수 `[scriptblock]` 없습니다 `[object]` .</span><span class="sxs-lookup"><span data-stu-id="69615-142">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="69615-143">파이프라인 입력을 제공 하지 않고 **지연 바인드** 스크립트 블록을 사용 하는 경우 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69615-143">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a><span data-ttu-id="69615-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69615-144">See Also</span></span>

[<span data-ttu-id="69615-145">about_Functions</span><span class="sxs-lookup"><span data-stu-id="69615-145">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="69615-146">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="69615-146">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="69615-147">about_Operators</span><span class="sxs-lookup"><span data-stu-id="69615-147">about_Operators</span></span>](about_Operators.md)

