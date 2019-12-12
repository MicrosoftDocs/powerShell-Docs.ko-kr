---
title: AccessDbProviderSample04 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366972"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="e3997-102">AccessDbProviderSample04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="e3997-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="e3997-103">다음 코드는 [Windows Powershell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)에서 설명 하는 windows powershell 공급자의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e3997-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="e3997-104">이 공급자는 다중 계층 데이터 저장소에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3997-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="e3997-105">이러한 유형의 데이터 저장소의 경우 저장소의 최상위 수준에 루트 항목이 포함 되 고 각 후속 수준은 자식 항목의 노드 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3997-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="e3997-106">사용자는 이러한 자식 노드에 대해 작업을 수행할 수 있으므로 데이터 저장소를 통해 계층적으로 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3997-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e3997-107">코드 예제</span><span class="sxs-lookup"><span data-stu-id="e3997-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="e3997-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3997-108">See Also</span></span>

[<span data-ttu-id="e3997-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e3997-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
