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
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081957"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 코드 샘플

다음 코드에 설명 된 Windows PowerShell 공급자의 구현을 보여 줍니다 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)합니다. 이 공급자는 다중 계층 데이터 저장소에서 작동합니다. 이 유형의 데이터 저장소에 대 한 루트 항목을 포함 하는 저장소의 최상위 및 하위 항목 노드로 이어지는 각 수준 라고 합니다. 사용자가 이러한 자식 노드 작업 하도록 함으로써 사용자는 데이터 저장소를 통해 계층적으로 작용할 수 있습니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)