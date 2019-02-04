---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682333"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="a03ed-102">Get-ChildItem의 -Depth 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a03ed-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="a03ed-103">이제 **Get-ChildItem**은 **–Recurse**와 함께 사용되어 재귀를 제한하는 **–Depth** 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a03ed-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="a03ed-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="a03ed-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="a03ed-105">디렉터리: C:\\사용자가\\slee\\다운로드\\예제</span><span class="sxs-lookup"><span data-stu-id="a03ed-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a03ed-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="a03ed-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a03ed-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="a03ed-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a03ed-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="a03ed-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a03ed-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a03ed-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a03ed-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a03ed-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a03ed-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="a03ed-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="a03ed-112">디렉터리: C:\\사용자가\\slee\\다운로드\\예제</span><span class="sxs-lookup"><span data-stu-id="a03ed-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a03ed-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="a03ed-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a03ed-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="a03ed-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a03ed-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="a03ed-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a03ed-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a03ed-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a03ed-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a03ed-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a03ed-118">디렉터리: C:\\사용자가\\slee\\다운로드\\예제\\Depth0</span><span class="sxs-lookup"><span data-stu-id="a03ed-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="a03ed-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="a03ed-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a03ed-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="a03ed-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
