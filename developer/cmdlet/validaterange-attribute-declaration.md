---
title: ValidateRange 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067113"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 특성 선언

ValidateRange 특성 cmdlet 매개 변수 인수에 대 한 최소 및 최대 값 (범위)를 지정합니다. Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.

## <a name="syntax"></a>구문

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>매개 변수

`MinRange` ([System.Object](/dotnet/api/system.object)) 필요 합니다. 허용 되는 최소값을 지정 합니다.

`MaxRange` ([System.Object](/dotnet/api/system.object)) 필요 합니다. 허용 되는 최대값을 지정 합니다.

## <a name="remarks"></a>설명

- Windows PowerShell 런타임 생성 오류를 throw 때의 값을 `MinRange` 매개 변수 값 보다 큽니다.는 `MaxRange` 매개 변수입니다.

- Windows PowerShell 런타임에 다음과 같은 유효성 검사 오류가 throw 됩니다.

    - 인수의 값이 보다 작은 `MinRange` 제한 보다 크거나는 `MaxRange` 제한 합니다.

    - 인수가 없는 경우와 동일한 형식의 합니다 `MinRange` 하며 `MaxRange` 매개 변수입니다.

- ValidateRange 특성은 정의한 합니다 [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 클래스입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
