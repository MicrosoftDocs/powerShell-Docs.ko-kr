---
title: 수량 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067538"
---
# <a name="quantity-parameters"></a><span data-ttu-id="ac5ec-102">수량 매개 변수수량 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ac5ec-102">Quantity Parameters</span></span>

<span data-ttu-id="ac5ec-103">다음 표에서 권장 되는 이름 및 수량 매개 변수에 대 한 기능을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="ac5ec-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ac5ec-104">Parameter</span></span>|<span data-ttu-id="ac5ec-105">기능</span><span class="sxs-lookup"><span data-stu-id="ac5ec-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="ac5ec-106">**모든**</span><span class="sxs-lookup"><span data-stu-id="ac5ec-106">**All**</span></span><br><span data-ttu-id="ac5ec-107">데이터 형식: 부울</span><span class="sxs-lookup"><span data-stu-id="ac5ec-107">Data type: Boolean</span></span>|<span data-ttu-id="ac5ec-108">이 매개 변수를 구현 하도록 `true` 리소스의 기본 하위 집합이 아니라 리소스를 모두 처리 되는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="ac5ec-109">이 매개 변수를 구현 하도록 `false` 리소스의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="ac5ec-110">**할당**</span><span class="sxs-lookup"><span data-stu-id="ac5ec-110">**Allocation**</span></span><br><span data-ttu-id="ac5ec-111">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="ac5ec-111">Data type: Int32</span></span>|<span data-ttu-id="ac5ec-112">사용자를 할당 하는 항목의 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="ac5ec-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="ac5ec-113">**BlockCount**</span></span><br><span data-ttu-id="ac5ec-114">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="ac5ec-114">Data type: Int64</span></span>|<span data-ttu-id="ac5ec-115">사용자는 블록 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="ac5ec-116">**개수**</span><span class="sxs-lookup"><span data-stu-id="ac5ec-116">**Count**</span></span><br><span data-ttu-id="ac5ec-117">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="ac5ec-117">Data type: Int64</span></span>|<span data-ttu-id="ac5ec-118">사용자 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="ac5ec-119">**범위**</span><span class="sxs-lookup"><span data-stu-id="ac5ec-119">**Scope**</span></span><br><span data-ttu-id="ac5ec-120">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="ac5ec-120">Data type: Keyword</span></span>|<span data-ttu-id="ac5ec-121">사용자에 대해 작동 하는 범위를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ac5ec-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac5ec-122">See Also</span></span>

[<span data-ttu-id="ac5ec-123">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ac5ec-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

<span data-ttu-id="ac5ec-124">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="ac5ec-124">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="ac5ec-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ac5ec-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
