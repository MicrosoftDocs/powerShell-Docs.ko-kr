---
title: Quantity 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369562"
---
# <a name="quantity-parameters"></a><span data-ttu-id="244c1-102">수량 매개 변수수량 매개 변수</span><span class="sxs-lookup"><span data-stu-id="244c1-102">Quantity Parameters</span></span>

<span data-ttu-id="244c1-103">다음 표에서는 quantity 매개 변수에 대 한 권장 이름 및 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="244c1-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="244c1-104">Parameter</span></span>|<span data-ttu-id="244c1-105">기능</span><span class="sxs-lookup"><span data-stu-id="244c1-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="244c1-106">**All**</span><span class="sxs-lookup"><span data-stu-id="244c1-106">**All**</span></span><br><span data-ttu-id="244c1-107">데이터 형식: Boolean</span><span class="sxs-lookup"><span data-stu-id="244c1-107">Data type: Boolean</span></span>|<span data-ttu-id="244c1-108">이 매개 변수를 구현 하 여 `true`는 리소스의 기본 하위 집합 대신 모든 리소스를 처리 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="244c1-109">`false`에서 리소스의 하위 집합을 표시 하도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="244c1-110">**Allocation**</span><span class="sxs-lookup"><span data-stu-id="244c1-110">**Allocation**</span></span><br><span data-ttu-id="244c1-111">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="244c1-111">Data type: Int32</span></span>|<span data-ttu-id="244c1-112">사용자가 할당할 항목 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="244c1-113">**블록 수**</span><span class="sxs-lookup"><span data-stu-id="244c1-113">**BlockCount**</span></span><br><span data-ttu-id="244c1-114">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="244c1-114">Data type: Int64</span></span>|<span data-ttu-id="244c1-115">사용자가 블록 수를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="244c1-116">**개수**</span><span class="sxs-lookup"><span data-stu-id="244c1-116">**Count**</span></span><br><span data-ttu-id="244c1-117">데이터 형식: Int64</span><span class="sxs-lookup"><span data-stu-id="244c1-117">Data type: Int64</span></span>|<span data-ttu-id="244c1-118">이 매개 변수를 구현 하 여 사용자가 수를 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="244c1-119">**범위**</span><span class="sxs-lookup"><span data-stu-id="244c1-119">**Scope**</span></span><br><span data-ttu-id="244c1-120">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="244c1-120">Data type: Keyword</span></span>|<span data-ttu-id="244c1-121">사용자가 작동할 범위를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="244c1-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="244c1-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="244c1-122">See Also</span></span>

[<span data-ttu-id="244c1-123">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="244c1-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

<span data-ttu-id="244c1-124">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="244c1-124">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="244c1-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="244c1-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
