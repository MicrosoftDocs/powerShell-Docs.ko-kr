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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370002"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 코드의 특성

Windows PowerShell에서 제공 하는 공통 기능을 사용 하기 위해 cmdlet 코드에 정의 된 클래스 및 공용 속성은 특성으로 데코 레이트 됩니다. 예를 들어, 다음 클래스 정의에서는 Cmdlet 특성을 사용 하 여 **Get Proc** cmdlet이 구현 된 Microsoft .NET Framework 클래스를 식별 합니다. 이 cmdlet은이 문서의 예로 사용 되며 Windows PowerShell에서 제공 하는 `Get-Process` cmdlet과 비슷합니다.

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
