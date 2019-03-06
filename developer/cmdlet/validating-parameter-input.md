---
title: 매개 변수 입력 유효성 검사 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429842"
---
# <a name="validating-parameter-input"></a>매개 변수 입력 유효성 검사

PowerShell에는 여러 가지 방법으로 cmdlet 매개 변수에 전달 된 인수 유효성을 검사할 수 있습니다.
PowerShell 길이, 범위 및 인수의 문자 패턴에 유효성을 검사할 수 있습니다.
사용할 수 있는 인수 (개수) 수가 검사할 수 있습니다.
이러한 유효성 검사 규칙 cmdlet 클래스의 공용 속성에 대 한 매개 변수 특성을 사용 하 여 선언 된 유효성 검사 특성에 의해 정의 됩니다.

매개 변수 인수에 유효성을 검사 하려면 PowerShell 런타임이 cmdlet을 실행 하기 전에 매개 변수의 값을 확인 하려면 유효성 검사 특성을 제공 하는 정보를 사용 합니다.
매개 변수 입력 유효 하지 않으면 사용자는 오류 메시지를 받습니다.
각 유효성 검사 매개 변수는 PowerShell에서 적용 되는 유효성 검사 규칙을 정의 합니다.

PowerShell에서 다음 특성을 기반으로 유효성 검사 규칙을 적용 합니다.

### <a name="validatecount"></a>ValidateCount

인수는 매개 변수를 받아들일 수 있는 최소 및 최대 수를 지정 합니다.
자세한 내용은 [ValidateCount 특성 선언을](./validatecount-attribute-declaration.md)합니다.

### <a name="validatelength"></a>ValidateLength

매개 변수 인수에 최소 및 최대 문자 수를 지정합니다.
자세한 내용은 [ValidateLength 특성 선언을](./validatelength-attribute-declaration.md)합니다.

### <a name="validatepattern"></a>ValidatePattern

매개 변수 인수를 확인 하는 정규식을 지정 합니다.
자세한 내용은 [ValidatePattern 특성 선언을](./validatepattern-attribute-declaration.md)합니다.

### <a name="validaterange"></a>ValidateRange

매개 변수 인수의 최소값과 최대값을 지정합니다.
자세한 내용은 [ValidateRange 특성 선언을](./validaterange-attribute-declaration.md)합니다.

### <a name="validateset"></a>ValidateSet

매개 변수 인수에 대 한 유효한 값을 지정합니다.
자세한 내용은 [ValidateSet 특성 선언을](./validateset-attribute-declaration.md)합니다.

## <a name="see-also"></a>참고 항목

[매개 변수 입력의 유효성을 검사 하는 방법](./how-to-validate-parameter-input.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
