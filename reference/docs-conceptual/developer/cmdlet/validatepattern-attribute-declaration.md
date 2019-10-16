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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369162"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 특성 선언

ValidatePattern 특성은 cmdlet 매개 변수의 인수에 대 한 유효성을 검사 하는 정규식 패턴을 지정 합니다. 이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.

Cmdlet 내에서 ValidatePattern가 호출 되 면 Windows PowerShell 런타임은 cmdlet 매개 변수의 인수를 문자열로 변환한 다음 해당 문자열을 ValidatePattern 특성에서 제공 된 패턴과 비교 합니다. 이 cmdlet은 인수의 변환 된 문자열 표현과 제공 된 패턴이 일치 하는 경우에만 실행 됩니다. 일치 하지 않는 경우 Windows PowerShell 런타임에서 오류가 throw 됩니다.

## <a name="syntax"></a>구문

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>매개 변수

`RegexString` ([system.string](/dotnet/api/System.String))이 필요 합니다. 매개 변수 인수의 유효성을 검사 하는 정규식을 지정 합니다.

옵션 ([system.text.regularexpressions.regex>. system.text.regularexpressions.regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions))은 선택적으로 명명 된 매개 변수입니다. 정규식 옵션을 지정 하는 [system.text.regularexpressions.regex>. system.text.regularexpressions.regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) 플래그의 비트 조합을 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성은 매개 변수 당 한 번만 사용할 수 있습니다.

- 특성의 `Option` 매개 변수를 사용 하 여 패턴을 추가로 정의할 수 있습니다. 예를 들어 대/소문자를 구분 하는 패턴을 만들 수 있습니다.

- 이 특성이 컬렉션에 적용 되는 경우 컬렉션의 각 요소가 패턴과 일치 해야 합니다.

- ValidatePattern 특성은 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[Validatepatternattribute.](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
