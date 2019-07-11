---
title: ValidateLength 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735100"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 특성 선언

ValidateLength 특성 cmdlet 매개 변수 인수에 대 한 문자의 최소 및 최대 수를 지정합니다. Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.

## <a name="syntax"></a>구문

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>매개 변수

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 필요 합니다. 허용 되는 문자의 최소 수를 지정 합니다.

`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) 필요 합니다. 허용 되는 문자의 최대 수를 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [입력 유효성 검사 규칙 선언 하는 방법을](./how-to-validate-parameter-input.md)합니다.

- 이 특성을 사용 하지 않으면 해당 매개 변수 인수 길이 수 있습니다.

- Windows PowerShell 런타임에 다음과 같은 경우 오류가 throw 됩니다.

    - 때의 값을 `MaxLength` 특성 매개 변수 값 보다 작습니다는 `MinLength` 특성 매개 변수입니다.

    - 경우는 `MaxLength` 특성 매개 변수는 0으로 설정 됩니다.

    - 경우 인수 문자열이 아닙니다.

- ValidateLength 특성은 정의한 합니다 [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 클래스입니다.

## <a name="see-also"></a>관련 항목

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
