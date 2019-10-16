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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366972"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 코드 샘플

다음 코드는 [Windows Powershell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)에서 설명 하는 windows powershell 공급자의 구현을 보여 줍니다. 이 공급자는 다중 계층 데이터 저장소에서 작동 합니다. 이러한 유형의 데이터 저장소의 경우 저장소의 최상위 수준에 루트 항목이 포함 되 고 각 후속 수준은 자식 항목의 노드 라고 합니다. 사용자는 이러한 자식 노드에 대해 작업을 수행할 수 있으므로 데이터 저장소를 통해 계층적으로 상호 작용할 수 있습니다.

## <a name="code-sample"></a>코드 샘플

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
