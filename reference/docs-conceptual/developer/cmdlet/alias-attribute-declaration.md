---
title: Alias 특성 선언 | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370022"
---
# <a name="alias-attribute-declaration"></a>Alias 특성 선언

Alias 특성을 사용 하면 사용자가 cmdlet 매개 변수에 대해 다른 이름을 지정할 수 있습니다. 별칭을 사용 하 여 매개 변수 이름에 대 한 바로 가기를 제공 하거나 다양 한 시나리오에 적합 한 다른 이름을 제공할 수 있습니다.

## <a name="syntax"></a>구문

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>매개 변수

`aliasName` (String [])이 필요 합니다. Cmdlet 매개 변수에 대 한 쉼표로 구분 된 별칭 이름 집합을 지정 합니다.

## <a name="remarks"></a>설명

- Alias 특성은 cmdlet 매개 변수를 지정할 때 Parameter 특성과 함께 사용 됩니다. 이러한 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.

- 각 별칭 이름은 cmdlet 내에서 고유 해야 합니다. Windows PowerShell은 중복 된 별칭 이름을 확인 하지 않습니다.

- 별칭 특성은 cmdlet의 각 매개 변수에 대해 한 번만 사용 됩니다.

- Alias 특성은 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[매개 변수 별칭](./parameter-aliases.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
