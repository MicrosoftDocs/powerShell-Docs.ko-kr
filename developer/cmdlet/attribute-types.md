---
title: 특성 유형 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863809"
---
# <a name="attribute-types"></a>특성 유형

Cmdlet 특성 기능별로 그룹화 할 수 있습니다.
다음 섹션에서는 사용 가능한 특성을 설명 하 고 런타임에 수행 특성 호출 되 면을 설명 합니다.

## <a name="cmdlet-attributes"></a>Cmdlet 특성

### <a name="cmdlet"></a>Cmdlet

Cmdlet으로.NET Framework 클래스를 식별합니다.
필수 기본 특성입니다.
자세한 내용은 [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.

## <a name="parameter-attributes"></a>매개 변수 특성

### <a name="parameter"></a>매개 변수

Cmdlet 매개 변수로 cmdlet 클래스에서 public 속성을 식별합니다.
자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.

### <a name="alias"></a>별칭

매개 변수에 대해 하나 이상의 별칭을 지정합니다.
자세한 내용은 [별칭 특성 선언은](./alias-attribute-declaration.md)합니다.

## <a name="argument-validation-attributes"></a>인수 유효성 검사 특성

### <a name="validatecount"></a>ValidateCount

Cmdlet 매개 변수에 대해 허용 되는 인수의 최소 및 최대 수를 지정 합니다.
자세한 내용은 [ValidateCount 특성 선언을](./validatecount-attribute-declaration.md)합니다.

### <a name="validatelength"></a>ValidateLength

Cmdlet 매개 변수 인수에 대 한 문자의 최소 및 최대 수를 지정합니다.
자세한 내용은 [ValidateLength 특성 선언을](./validatelength-attribute-declaration.md)합니다.

### <a name="validatepattern"></a>ValidatePattern

Cmdlet 매개 변수 인수 일치 해야 하는 정규식 패턴을 지정 합니다.
자세한 내용은 [ValidatePattern 특성 선언을](./validatepattern-attribute-declaration.md)합니다.

### <a name="validaterange"></a>ValidateRange

Cmdlet 매개 변수 인수에 대 한 최소 및 최대 값을 지정합니다.
자세한 내용은 [ValidateRange 특성 선언을](./validaterange-attribute-declaration.md)합니다.

### <a name="validateset"></a>ValidateSet

Cmdlet 매개 변수 인수에 대 한 유효한 값 집합을 지정 합니다.
자세한 내용은 [ValidateSet 특성 선언을](./validateset-attribute-declaration.md)합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
