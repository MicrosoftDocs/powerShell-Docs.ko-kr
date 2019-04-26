---
title: 별칭 특성 선언은 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068719"
---
# <a name="alias-attribute-declaration"></a>Alias 특성 선언

Alias 특성을 cmdlet 매개 변수에 대해 다른 이름을 지정할 수 있습니다. 다양 한 시나리오에 적합 한 다양 한 이름을 제공할 수 있습니다 또는 매개 변수 이름에 대 한 바로 가기를 제공에 별칭을 사용할 수 있습니다.

## <a name="syntax"></a>구문

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>매개 변수

`aliasName` (시간이 걸린다 필수. Cmdlet 매개 변수에 대 한 쉼표로 구분 된 별칭 이름 집합을 지정합니다.

## <a name="remarks"></a>설명

- Alias 특성은 cmdlet 매개 변수를 지정 하는 경우, 매개 변수 속성을 사용 하 여 사용 됩니다. 이러한 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md)합니다.

- 각 별칭은 cmdlet 내에서 고유 해야 합니다. Windows PowerShell 별칭 중복 이름에 대 한 확인 하지 않습니다.

- Alias 특성 cmdlet에서 각 매개 변수에 대해 한 번 사용 됩니다.

- Alias 특성은 정의한 합니다 [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 클래스입니다.

## <a name="see-also"></a>참고 항목

[매개 변수 별칭](./parameter-aliases.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
