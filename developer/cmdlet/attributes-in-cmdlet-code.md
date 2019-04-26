---
title: Cmdlet 코드의 특성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068688"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 코드의 특성

Windows PowerShell에서 제공 하는 일반적인 기능을 사용 하려면 클래스 및 cmdlet 코드에서 정의 하는 공용 속성을 특성으로 데코레이팅 됩니다. 다음 클래스 정의 Cmdlet 특성을 사용 하 여 Microsoft.NET Framework 클래스를 식별 하는 예를 들어 합니다 **Get-proc** cmdlet 구현 됩니다. (이 cmdlet은이 문서에서 예제로 사용 되며 비슷합니다는 `Get-Process` cmdlet은 Windows PowerShell에서 제공 합니다.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

이러한 특성 이므로 구현과 cmdlet 코드의 구현에서 별도 메타 데이터를 간주 됩니다. Windows PowerShell 런타임이 cmdlet을 실행 하면 특성을 인식 하 고 각 특성에 대 한 적절 한 조치를 수행 합니다.

고유한 버전의 이러한 특성에 의해 제공 기능을 구현 하려는 하지만 좋은 cmdlet 설계는 이러한 일반적인 기능을 사용 합니다.

Cmdlet에서 선언할 수 있는 다른 특성에 대 한 자세한 내용은 참조 하세요. [특성 유형을](./attribute-types.md)합니다.

## <a name="see-also"></a>참고 항목

[특성 유형](./attribute-types.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
