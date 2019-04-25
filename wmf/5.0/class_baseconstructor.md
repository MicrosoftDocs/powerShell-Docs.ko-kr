---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085884"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="2e260-102">기본 클래스 생성자 호출</span><span class="sxs-lookup"><span data-stu-id="2e260-102">Call Base Class Constructor</span></span>

<span data-ttu-id="2e260-103">하위 클래스에서 기본 클래스 생성자를 호출하려면 **base** 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e260-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="2e260-104">기본 클래스에 기본(매개 변수 없음) 생성자가 있는 경우 명시적 생성자 호출을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e260-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
