---
title: 확장 유형 시스템 멤버 집합
ms.date: 07/09/2020
ms.openlocfilehash: 3f4e44ed7b498bb7c4a71f7b131270ed4f2ef981
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786257"
---
# <a name="ets-member-sets"></a>멤버 집합

멤버 집합을 사용 하면 해당 하위 집합의 멤버를 하위 집합 이름으로 함께 참조할 수 있도록 **PSObject** 개체의 멤버를 두 개의 하위 집합으로 분할할 수 있습니다. 두 가지 하위 집합 유형은 속성 집합과 멤버 집합을 포함 합니다. PowerShell에서 멤버 집합을 사용 하는 방법에 대 한 예를 들어, 지정 된 **PSObject** 개체에 대해 표시할 속성을 런타임에 결정 하는 데 사용 되는 **DefaultDisplayPropertySet** 라는 특정 속성 집합이 있습니다.

## <a name="property-sets"></a>속성 집합

속성 집합은 **PSObject** 형식의 속성을 원하는 개수 만큼 포함할 수 있습니다. 일반적으로 속성 집합은 동일한 형식의 속성 컬렉션이 필요할 때마다 사용할 수 있습니다. 속성 집합은 `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` 속성 집합 이름 및 참조 된 속성의 이름으로 생성자를 호출 하 여 만듭니다. 그런 다음 생성 된 **PSPropertySet** 개체를 집합의 속성을 가리키는 별칭으로 사용할 수 있습니다. [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) 클래스에는 다음과 같은 속성 및 메서드가 있습니다.

- **Isinstance** 속성: 속성의 원본을 나타내는 **부울** 값을 가져옵니다.
- **MemberType** property: 속성 집합의 속성 형식을 가져옵니다.
- **Name** 속성: 속성 집합의 이름을 가져옵니다.
- **Referencedpropertynames** 속성: 속성 집합의 속성 이름을 가져옵니다.
- **TypeNameOfValue** property:이 집합을 속성 집합으로 정의 하는 **PropertySet** 열거형 상수를 가져옵니다.
- **Value** 속성: **PSPropertySet** 개체를 가져오거나 설정 합니다.
- `PSPropertySet.Copy`method: **PSPropertySet** 개체의 정확한 복사본을 만듭니다.
- `PSMemberSet.ToString`method: **PSPropertySet** 개체를 문자열로 변환 합니다.

## <a name="member-sets"></a>멤버 집합

멤버 집합은 모든 형식의 확장 멤버를 원하는 수 만큼 포함할 수 있습니다. 멤버 집합은 다음을 호출 하 여 생성 됩니다.`PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
멤버 집합의 이름과 참조 멤버의 이름을 사용 하는 생성자입니다. 그러면 만든 **PSPropertySet** 개체를 해당 집합의 멤버를 가리키는 별칭으로 사용할 수 있습니다. [Psmemberset](/dotnet/api/system.management.automation.psmemberset) 클래스에는 다음과 같은 속성 및 메서드가 있습니다.

- **Isinstance** 속성: 멤버의 원본을 나타내는 **부울** 값을 가져옵니다.
- **Members** 속성: 멤버 집합의 모든 멤버를 가져옵니다.
- **MemberType** property:이 집합을 멤버 집합으로 정의 하는 **MemberSet** 열거형 상수를 가져옵니다.
- **메서드** 속성: 멤버 집합에 포함 된 메서드를 가져옵니다.
- **Properties** 속성: 멤버 집합에 포함 된 속성을 가져옵니다.
- **TypeNameOfValue** property:이 집합을 멤버 집합으로 정의 하는 **MemberSet** 열거형 상수를 가져옵니다.
- **Value** 속성: **Psmemberset** 개체를 가져옵니다.
- `PSMemberSet.Copy`method: **Psmemberset** 개체의 정확한 복사본을 만듭니다.
- `PSMemberSet.ToString`method: **Psmemberset** 개체를 문자열로 변환 합니다.
