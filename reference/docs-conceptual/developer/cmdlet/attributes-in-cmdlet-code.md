---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 코드의 특성
description: Cmdlet 코드의 특성
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653647"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 코드의 특성

Windows PowerShell에서 제공 하는 공통 기능을 사용 하기 위해 cmdlet 코드에 정의 된 클래스 및 공용 속성은 특성으로 데코 레이트 됩니다. 예를 들어, 다음 클래스 정의에서는 Cmdlet 특성을 사용 하 여 **Get Proc** cmdlet이 구현 된 Microsoft .NET Framework 클래스를 식별 합니다. 이 cmdlet은이 문서의 예로 사용 되며 `Get-Process` Windows PowerShell에서 제공 하는 cmdlet과 유사 합니다.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

이러한 특성의 구현은 cmdlet 코드의 구현과 별개 이므로 메타 데이터로 간주 됩니다. Windows PowerShell 런타임은 cmdlet을 실행할 때 특성을 인식 한 다음 각 특성에 대해 적절 한 작업을 수행 합니다.

이러한 특성에서 제공 하는 고유한 버전의 기능을 구현 하는 것이 좋지만 좋은 cmdlet 디자인에서는 이러한 일반적인 기능을 사용 합니다.

Cmdlet에서 선언할 수 있는 다양 한 특성에 대 한 자세한 내용은 [특성 형식](./attribute-types.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[특성 유형](./attribute-types.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
