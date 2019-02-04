---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682133"
---
# <a name="call-base-class-method"></a><span data-ttu-id="30806-102">기본 클래스 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="30806-102">Call Base Class Method</span></span>

<span data-ttu-id="30806-103">하위 클래스에서 기존 메서드를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30806-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="30806-104">이렇게 하려면 동일한 이름과 서명을 사용하여 메서드를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="30806-104">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="30806-105">재정의된 구현에서 기본 클래스 메서드를 호출하려면 호출할 때 기본 클래스([baseClass]$this)로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="30806-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="30806-106">모든 PowerShell 메서드는 가상입니다.</span><span class="sxs-lookup"><span data-stu-id="30806-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="30806-107">재정의에 사용한 것과 동일한 구문을 사용하여 하위 클래스에서 비가상 .NET 메서드를 숨길 수 있습니다. 동일한 이름과 서명으로 메서드를 선언하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30806-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
