---
title: 특성 유형 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 96fdd38ba10eb748ab0762f0c910463dd472494d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782381"
---
# <a name="attribute-types"></a>특성 유형

Cmdlet 특성은 기능별로 그룹화 할 수 있습니다.
다음 섹션에서는 사용 가능한 특성을 설명 하 고 특성이 호출 될 때 런타임이 수행 하는 작업을 설명 합니다.

## <a name="cmdlet-attributes"></a>Cmdlet 특성

### <a name="cmdlet"></a>cmdlet

.NET Framework 클래스를 cmdlet으로 식별 합니다.
필수 기본 특성입니다.
자세한 내용은 [Cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

## <a name="parameter-attributes"></a>매개 변수 특성

### <a name="parameter"></a>매개 변수

Cmdlet 클래스에서 공용 속성을 cmdlet 매개 변수로 식별 합니다.
자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

### <a name="alias"></a>Alias

매개 변수에 대 한 별칭을 하나 이상 지정 합니다.
자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.

## <a name="argument-validation-attributes"></a>인수 유효성 검사 특성

### <a name="validatecount"></a>ValidateCount

Cmdlet 매개 변수에 사용할 수 있는 인수의 최소 및 최대 수를 지정 합니다.
자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.

### <a name="validatelength"></a>ValidateLength

Cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다.
자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.

### <a name="validatepattern"></a>ValidatePattern

Cmdlet 매개 변수 인수가 일치 해야 하는 정규식 패턴을 지정 합니다.
자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.

### <a name="validaterange"></a>ValidateRange

Cmdlet 매개 변수 인수에 대 한 최소값 및 최대값을 지정 합니다.
자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.

### <a name="validateset"></a>ValidateSet

Cmdlet 매개 변수 인수에 대 한 유효한 값 집합을 지정 합니다.
자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
