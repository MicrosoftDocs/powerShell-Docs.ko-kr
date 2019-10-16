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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369132"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 특성 선언

ValidateRange 특성은 cmdlet 매개 변수 인수에 대 한 최소값 및 최대값 (범위)을 지정 합니다. 이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.

## <a name="syntax"></a>구문

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>매개 변수

`MinRange` ([system.object](/dotnet/api/system.object))이 필요 합니다. 허용 되는 최소값을 지정 합니다.

`MaxRange` ([system.object](/dotnet/api/system.object))이 필요 합니다. 허용 되는 최대값을 지정 합니다.

## <a name="remarks"></a>설명

- @No__t-0 매개 변수의 값이 `MaxRange` 매개 변수의 값 보다 크면 Windows PowerShell 런타임이 생성 오류를 throw 합니다.

- Windows PowerShell 런타임은 다음과 같은 경우 유효성 검사 오류를 throw 합니다.

    - 인수의 값이 `MinRange` 보다 작거나 `MaxRange` 제한 보다 큰 경우

    - 인수가 `MinRange` 및 `MaxRange` 매개 변수와 동일한 형식이 아닌 경우

- ValidateRange 특성은 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[Validaterangeattribute.](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
