---
ms.date: 09/13/2016
ms.topic: reference
title: 수량 매개 변수수량 매개 변수
description: 수량 매개 변수수량 매개 변수
ms.openlocfilehash: 3f7c23eec34a709b1f2d59f611c93909b20f4124
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650302"
---
# <a name="quantity-parameters"></a><span data-ttu-id="c6485-103">수량 매개 변수수량 매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6485-103">Quantity Parameters</span></span>

<span data-ttu-id="c6485-104">다음 표에서는 quantity 매개 변수에 대 한 권장 이름 및 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-104">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="c6485-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6485-105">Parameter</span></span>|<span data-ttu-id="c6485-106">기능</span><span class="sxs-lookup"><span data-stu-id="c6485-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="c6485-107">**모두**</span><span class="sxs-lookup"><span data-stu-id="c6485-107">**All**</span></span><br><span data-ttu-id="c6485-108">데이터 형식: Boolean</span><span class="sxs-lookup"><span data-stu-id="c6485-108">Data type: Boolean</span></span>|<span data-ttu-id="c6485-109">이 매개 변수를 구현 하 여 `true` 모든 리소스가 리소스의 기본 하위 집합 대신 처리 되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-109">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="c6485-110">이 매개 변수를 구현 하 여 `false` 리소스의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-110">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="c6485-111">**Allocation**</span><span class="sxs-lookup"><span data-stu-id="c6485-111">**Allocation**</span></span><br><span data-ttu-id="c6485-112">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="c6485-112">Data type: Int32</span></span>|<span data-ttu-id="c6485-113">사용자가 할당할 항목 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-113">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="c6485-114">**블록 수**</span><span class="sxs-lookup"><span data-stu-id="c6485-114">**BlockCount**</span></span><br><span data-ttu-id="c6485-115">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="c6485-115">Data type: Int64</span></span>|<span data-ttu-id="c6485-116">사용자가 블록 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-116">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="c6485-117">**개수**</span><span class="sxs-lookup"><span data-stu-id="c6485-117">**Count**</span></span><br><span data-ttu-id="c6485-118">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="c6485-118">Data type: Int64</span></span>|<span data-ttu-id="c6485-119">이 매개 변수를 구현 하 여 사용자가 수를 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-119">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="c6485-120">**범위**</span><span class="sxs-lookup"><span data-stu-id="c6485-120">**Scope**</span></span><br><span data-ttu-id="c6485-121">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="c6485-121">Data type: Keyword</span></span>|<span data-ttu-id="c6485-122">사용자가 작동할 범위를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6485-122">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c6485-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6485-123">See Also</span></span>

[<span data-ttu-id="c6485-124">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6485-124">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

<span data-ttu-id="c6485-125">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="c6485-125">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="c6485-126">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c6485-126">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
