---
ms.date: 07/09/2020
ms.topic: reference
title: 확장 유형 시스템 클래스 멤버
description: 확장 유형 시스템 클래스 멤버
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666844"
---
# <a name="extended-type-system-class-members"></a>확장 유형 시스템 클래스 멤버

**PSMemberTypes** 열거형에 의해 정의 되는 형식을 가진 여러 종류의 멤버를 참조 합니다. 이러한 멤버 형식에는 각각 고유한 CLR 형식으로 정의 되는 속성, 메서드, 멤버 및 멤버 집합이 포함 됩니다. 예를 들어, **참고 속성** 은 고유한 **psnoteproperty** 형식으로 정의 됩니다. 이러한 개별 CLR 형식에는 [Psmemberinfo 클래스](/dotnet/api/system.management.automation.psmemberinfo)에서 상속 되는 고유한 속성과 공용 속성이 모두 있습니다.

## <a name="the-psmemberinfo-class"></a>PSMemberInfo 클래스

**Psmemberinfo** 클래스는 모든 멤버 형식에 대 한 기본 클래스로 사용 됩니다. 이 클래스는 모든 멤버 CLR 형식에 대 한 다음 기본 속성을 제공 합니다.

- **Name** 속성: 멤버의 이름입니다. 이 이름은 기본 개체에서 정의 하거나, 적용 된 멤버나 확장 멤버가 노출 될 때 PowerShell에서 정의 될 수 있습니다.
- **Value** 속성: 특정 멤버에서 반환 된 값입니다. 각 멤버 형식은 해당 멤버 값을 처리 하는 방법을 정의 합니다.
- **TypeNameOfValue** Property: value 속성에 의해 반환 되는 값의 CLR 형식 이름입니다.

## <a name="accessing-members"></a>멤버 액세스

멤버 컬렉션은 **PSObject** 개체의 **멤버**, **메서드** 및 **속성** 속성을 통해 액세스할 수 있습니다.

## <a name="ets-properties"></a>ETS 속성

속성은 속성으로 처리 될 수 있는 멤버입니다. 기본적으로 식의 왼쪽에 표시 될 수 있습니다. 별칭 속성, 코드 속성, PowerShell 속성, 메모 속성 및 스크립트 속성을 포함 합니다. 이러한 속성 유형에 대 한 자세한 내용은 속성 [속성](properties.md)을 참조 하세요.

## <a name="ets-methods"></a>ETS 메서드

인수는 인수를 사용 하 고 결과를 반환할 수 있으며 식의 왼쪽에 표시 될 수 없는 멤버입니다. 여기에는 코드 메서드, PowerShell 메서드 및 스크립트 메서드가 포함 됩니다.
이러한 메서드 형식에 대 한 자세한 [내용은 메서드를 참조 하세요](methods.md).
