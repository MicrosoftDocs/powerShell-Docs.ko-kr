---
ms.date: 09/13/2016
ms.topic: reference
title: OutputType 특성 선언
description: OutputType 특성 선언
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646452"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 특성 선언

`OutputType`특성은 cmdlet, 함수 또는 스크립트에서 반환 하는 .NET Framework 유형을 식별 합니다.

## <a name="syntax"></a>구문

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>매개 변수

( `string[]` 또는)를 입력 `Type[]` 해야 합니다. Cmdlet 함수 또는 스크립트에서 반환 되는 유형을 지정 합니다.

ParameterSetName (string []) 선택 사항입니다. 매개 변수에 지정 된 형식을 반환 하는 매개 변수 집합을 지정 합니다 `type` .

providerCmdlet 옵션입니다. 매개 변수에 지정 된 형식을 반환 하는 공급자 cmdlet을 지정 합니다 `type` .

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
