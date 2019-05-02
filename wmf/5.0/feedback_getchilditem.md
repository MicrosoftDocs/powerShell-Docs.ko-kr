---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085296"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="0219c-102">Get-ChildItem의 -Depth 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0219c-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="0219c-103">이제 **Get-ChildItem**은 **–Recurse**와 함께 사용되어 재귀를 제한하는 **–Depth** 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0219c-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="0219c-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="0219c-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="0219c-105">디렉터리: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="0219c-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="0219c-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="0219c-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="0219c-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="0219c-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="0219c-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="0219c-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="0219c-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="0219c-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="0219c-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="0219c-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="0219c-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="0219c-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="0219c-112">디렉터리: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="0219c-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="0219c-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="0219c-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="0219c-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="0219c-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="0219c-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="0219c-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="0219c-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="0219c-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="0219c-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="0219c-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="0219c-118">디렉터리: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="0219c-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="0219c-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="0219c-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="0219c-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="0219c-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
