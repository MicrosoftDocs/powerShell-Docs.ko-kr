---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057794"
---
# <a name="convert-string"></a><span data-ttu-id="eed66-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="eed66-102">Convert-String</span></span>
<span data-ttu-id="eed66-103">**Convert-String**은 "자동 대체" 기능을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="eed66-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="eed66-104">텍스트가 어떻게 표시되는지에 대한 이전 및 이후 예제를 제공하면 **Convert-String**에서 자동으로 텍스트 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eed66-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="eed66-105">다음은 어떤 사람의 이름과 성을 가져오고 성, 쉼표, 성의 첫 이니셜 및 점으로 바꾸는 데모입니다.</span><span class="sxs-lookup"><span data-stu-id="eed66-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="eed66-106">정규식을 사용하여 시간이 얼마나 걸리는지 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="eed66-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
