---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682293"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="9e8c5-102">구현된 인터페이스 선언</span><span class="sxs-lookup"><span data-stu-id="9e8c5-102">Declare Implemented Interface</span></span>

<span data-ttu-id="9e8c5-103">구현된 인터페이스는 기본 형식 다음이나 지정된 기본 형식이 없는 경우 콜론(:) 바로 다음에 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8c5-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="9e8c5-104">쉼표를 사용하여 모든 형식 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8c5-104">Separate all type names by using commas.</span></span> <span data-ttu-id="9e8c5-105">C# 구문과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8c5-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```
