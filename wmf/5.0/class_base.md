---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 8b3ebd22e03bf9bdd5f26965137a1b1ce9f47c3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058780"
---
# <a name="declare-base-class"></a><span data-ttu-id="7f6e5-102">기본 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="7f6e5-102">Declare Base Class</span></span>
<span data-ttu-id="7f6e5-103">Windows PowerShell 클래스를 다른 Windows PowerShell 클래스의 기본 형식으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f6e5-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="7f6e5-104">또한 기존 .NET Framework 형식을 기본 클래스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f6e5-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
