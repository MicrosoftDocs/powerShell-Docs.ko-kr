---
title: ValidatePattern 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067130"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 특성 선언

ValidatePattern 특성 cmdlet 매개 변수 인수의 유효성을 검사 하는 정규식 패턴을 지정 합니다. Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.

ValidatePattern cmdlet 내에서 호출 되 면 Windows PowerShell cmdlet 매개 변수의 인수를 문자열로 변환 런타임과 ValidatePattern 특성에 의해 제공 된 패턴에 해당 문자열을 비교 합니다. Cmdlet은 변환 된 문자열 표현을 인수 및 지정 된 패턴과 일치 하는 경우에 실행 됩니다. 일치 하지 않으면 Windows PowerShell 런타임에 의해 오류가 throw 됩니다.

## <a name="syntax"></a>구문

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>매개 변수

`RegexString` ([System.String](/dotnet/api/System.String)) 필요 합니다. 매개 변수 인수를 확인 하는 정규식을 지정 합니다.

옵션 ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 명명 된 매개 변수는 선택 사항입니다. 비트 조합을 지정 [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) 정규식 옵션을 지정 하는 플래그입니다.

## <a name="remarks"></a>설명

- 이 특성 매개 변수당 한 번만 사용할 수 있습니다.

- 사용할 수는 `Option` 추가로 패턴을 정의할 특성의 매개 변수입니다. 예를 들어 가능 패턴 대/소문자 구분 합니다.

- 이 특성 컬렉션에 적용할 경우 컬렉션의 각 요소에 패턴을 일치 해야 합니다.

- ValidatePattern 특성은 정의한 합니다 [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) 클래스입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
