---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateRange 특성 선언
description: ValidateRange 특성 선언
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660599"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 특성 선언

ValidateRange 특성은 cmdlet 매개 변수 인수에 대 한 최소값 및 최대값 (범위)을 지정 합니다. 이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.

## <a name="syntax"></a>구문

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>매개 변수

`MinRange` ([System.object](/dotnet/api/system.object))가 필요 합니다. 허용 되는 최소값을 지정 합니다.

`MaxRange` ([System.object](/dotnet/api/system.object))가 필요 합니다. 허용 되는 최대값을 지정 합니다.

## <a name="remarks"></a>설명

- Windows PowerShell 런타임에서는 `MinRange` 매개 변수 값이 매개 변수 값 보다 클 때 생성 오류를 throw 합니다 `MaxRange` .

- Windows PowerShell 런타임은 다음과 같은 경우 유효성 검사 오류를 throw 합니다.

  - 인수의 값이 제한 보다 작거나 한 `MinRange` 도 보다 큰 경우 `MaxRange`

  - 인수가 `MinRange` 및 매개 변수와 동일한 형식이 아닌 경우 `MaxRange`

- ValidateRange 특성은 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[Validaterangeattribute.](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
