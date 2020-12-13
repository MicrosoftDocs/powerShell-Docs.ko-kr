---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateCount 특성 선언
description: ValidateCount 특성 선언
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646276"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 특성 선언

ValidateCount 특성은 cmdlet 매개 변수에 허용 되는 인수의 최소 및 최대 수를 지정 합니다.

## <a name="syntax"></a>구문

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>매개 변수

`MinLength` ([System.web][])이 필요 합니다. 인수의 최소 개수를 지정 합니다.

`MaxLength`([System.web][])이 필요 합니다. 최대 인수 수를 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 [인수 수의 유효성을 검사][]하는 방법을 참조 하세요.

- 이 특성이 호출 되지 않으면 해당 cmdlet 매개 변수에 원하는 수의 인수가 있을 수 있습니다.

- Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.

  - `MinLength`및 `MaxLength` 특성 매개 변수는 [system.object][]형식이 아닙니다.

  - `MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`

- ValidateCount 특성은 [ValidateCountAttribute][] 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[ValidateCountAttribute.][]

[인수 개수를 확인하는 방법][]

[Writing a Windows PowerShell Cmdlet][](Windows PowerShell Cmdlet 작성)

[인수 개수를 확인하는 방법]: how-to-validate-an-argument-count.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md(Windows PowerShell Cmdlet 작성)

[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute.]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
