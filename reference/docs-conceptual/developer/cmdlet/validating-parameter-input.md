---
title: 매개 변수 입력 유효성 검사 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783996"
---
# <a name="validating-parameter-input"></a>매개 변수 입력 유효성 검사

PowerShell은 여러 가지 방법으로 cmdlet 매개 변수에 전달 되는 인수의 유효성을 검사할 수 있습니다.
PowerShell은 인수의 길이, 범위 및 패턴의 유효성을 검사할 수 있습니다.
사용할 수 있는 인수 수 (개수)의 유효성을 검사할 수 있습니다.
이러한 유효성 검사 규칙은 cmdlet 클래스의 공용 속성에 대 한 매개 변수 특성을 사용 하 여 선언 된 유효성 검사 특성에 의해 정의 됩니다.

매개 변수 인수의 유효성을 검사 하기 위해 PowerShell 런타임은 유효성 검사 특성에서 제공 하는 정보를 사용 하 여 cmdlet이 실행 되기 전에 매개 변수의 값을 확인 합니다.
매개 변수 입력이 잘못 된 경우 사용자에 게 오류 메시지가 나타납니다.
각 유효성 검사 매개 변수는 PowerShell에서 적용 되는 유효성 검사 규칙을 정의 합니다.

PowerShell은 다음 특성을 기반으로 유효성 검사 규칙을 적용 합니다.

### <a name="validatecount"></a>ValidateCount

매개 변수가 허용할 수 있는 인수의 최소 및 최대 수를 지정 합니다.
자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.

### <a name="validatelength"></a>ValidateLength

매개 변수 인수에서 최소 및 최대 문자 수를 지정 합니다.
자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.

### <a name="validatepattern"></a>ValidatePattern

매개 변수 인수의 유효성을 검사 하는 정규식을 지정 합니다.
자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.

### <a name="validaterange"></a>ValidateRange

매개 변수 인수의 최소값과 최대값을 지정 합니다.
자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.

### <a name="validateset"></a>ValidateSet

매개 변수 인수에 대 한 유효한 값을 지정 합니다.
자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[매개 변수 입력 유효성을 검사하는 방법](./how-to-validate-parameter-input.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
