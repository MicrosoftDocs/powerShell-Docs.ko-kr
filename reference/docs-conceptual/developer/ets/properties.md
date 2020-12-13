---
ms.date: 07/09/2020
ms.topic: reference
title: 확장 유형 시스템 속성
description: 확장 유형 시스템 속성
ms.openlocfilehash: cccd3c400a8822ee25c44e8e1625e35571420259
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646142"
---
# <a name="ets-properties"></a>ETS 속성

속성은 속성으로 처리 될 수 있는 멤버입니다. 기본적으로 식의 왼쪽에 표시 될 수 있습니다. 사용할 수 있는 속성에는 별칭, 코드, 메모 및 스크립트 속성이 있습니다.

## <a name="alias-property"></a>Alias 속성

별칭 속성은 **PSObject** 개체가 포함 하는 다른 속성을 참조 하는 속성입니다. 주로 참조 된 속성의 이름을 바꾸는 데 사용 됩니다. 그러나 참조 된 속성의 값을 다른 형식으로 변환 하는 데 사용할 수도 있습니다. 이 형식의 속성은 나머지와 관련 하 여 항상 확장 멤버 이며 [PSAliasProperty](/dotnet/api/system.management.automation.psaliasproperty) 클래스에 의해 정의 됩니다. 클래스에는 다음 속성이 포함 되어 있습니다.

- **ConversionType** property: 참조 된 멤버의 값을 변환 하는 데 사용 되는 CLR 형식입니다.
- **IsGettable** property: 참조 된 속성의 값을 검색할 수 있는지 여부를 나타냅니다.
  이 속성은 참조 된 속성의 **IsGettable** 속성을 검사 하 여 동적으로 결정 됩니다.
- **Issettable** 속성: 참조 된 속성의 값을 설정할 수 있는지 여부를 나타냅니다. 이 속성은 참조 된 속성의 **Issettable** 수 있는 속성을 검사 하 여 동적으로 결정 됩니다.
- **MemberType** property:이 속성을 별칭 속성으로 정의 하는 **AliasProperty** 열거형 상수입니다.
- **ReferencedMemberName** property:이 별칭이 참조 하는 참조 된 속성의 이름입니다.
- **TypeNameOfValue** property: 참조 된 속성 값의 CLR 형식에 대 한 전체 이름입니다.
- **Value** 속성: 참조 된 속성의 값입니다.

## <a name="code-property"></a>코드 속성

코드 속성은 CLR 언어로 정의 된 getter 및 setter 인 속성입니다. 코드 속성을 사용할 수 있으려면 개발자가 속성을 CLR 언어로 작성 하 고 컴파일한 후 결과 어셈블리를 제공 해야 합니다. 이 어셈블리는 코드 속성이 필요한 runspace에서 사용할 수 있어야 합니다. 이 형식의 속성은 나머지와 관련 하 여 항상 확장 멤버 이며 [Pscodeproperty](/dotnet/api/system.management.automation.pscodeproperty) 클래스로 정의 됩니다. 클래스에는 다음 속성이 포함 되어 있습니다.

- **Gettercodereference** 속성: 코드 속성의 값을 가져오는 데 사용 되는 메서드입니다.
- **IsGettable** 속성: 코드 속성의 값을 검색할 수 있는지 여부를 나타냅니다. **Settercodereference** 속성: 코드 속성의 값을 설정 하는 데 사용 되는 메서드입니다.
- **Issettable** 속성: 코드 속성의 값을 설정할 수 있는지 여부, **Settercodereference** 속성이 null이 아님을 나타냅니다.
- **MemberType** property:이 속성을 코드 속성으로 정의 하는 **codeproperty** 열거형 상수입니다.
- **Settercodereference** 속성: 코드 속성의 값을 가져오는 데 사용 되는 메서드입니다.
- **TypeNameOfValue** 속성: 속성 가져오기 작업에서 반환 하는 코드 속성 값의 CLR 형식입니다.
- **Value** 속성: 코드 속성의 값입니다. 이 속성을 검색할 때 GetterCodeReference 속성의 getter 코드를 호출 하 여 현재 **PSObject** 개체를 전달 하 고 호출에서 반환 된 값을 반환 합니다. 이 속성이 설정 되 면 현재 **PSObject** 개체를 첫 번째 인수로 전달 하 고 두 번째 인수로 값을 설정 하는 데 사용 되는 개체를 사용 하 여 **Settercodereference** 속성의 setter 코드를 호출 합니다.

## <a name="note-property"></a>Note 속성

메모 속성은 이름/값 쌍이 있는 속성입니다. 이 형식의 속성은 나머지와 관련 하 여 항상 확장 멤버 이며 [psclass 속성](/dotnet/api/system.management.automation.psnoteproperty) 클래스로 정의 됩니다. 클래스에는 다음 속성이 포함 되어 있습니다.

- **IsGettable** property: note 속성의 값을 검색할 수 있는지 여부를 나타냅니다.
- **Issettable** 속성: 메모 속성의 값을 설정할 수 있는지 여부를 나타냅니다.
- **MemberType** property:이 속성을 메모 속성으로 정의 하는 **note 속성** 열거형 상수입니다.
- **TypeNameOfValue** 속성: 메모 속성의 get 작업에서 반환 하는 개체의 정규화 된 형식 이름입니다.
- **Value**: note 속성의 값입니다.

## <a name="powershell-property"></a>PowerShell 속성

PowerShell 속성은 기본 개체 또는 어댑터를 통해 사용할 수 있는 속성에 정의 된 속성입니다. Clr 필드는 물론 clr 속성도 참조할 수 있습니다. 이 형식의 속성은 모든 것을 기준으로 기본 멤버 또는 어댑터 멤버일 수 있으며, [Psproperty](/dotnet/api/system.management.automation.psproperty) 클래스로 정의 됩니다. 클래스에는 다음 속성이 포함 되어 있습니다.

- **IsGettable** property: 기본 또는 적용 된 속성의 값을 검색할 수 있는지 여부를 나타냅니다.
- **Issettable** 속성: 기본 또는 적용 된 속성의 값을 설정할 수 있는지 여부를 나타냅니다.
- **MemberType** property:이 속성을 PowerShell 속성으로 정의 하는 속성 열거형 상수입니다.
- **TypeNameOfValue** property: 속성 값 형식의 정규화 된 이름입니다. 예를 들어 값이 문자열인 속성의 경우 해당 속성 값 **형식은 system.string입니다.**
- **Value** 속성: 속성의 값입니다. 해당 작업을 지원 하지 않는 속성에 대해 get 또는 set 작업을 호출 하면 **getvalueexception** 또는 **setvalueexception** 예외가 throw 됩니다.

## <a name="powershell-script-property"></a>PowerShell 스크립트 속성

스크립트 속성은 getter 및 setter 스크립트를 포함 하는 속성입니다. 이 형식의 속성은 나머지와 관련 하 여 항상 확장 멤버 이며 [Psscriptproperty](/dotnet/api/system.management.automation.psscriptproperty) 클래스로 정의 됩니다. 클래스에는 다음 속성이 포함 되어 있습니다.

- **Getterscript** 속성: 스크립트 속성 값을 검색 하는 데 사용 되는 스크립트입니다.
- **IsGettable** Property: **getterscript** 속성이 스크립트 블록을 노출 하는지 여부를 나타냅니다.
- **Issettable** 가능 속성: **setterscript** 속성이 스크립트 블록을 노출 하는지 여부를 나타냅니다.
- **MemberType** property:이 속성을 스크립트 속성으로 식별 하는 scriptproperty 열거형 상수입니다.
- **Setterscript** 속성: 스크립트 속성 값을 설정 하는 데 사용 되는 스크립트입니다.
- **TypeNameOfValue** property: getter 스크립트에서 반환 하는 개체의 정규화 된 형식 이름입니다. 이 경우에는 **system.object** 가 항상 반환 됩니다.
- **Value** 속성: 스크립트 속성의 값입니다. Get은 getter 스크립트를 호출 하 고 제공 된 값을 반환 합니다. 집합은 setter 스크립트를 호출 합니다.
