---
title: AccessDbProviderSample04 코드 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 05509c5b36475bcd3f91c9ab7413974994d668d6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787277"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="ea4c8-102">AccessDbProviderSample04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="ea4c8-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="ea4c8-103">다음 코드는 [Windows Powershell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)에서 설명 하는 windows powershell 공급자의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea4c8-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="ea4c8-104">이 공급자는 다중 계층 데이터 저장소에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea4c8-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="ea4c8-105">이러한 유형의 데이터 저장소의 경우 저장소의 최상위 수준에 루트 항목이 포함 되 고 각 후속 수준은 자식 항목의 노드 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea4c8-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="ea4c8-106">사용자는 이러한 자식 노드에 대해 작업을 수행할 수 있으므로 데이터 저장소를 통해 계층적으로 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea4c8-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ea4c8-107">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ea4c8-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="ea4c8-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea4c8-108">See Also</span></span>

[<span data-ttu-id="ea4c8-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ea4c8-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
