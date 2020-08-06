---
title: ValidateSet 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787770"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 특성 선언

ValidateSetAttribute 특성은 cmdlet 매개 변수 인수에 사용할 수 있는 값의 집합을 지정 합니다. 이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.

이 특성이 지정 된 경우 Windows PowerShell 런타임에서는 cmdlet 매개 변수에 대해 제공 된 인수가 제공 된 요소 집합의 요소와 일치 하는지 여부를 확인 합니다. Cmdlet은 매개 변수 인수가 집합의 요소와 일치 하는 경우에만 실행 됩니다. 일치 하는 항목이 없으면 Windows PowerShell 런타임에서 오류가 발생 합니다.

## <a name="syntax"></a>구문

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>매개 변수

`ValidValues`([System.string](/dotnet/api/System.String))이 필요 합니다. 유효한 매개 변수 요소 값을 지정 합니다. 다음 샘플에서는 하나 또는 여러 요소를 지정 하는 방법을 보여 줍니다.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase`([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. 기본값은 `true` 대/소문자가 무시 됨을 나타냅니다. 값을 `false` 사용 하면 cmdlet에서 대/소문자를 구분 합니다.

## <a name="remarks"></a>설명

- 이 특성은 매개 변수 당 한 번만 사용할 수 있습니다.

- 매개 변수 값이 배열인 경우 배열의 모든 요소는 특성 집합의 요소와 일치 해야 합니다.

- ValidateSetAttribute 특성은 [ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[Validatesetattribute.](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
