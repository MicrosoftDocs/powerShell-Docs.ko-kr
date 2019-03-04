---
title: AccessDbProviderSample05 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fea5d923-8001-4407-8975-743918bc8c80
caps.latest.revision: 6
ms.openlocfilehash: 92c2d4d200ea917f0111ef9424de71611270fba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854629"
---
# <a name="accessdbprovidersample05-code-sample"></a><span data-ttu-id="ff704-102">AccessDbProviderSample05 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="ff704-102">AccessDbProviderSample05 Code Sample</span></span>

<span data-ttu-id="ff704-103">다음 코드에 설명 된 Windows PowerShell 탐색 공급자의 구현을 보여 줍니다 [Windows PowerShell 탐색 공급자 만들기](./creating-a-windows-powershell-navigation-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ff704-103">The following code shows the implementation of the Windows PowerShell navigation provider described in [Creating a Windows PowerShell Navigation Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span> <span data-ttu-id="ff704-104">이 공급자는 재귀 명령, 중첩 된 컨테이너 및 데이터 저장소를 탐색할 수 있도록 하는 상대 경로 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff704-104">This provider supports recursive commands, nested containers, and relative paths that allow it to navigate the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ff704-105">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ff704-105">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L11-L1960 "AccessDBProviderSample05.cs")]

## <a name="see-also"></a><span data-ttu-id="ff704-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff704-106">See Also</span></span>

[<span data-ttu-id="ff704-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ff704-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)