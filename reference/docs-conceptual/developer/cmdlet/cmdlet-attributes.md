---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 특성
description: Cmdlet 특성
ms.openlocfilehash: 6a106f33cb34c6c33b88a981815543bc9af4e4ba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653519"
---
# <a name="cmdlet-attributes"></a>Cmdlet 특성

Windows PowerShell은 사용자 코드 내에서 해당 기능을 구현 하지 않고 cmdlet에 일반적인 기능을 추가 하는 데 사용할 수 있는 여러 특성을 정의 합니다. 여기에는 cmdlet 클래스로 Microsoft .NET Framework 클래스를 식별 하는 Cmdlet 특성, cmdlet에서 반환 되는 .NET Framework 형식을 지정 하는 OutputType 특성, cmdlet 매개 변수로 공용 속성을 식별 하는 매개 변수 특성 등이 포함 됩니다.

## <a name="in-this-section"></a>섹션 내용

[Cmdlet 코드의 특성](./attributes-in-cmdlet-code.md) Cmdlet 코드에서 특성을 사용 하는 경우의 이점을 설명 합니다.

[특성 유형](./attribute-types.md) Cmdlet 클래스를 데코레이팅 할 수 있는 다양 한 특성에 대해 설명 합니다.

[별칭 특성 선언](./alias-attribute-declaration.md) Cmdlet 매개 변수 이름에 대 한 별칭을 정의 하는 방법을 설명 합니다.

[Cmdlet 특성 선언](./cmdlet-attribute-declaration.md) .NET Framework 클래스를 cmdlet으로 정의 하는 방법을 설명 합니다.

[자격 증명 특성 선언](./credential-attribute-declaration.md) 문자열 입력을 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 로 변환 하기 위한 지원을 추가 하는 방법을 설명 합니다.

[OutputType 특성 선언](./outputtype-attribute-declaration.md) Cmdlet에서 반환 되는 .NET Framework 유형을 지정 하는 방법을 설명 합니다.

[매개 변수 특성 선언](./parameter-attribute-declaration.md) Cmdlet의 매개 변수를 정의 하는 방법을 설명 합니다.

[Validatecount 특성 선언](./validatecount-attribute-declaration.md) 매개 변수에 허용 되는 인수 수를 정의 하는 방법을 설명 합니다.

[ValidateLength 특성 선언](./validatelength-attribute-declaration.md) 매개 변수 인수의 길이 (문자 수)를 정의 하는 방법을 설명 합니다.

[ValidatePattern 특성 선언](./validatepattern-attribute-declaration.md) 매개 변수 인수에 대 한 올바른 패턴을 정의 하는 방법을 설명 합니다.

[ValidateRange 특성 선언](./validaterange-attribute-declaration.md) 매개 변수 인수의 올바른 범위를 정의 하는 방법을 설명 합니다.

[ValidateSet 특성 선언](./validateset-attribute-declaration.md) 매개 변수 인수에 사용할 수 있는 값을 정의 하는 방법을 설명 합니다.

## <a name="reference"></a>참조

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
