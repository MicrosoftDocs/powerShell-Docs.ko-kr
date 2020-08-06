---
title: ValidateLength 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.openlocfilehash: 7145dde55e79eeea6e3ceb91dfc1c93043a8857c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786308"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 특성 선언

ValidateLength 특성은 cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다. 이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.

## <a name="syntax"></a>구문

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>매개 변수

`MinLength`([System.web](/dotnet/api/System.Int32))이 필요 합니다. 허용 되는 최소 문자 수를 지정 합니다.

`MaxLength`([System.web](/dotnet/api/System.Int32))이 필요 합니다. 허용 되는 최대 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 [입력 유효성 검사 규칙을 선언 하는 방법](./how-to-validate-parameter-input.md)을 참조 하세요.

- 이 특성을 사용 하지 않으면 해당 매개 변수 인수의 길이는 모두 일 수 있습니다.

- Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.

  - `MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`

  - `MaxLength`특성 매개 변수가 0으로 설정 된 경우

  - 인수가 문자열이 아닌 경우

- ValidateLength 특성은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[Validatelengthattribute.](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
