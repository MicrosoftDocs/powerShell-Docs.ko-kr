---
ms.date: 07/09/2020
ms.topic: reference
title: 확장 유형 시스템 클래스 메서드
description: 확장 유형 시스템 클래스 메서드
ms.openlocfilehash: b53604a36e0a0c3587f345262e8f274e3a2c4859
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660386"
---
# <a name="ets-class-methods"></a>메서드 클래스 메서드

인수는 인수를 사용 하 고 결과를 반환할 수 있으며 식의 왼쪽에 표시 될 수 없는 멤버입니다. 기간 내에서 사용할 수 있는 메서드에는 코드, Windows PowerShell 및 스크립트 메서드가 포함 됩니다.

> [!NOTE]
> 스크립트에서 메서드 이름의 끝에 괄호를 추가 하 여 다른 멤버와 동일한 구문을 사용 하 여 메서드를 액세스할 수 있습니다.

## <a name="code-methods"></a>코드 메서드

코드 메서드는 CLR 언어로 정의 된 확장 멤버입니다. 기본 개체에 정의 된 메서드와 비슷한 기능을 제공 합니다. 그러나 코드 메서드를 **PSObject** 개체에 동적으로 추가할 수 있습니다. 코드 메서드를 사용할 수 있으려면 개발자가 속성을 CLR 언어로 작성 하 고 컴파일한 후 결과 어셈블리를 제공 해야 합니다. 이 어셈블리는 코드 메서드가 필요한 runspace에서 사용할 수 있어야 합니다. 코드 메서드 구현은 스레드로부터 안전 해야 합니다. 이러한 메서드에 대 한 액세스는 다음 공용 메서드 및 속성을 제공 하는 [Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) 개체를 통해 수행 됩니다.

- `PSCodeMethod.Copy` 메서드: **Pscodemethod** 개체의 정확한 복사본을 만듭니다.
- `PSCodeMethod.Invoke(System.Object[])` 메서드: 내부 코드 메서드를 호출 합니다.
- `PSCodeMethod.ToString` 메서드: **Pscodemethod** 개체를 문자열로 변환 합니다.
- `PSCodeMethod.CodeReference` property: 코드 메서드의 기반이 되는 기본 메서드를 가져옵니다.
- **Psmemberinfo. IsInstance** 속성: 멤버의 원본을 나타내는 **부울** 값을 가져옵니다.
- **Pscodemethod** 속성:이 메서드를 코드 메서드로 식별 하는 **PSMemberTypes** 열거형 상수를 가져옵니다.
- **PSMemberInfo.Name** property: 내부 코드 메서드의 이름을 가져옵니다.
- **Pscodemethod. 오버 로드 정의** 속성: 기본 코드 메서드의 모든 오버 로드에 대 한 정의를 가져옵니다.
- **Pscodemethod. TypeNameOfValue** 속성: 코드 메서드의 전체 이름을 가져옵니다.
- **Psmemberinfo. Value** 속성: **pscodemethod** 개체를 가져옵니다.

## <a name="windows-powershell-methods"></a>Windows PowerShell 메서드

PowerShell 메서드는 기본 개체에 정의 되거나 어댑터를 통해 액세스할 수 있는 CLR 메서드입니다. 이러한 메서드에 대 한 액세스는 다음 공용 메서드 및 속성을 제공 하는 **Psmethod** 개체를 통해 수행 됩니다.

- `PSMethod.Copy` 메서드: **Psmethod** 개체의 정확한 복사본을 만듭니다.
- `PSMethod.Invoke(System.Object[])` 메서드: 기본 메서드를 호출 합니다.
- `PSMethod.ToString` 메서드: **Psmethod** 개체를 문자열로 변환 합니다.
- **Psmemberinfo. IsInstance** 속성: 멤버의 원본을 나타내는 **부울** 값을 가져옵니다.
- **MemberType** 속성:이 메서드를 PowerShell 메서드로 식별 하는 **PSMemberTypes** 열거형 상수를 가져옵니다.
- **PSMemberInfo.Name** property: 기본 메서드의 이름을 가져옵니다.
- **Psmethod. 과잉 load정의와** 속성: 기본 메서드의 모든 오버 로드에 대 한 정의를 가져옵니다.
- **TypeNameOfValue** 속성:이 메서드의 작업 유형을 가져옵니다.
- **Psmemberinfo. Value** 속성: **Psmemberinfo** 개체를 가져옵니다.

## <a name="script-methods"></a>스크립트 메서드

스크립트 메서드는 PowerShell 언어로 정의 된 확장 멤버입니다. 기본 개체에 정의 된 메서드와 비슷한 기능을 제공 합니다. 그러나 스크립트 메서드를 **PSObject** 개체에 동적으로 추가할 수 있습니다. 이러한 메서드에 대 한 액세스는 다음 공용 메서드 및 속성을 제공 하는 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) 개체를 통해 수행 됩니다.

- `PSScriptMethod.Copy` method: **PSScriptMethod** 개체의 정확한 복사본을 만듭니다.
- `PSScriptMethod.Invoke(System.Object[])` 메서드: 기본 스크립트 메서드를 호출 합니다.
- `PSScriptMethod.ToString` method: **PSScriptMethod** 개체를 문자열로 변환 합니다.
- **Psmemberinfo. IsInstance** 속성: 멤버의 원본을 나타내는 **부울** 값을 가져옵니다.
- **PSScriptMethod. MemberType** 속성:이 메서드를 스크립트 메서드로 식별 하는 **ScriptMethod** 열거형 상수를 가져옵니다.
- **PSMemberInfo.Name** property: 내부 코드 메서드의 이름을 가져옵니다.
- **PSScriptMethod** 속성: 기본 스크립트 메서드의 모든 오버 로드에 대 한 정의를 가져옵니다.
- **PSScriptMethod. TypeNameOfValue** 속성:이 메서드의 작업 유형을 가져옵니다.
- **PSScriptMethod** 속성: 메서드를 호출 하는 데 사용 되는 스크립트를 가져옵니다.
- **Psmemberinfo. Value** 속성: **PSScriptMethod** 개체를 가져옵니다.
