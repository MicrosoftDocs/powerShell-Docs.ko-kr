---
title: 확장 유형 시스템에서 발생 하는 오류 및 예외
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 0e0b158e51d15db266415fb1ea6bb16fba319e62
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86218015"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>확장 유형 시스템에서 발생 하는 오류 및 예외

오류는 형식 데이터를 초기화 하는 동안 그리고 **PSObject** 개체의 멤버에 액세스 하거나 **languageprimitives.physicalhash**와 같은 유틸리티 클래스 중 하나를 사용 하는 경우에 발생할 수 있습니다.

## <a name="runtime-errors"></a>런타임 오류

한 가지 예외를 제외 하 고, 캐스팅할 때 런타임에 **ExtendedTypeSystemException** 에서 throw 되는 모든 예외는 **ExtendedTypeSystemException** 클래스에서 파생 된 예외 또는 예외입니다. 이렇게 하면 스크립트 개발자가 스크립트의 문을 사용 하 여 이러한 예외를 트래핑할 수 있습니다 `Trap` .

## <a name="errors-getting-member-values"></a>멤버 값을 가져오는 중 오류 발생

GetValueInvocationException 멤버 (속성, 메서드 또는 매개 변수가 있는 속성)의 값을 가져올 때 발생 하는 모든 오류는 **Getvalueexception** 또는 **GetValueInvocationException** exception을 throw 합니다.
오류가 발생 했음을 인식 하면 **Getvalueexception** 예외가 throw 됩니다. 참조 된 멤버의 기본 getter가 오류가 발생 한 것을 인식 하는 경우 get 호출 오류를 발생 시킨 내부 예외를 포함 하거나 포함 하지 않을 수 있는 **GetValueInvocationException** 예외가 throw 됩니다.

## <a name="errors-setting-member-values"></a>오류 설정 멤버 값

SetValueInvocationException 속성 값을 설정할 때 발생 하는 모든 오류는 **Setvalueexception** 또는 **SetValueInvocationException** exception을 throw 합니다. 오류가 발생 했음을 인식 하면 **Setvalueexception** 예외가 throw 됩니다. 참조 된 속성의 기본 setter가 오류가 발생 한 것을 인식 하면 set 호출 오류를 발생 시킨 내부 예외를 포함 하거나 포함 하지 않을 수 있는 **SetValueInvocationException** 예외가 throw 됩니다.

## <a name="errors-invoking-a-method"></a>메서드를 호출 하는 오류

MethodInvocationException 메서드를 호출할 때 발생 하는 모든 오류는 **MethodException** 또는 **MethodInvocationException** 예외를 throw 합니다. **MethodException** 에서 오류가 발생 한 것으로 인식 되 면 예외가 throw 됩니다. 참조 된 메서드에서 오류가 발생 한 것을 인식 하면 호출 오류를 발생 시킨 내부 예외를 포함 하거나 포함 하지 않을 수 있는 **MethodInvocationException** 예외가 throw 됩니다.

## <a name="casting-errors"></a>캐스팅 오류

잘못 된 캐스팅을 시도 하면 **PSInvalidCastException** 이 throw 됩니다. 이 예외는 **InvalidCastException**에서 파생 되기 때문에 스크립트에서 직접 트랩할 수 없습니다. 캐스팅을 시도 하는 엔터티는 **이를** **PSInvalidCastException** 로 래핑하여 스크립트에서 트래핑할 수 있도록 해야 합니다. **PSPropertySet**, **psmemberset**, **psmemberset**또는 **ReadOnlyPSMemberInfoCollection ' 1**의 멤버의 값을 설정 하려고 하면 **NotSupportedException** 이 throw 됩니다.

## <a name="common-runtime-errors"></a>일반적인 런타임 오류

발생 하는 다른 모든 일반적인 런타임 오류는 특정 예외 형식이 추가로 없는 **ExtendedTypeSystemException** exception 형식입니다.

## <a name="initialization-errors"></a>초기화 오류

를 초기화할 때 오류가 발생할 수 있습니다 `types.ps1xml` . 일반적으로 이러한 오류는 PowerShell 런타임이 시작 될 때 표시 됩니다. 그러나 모듈이 로드 될 때 표시 될 수도 있습니다.
