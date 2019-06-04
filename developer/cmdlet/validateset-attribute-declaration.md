---
title: ValidateSet 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067073"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 특성 선언

ValidateSetAttribute 특성에는 cmdlet 매개 변수 인수에 대 한 가능한 값 집합을 지정합니다. Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.

이 특성을 지정 하는 경우 Windows PowerShell 런타임이 cmdlet 매개 변수에 대해 제공 된 인수는 집합의 요소에 제공 된 요소 일치 하는지 여부를 결정 합니다. Cmdlet 매개 변수 인수에 집합의 요소와 일치 하는 경우에 실행 됩니다. 일치 하는 항목이 없으면 Windows PowerShell 런타임에 의해 오류가 throw 됩니다.

## <a name="syntax"></a>구문

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>매개 변수

`ValidValues` ([System.String](/dotnet/api/System.String)) 필요 합니다. 유효한 매개 변수 요소 값을 지정합니다. 다음 샘플에는 요소가 하나 또는 여러 요소를 지정 하는 방법을 보여 줍니다.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. 기본값은 `true` 대/소문자를 무시 함을 나타냅니다. 값 `false` cmdlet은 대/소문자 구분을 만듭니다.

## <a name="remarks"></a>설명

- 이 특성 매개 변수당 한 번만 사용할 수 있습니다.

- 매개 변수 값이 배열인 경우 배열의 모든 요소는 특성 집합의 요소를 일치 해야 합니다.

- ValidateSetAttribute 특성은 정의한 합니다 [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) 클래스입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
