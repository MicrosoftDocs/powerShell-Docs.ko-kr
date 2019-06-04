---
title: OutputType 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067606"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 특성 선언

`OutputType` 특성은 cmdlet, 함수 또는 스크립트에서 반환 되는.NET Framework 형식 식별 합니다.

## <a name="syntax"></a>구문

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>매개 변수

형식 (`string[]` 또는 `Type[]`) 필요 합니다. Cmdlet은 함수 또는 스크립트에서 반환 형식을 지정 합니다.

ParameterSetName (시간이 걸린다는 선택 사항입니다. 에 지정 된 형식을 반환 하는 매개 변수 집합을 지정 합니다 `type` 매개 변수입니다.

providerCmdlet 선택 사항입니다. 에 지정 된 형식을 반환 하는 공급자 cmdlet은 지정 된 `type` 매개 변수입니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
