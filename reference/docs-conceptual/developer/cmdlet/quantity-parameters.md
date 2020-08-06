---
title: Quantity 매개 변수 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7ff6562380bb6336b08879b31d8d9fed47bfb6a7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781820"
---
# <a name="quantity-parameters"></a><span data-ttu-id="9dc93-102">수량 매개 변수수량 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9dc93-102">Quantity Parameters</span></span>

<span data-ttu-id="9dc93-103">다음 표에서는 quantity 매개 변수에 대 한 권장 이름 및 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="9dc93-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9dc93-104">Parameter</span></span>|<span data-ttu-id="9dc93-105">기능</span><span class="sxs-lookup"><span data-stu-id="9dc93-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="9dc93-106">**모두**</span><span class="sxs-lookup"><span data-stu-id="9dc93-106">**All**</span></span><br><span data-ttu-id="9dc93-107">데이터 형식: Boolean</span><span class="sxs-lookup"><span data-stu-id="9dc93-107">Data type: Boolean</span></span>|<span data-ttu-id="9dc93-108">이 매개 변수를 구현 하 여 `true` 모든 리소스가 리소스의 기본 하위 집합 대신 처리 되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="9dc93-109">이 매개 변수를 구현 하 여 `false` 리소스의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="9dc93-110">**Allocation**</span><span class="sxs-lookup"><span data-stu-id="9dc93-110">**Allocation**</span></span><br><span data-ttu-id="9dc93-111">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="9dc93-111">Data type: Int32</span></span>|<span data-ttu-id="9dc93-112">사용자가 할당할 항목 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="9dc93-113">**블록 수**</span><span class="sxs-lookup"><span data-stu-id="9dc93-113">**BlockCount**</span></span><br><span data-ttu-id="9dc93-114">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="9dc93-114">Data type: Int64</span></span>|<span data-ttu-id="9dc93-115">사용자가 블록 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="9dc93-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="9dc93-116">**Count**</span></span><br><span data-ttu-id="9dc93-117">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="9dc93-117">Data type: Int64</span></span>|<span data-ttu-id="9dc93-118">이 매개 변수를 구현 하 여 사용자가 수를 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="9dc93-119">**범위**</span><span class="sxs-lookup"><span data-stu-id="9dc93-119">**Scope**</span></span><br><span data-ttu-id="9dc93-120">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="9dc93-120">Data type: Keyword</span></span>|<span data-ttu-id="9dc93-121">사용자가 작동할 범위를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dc93-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9dc93-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9dc93-122">See Also</span></span>

[<span data-ttu-id="9dc93-123">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9dc93-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="9dc93-124">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9dc93-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9dc93-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9dc93-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
